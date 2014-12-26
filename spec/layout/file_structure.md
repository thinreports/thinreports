# Layout File Structure

## File

|Attribute   |Value           |
|------------|----------------|
|Content Type|application/json|
|Encoding    |utf8            |

## Structures

```javascript
{
  "version":           "0.0.0",
  "finger-print":      "number",
  "config": {
    "title":           "商品伝票一覧",
    "option": {

    },
    "page": {
      "paper-type":    "A4",
      "width":         "000",
      "height":        "000",
      "orientation":   "landscape",
      "margin-top":    "20",
      "margin-bottom": "20",
      "margin-left":   "20",
      "margin-right":  "20",
    }
  },
  "svg": "<svg ...><g class=\"canvas\">...</g></svg>",
  "state": {
    "layout-guide": [{"type": "x", "position": 100},,,],
  }
}
```

### Deprecation

**Since `0.8.0`**

* `config: option`

**Since `0.7.0`**

* `config: option: pxd`

**Since `0.6.0.pre3`**

* `updated-at`
* `built-at`
* `encoding`

## Description

|Structure|Description|Value|Condition|Depth|
|---------|-----------|-----|---------|-----|
|version|作成/更新時のEditor Version|新しいEditor Versionで編集、保存された場合のみ、version を上書きする||0|
|finger-print|キャンバス + ページ設定のHash値|||0|
|config|レイアウトの設定情報|||0|
|title|帳票のタイトル|||1|
|page|[Page設定を参照](#Page)|||1|
|svg|レイアウト情報<br>Editorで作成したSVGレイアウト|||0|
|state|状態の保存|||0|
|layout-guide|[レイアウトガイド情報を参照](#Layout Guide)|Array||1|

### Page

|Structure|Description|Value|Condition|Depth|
|---------|-----------|-----|---------|-----|
|paper-type|用紙サイズ|A4, A3, B4, B5, B4_ISO, B5_ISO, user||2|
|width|用紙幅 (px)|**_BLANK_** , number|userのみ|2|
|height|用紙高さ (px)|**_BLANK_** , number|userのみ|2|
|orientation|用紙の向き|landscape, portrait||2|
|margin-top|用紙の上余白|||2|
|margin-bottom|用紙の下余白|||2|
|margin-left|用紙の左余白|||2|
|margin-right|用紙の右余白|||2|

### Layout Guide

|Structure|Description|Value|Condition|Depth|
|---------|-----------|-----|---------|-----|
|type|レイアウトガイドの種類(横/縦)|x, y||2|
|position|レイアウトガイドの位置|number||2|

## NOTE

* layout内のSVGは、 `<svg>` タグ及び、 `<g class="canvas">` グループのみを保存する。
