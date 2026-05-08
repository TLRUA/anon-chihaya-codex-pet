# Anon Chihaya Codex Pet

<div align="center">
  <img src="./assets/previews/anon-chihaya-failed.gif" width="144" alt="Anon Chihaya idle animation">

  <p>
    <strong>A transparent animated Codex pet package for Anon Chihaya.</strong>
  </p>

  <p>
    <img alt="pet" src="https://img.shields.io/badge/pet-anon--chihaya-2ea44f">
    <img alt="actions" src="https://img.shields.io/badge/actions-9-0969da">
    <img alt="sprite" src="https://img.shields.io/badge/sprite-8x9%20atlas-111111">
    <img alt="background" src="https://img.shields.io/badge/background-transparent-7c3aed">
  </p>
</div>

## Motion Board

<table>
  <tr>
    <td align="center" width="33%">
      <img src="./assets/previews/anon-chihaya-idle.gif" width="132" alt="Idle"><br>
      <strong>Idle</strong><br>
      <sub>Row 0 - neutral idle loop</sub>
    </td>
    <td align="center" width="33%">
      <img src="./assets/previews/anon-chihaya-running-right.gif" width="132" alt="Running right"><br>
      <strong>Running Right</strong><br>
      <sub>Row 1 - rightward locomotion</sub>
    </td>
    <td align="center" width="33%">
      <img src="./assets/previews/anon-chihaya-running-left.gif" width="132" alt="Running left"><br>
      <strong>Running Left</strong><br>
      <sub>Row 2 - leftward locomotion</sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="33%">
      <img src="./assets/previews/anon-chihaya-waving.gif" width="132" alt="Waving"><br>
      <strong>Waving</strong><br>
      <sub>Row 3 - greeting gesture</sub>
    </td>
    <td align="center" width="33%">
      <img src="./assets/previews/anon-chihaya-jumping.gif" width="132" alt="Jumping"><br>
      <strong>Jumping</strong><br>
      <sub>Row 4 - jump loop</sub>
    </td>
    <td align="center" width="33%">
      <img src="./assets/previews/anon-chihaya-failed.gif" width="132" alt="Failed"><br>
      <strong>Failed</strong><br>
      <sub>Row 5 - failed reaction</sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="33%">
      <img src="./assets/previews/anon-chihaya-waiting.gif" width="132" alt="Waiting"><br>
      <strong>Waiting</strong><br>
      <sub>Row 6 - waiting loop</sub>
    </td>
    <td align="center" width="33%">
      <img src="./assets/previews/anon-chihaya-running.gif" width="132" alt="Running"><br>
      <strong>Running</strong><br>
      <sub>Row 7 - generic run loop</sub>
    </td>
    <td align="center" width="33%">
      <img src="./assets/previews/anon-chihaya-review.gif" width="132" alt="Review"><br>
      <strong>Review</strong><br>
      <sub>Row 8 - review loop</sub>
    </td>
  </tr>
</table>

## Official Action Order

| Row | GIF | Protocol Action |
|---:|---|---|
| 0 | `anon-chihaya-idle.gif` | `idle` |
| 1 | `anon-chihaya-running-right.gif` | `running-right` |
| 2 | `anon-chihaya-running-left.gif` | `running-left` |
| 3 | `anon-chihaya-waving.gif` | `waving` |
| 4 | `anon-chihaya-jumping.gif` | `jumping` |
| 5 | `anon-chihaya-failed.gif` | `failed` |
| 6 | `anon-chihaya-waiting.gif` | `waiting` |
| 7 | `anon-chihaya-running.gif` | `running` |
| 8 | `anon-chihaya-review.gif` | `review` |

## Design Notes

Some protocol actions are treated as **state slots** rather than literal motion requirements. The atlas still follows the Codex pet protocol, but a few slots use custom visual interpretations:

| Protocol Slot | Custom Interpretation |
|---|---|
| `running-right` / `running-left` | Image generation had trouble producing clean alternating arm motion for small running sprites, so these slots show the pet being picked up and dragged by the cursor instead. |
| `jumping` | A literal jump looked odd because the pet's screen-space Y position stays fixed during playback, so this slot is used for guitar playing instead. |

The Codex pet atlas is intentionally strict: fixed rows, fixed frame counts, and fixed playback timings. That makes pets predictable inside Codex, but it can also make some generated actions look twitchy or overly fast when the motion does not fit the available frames.

## Files

| File | Purpose |
|---|---|
| `pet.json` | Codex pet metadata |
| `spritesheet.webp` | 8x9 transparent sprite atlas |
| `assets/previews/*.gif` | README motion previews |

## Metadata

```json
{
  "id": "anon-chihaya",
  "displayName": "Anon Chihaya",
  "spritesheetPath": "spritesheet.webp"
}
```

## Preview Notes

- All preview GIFs are regenerated from `spritesheet.webp`.
- GIF files use a consistent `192x208` frame size.
- Background pixels are encoded as transparent GIF pixels.
- Blank source cells are replaced with the nearest valid frame from the same action.
- The motion board follows the Codex pet protocol row order: `idle`, `running-right`, `running-left`, `waving`, `jumping`, `failed`, `waiting`, `running`, `review`.
