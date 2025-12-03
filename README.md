# A.S.S (Aliucord Style Sheets)
Welcome to the official repository for **A.S.S (Aliucord Style Sheets)**.

## How to start
Styles are simple JSON files placed in `Aliucord/styles/`. A style consists of a **Manifest** and **Rules**.

**Rules** target Android View IDs (e.g., `chat_input_container`). You can find these IDs using Developer Assistant or by checking this [layout dump](https://github.com/RazerTexz/Discord-JADX/tree/main/decompiled/app/src/main/res/layout).

### Basic JSON Structure
Create a file named `YourStyleName.json`:

```json
{
    "manifest": {
        "name": "My Cool Style",
        "version": "1.0.0",
        "author": "Your Name"
    },
    "view_id": {
        "bgColor": "#FF0000"
    },
    "another_view_id": {
        "textColor": "#FFFFFF",
        "textSize": 14.0,
        "typeface": "myfont.ttf"
    }
}
```

<details>
<summary><b>Supported Properties</b></summary>

| Property | Type | Value |
| :--- | :--- | :--- |
| `width` / `height` | Number | `100` (or `-1` for MATCH_PARENT, `-2` for WRAP_CONTENT) |
| `leftMargin` / `topMargin` / `rightMargin` / `bottomMargin` | Number | `10` |
| `paddingLeft` / `paddingTop` / `paddingRight` / `paddingBottom` | Number | `10` |
| `textSize` | Number | `16.0` |
| `textColor` | Hex Color | `"#FFFFFF"` |
| `bgColor` | Hex Color | `"#000000"` |
| `bgTint` | Hex Color | `"#FF0000"` |
| `drawableTint` | Hex Color | `"#00FF00"` |
| `gradientColors` | Array of Hex Color | `["#FF0000", "#0000FF"]` |
| `gradientOrientation` | String | `"BL_TR"` / `"BOTTOM_TOP"` / `"BR_TL"` / `"LEFT_RIGHT"` / `"RIGHT_LEFT"` / `"TL_BR"` / `"TOP_BOTTOM"` / `"TR_BL"` |
| `gradientType` | String |  `"LINEAR"` / `"RADIAL"` / `"SWEEP"` |
| `visibility` | String | `"GONE"` / `"INVISIBLE"` / `"VISIBLE"` |
| `typeface` | String | `"myfont.ttf"` (must be placed under `Aliucord/styles/`) |

</details>

### Custom Properties
If a property is not listed in the table above, you can use **Reflection** to modify any View property.

**Rules:**
1. The key **must** be the full setter method name (e.g., use `"setAlpha"` instead of `"alpha"`).
2. You can access nested objects using dots (e.g., `"getPaint.setStrokeWidth"`).

**Value Parsing:**
Since JSON values for custom properties are read as strings, you must format them specifically:
* **Boolean:** `"true"` or `"false"`
* **Color:** `"#RRGGBB"` or `"#AARRGGBB"`
* **Float:** Must end with `f` (e.g., `"0.5f"`)
* **Integer:** Must end with `i` (e.g., `"10i"`)
* **String:** Default type (e.g., `"This is a string"`)

**Example:**
```json
"view_id": {
    "setAlpha": "0.8f",
    "setElevation": "4.0f"
}
```

## How to submit a style
Fill out the form [here](https://github.com/RAutobot/test/issues/new?template=submit_style.yml) and submit your issue.

## How to update a style
Fill out the form [here](https://github.com/RAutobot/test/issues/new?template=update_style.yml) and submit your issue.