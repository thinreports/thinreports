# Layout Shape Structure

## 構造の定義と規約

|Name|Structure|不要な場合|条件|
|----|---------|--------|---|
|Section|"section-name": { … }|"section_name": {}|Section自体が不要なとき|
|Attribute|"attribute-name":"…"|None|値 = Null or undefined|

## Shapeの構造定義と階層

|Structure|Description|
|---------|-----------|
|<!--SHAPE{|Top level|
|<!---SHAPE{|2nd level|
|<!----SHAPE{|3rd level|

**example**
```
<!--SHAPE{        # Top level
  <!---SHAPE{     # 2nd level
    <!----SHAPE{  # 3rd level
      :
    }SHAPE---->
  }SHAPE--->
}SHAPE-->
```

## Original Shapeの構造定義

|Structure|Description|
|---------|-----------|
|`<!--LAYOUT`|ShapeのLayout定義領域の開始|
|`<g or rect or ellipse or line ...>`|ShapeのLayout定義 (オリジナルそのまま)|
|`LAYOUT-->`|ShapeのLayout定義領域の終了|

### NOTE

実際は、`<!--LAYOUT...LAYOUT-->`中に一切の改行を含めない。

**example**

```
<!--LAYOUT<g class=\"s-tblock\" ... >...</g>LAYOUT-->
```

## Structure

### Basic

```javascript
<!--SHAPE
{
  "type": "s-rect",
  "id": "rect_1",
  "desc": "説明",
  "display": "true",
  "svg": {
    "tag": "rect",
    "attrs": {
      "svgAttrKey": [svgAttrValue],
           :
    }
  }
}
SHAPE-->
```

### Image

```javascript
<!--SHAPE
{
  "type": "s-image",
  "id": "image",
  "desc": "説明",
  "display": "true",
  "background": "false",
  "svg": {
    "tag": "rect",
    "attrs": {
      "svgAttrKey": [svgAttrValue],
           :
    }
  }
}
SHAPE-->
```

### Text

```javascript
<!--SHAPE
{
  "type": "s-text",
  "id": "text_1",
  "desc": "説明",
  "display": "true",
  "line-height": 20.0,
  "valign": "top",
  "box":{
    "x": 100.0,
    "y": 100.0,
    "width": 100.0,
    "height": 100.0
  },
  "inline-format": "false",
  "text":["hoge","foo"],
  "svg": {
    "tag": "g",
    "attrs": {
      "svgAttrKey": [svgAttrValue],
           :                      ,
    "content": "",
    }
  }
}
SHAPE-->
```

### Image Block

```javascript
<!--SHAPE
{
  "type": "s-iblock",
  "id": "block_1",
  "desc": "説明",
  "display": "true",
  "position-x": "left",
  "position-y": "top",
  "box":{
    "x": 100,
    "y": 100,
    "width": 100,
    "height": 100
  },
  "svg": {
    "tag": "image",
    "attrs": {
      "svgAttrKey": [svgAttrValue],
           :
    }
  }
}
SHAPE-->
```

### Text Block

```javascript
<!--SHAPE
{
  "type": "s-tblock",
  "id": "block_1",
  "desc": "説明",
  "ref-id": "block_2",
  "value": "0",
  "display": "true",
  "multiple": "false",
  "line-height": 20.0,
  "valign": "top",
  "overflow": "truncate",
  "word-wrap": "break-word",
  "box":{
    "x": 100,
    "y": 100,
    "width": 100,
    "height": 100
  },
  "inline-format": "false",
  "format": {
    "base": "\ {value}",
    "type": "datetime",
    "datetime": {
      "format": "%Y/%m/%d"
    },
//          or
    "number": {
      "delimiter": ",",
      "precision ": 3
    },
//          or
    "padding": {
      "length": 5,
      "char": 0,
      "direction": "L"
    },
  },
  "svg": {
    "tag": "textArea",
    "content": "",
    "attrs": {
      "svgAttrKey": [svgAttrValue],
           :
    }
  }
}
SHAPE-->
```

### List

```javascript
<!--SHAPE
{
  "type": "s-list",
  "id": "list_1",
  "desc": "説明",
  "display": "true",
  "content-height": 100,
  "page-break":"true",
  "header-enabled": "true",
  "page-header-enabled": "true",
  "page-footer-enabled": "true",
  "footer-enabled": "true",
  "header": {
    "height": 10,
    "translate":{ "x": 100, "y": 100 },
    "svg ": {
      "tag": "g",
      "content": "…"
    }
  },
  "page-header": {
    "height": 10,
    "translate":{ "x": 100, "y": 100 },
    "svg ": {
      "tag": "g",
      "content": "…"
    }
  },
  "detail": {
    "height": 10,
    "translate":{ "x": 100, "y": 100 },
    "svg": {
      "tag": "g",
      "content": "…"
    }
  },
  "page-footer": {
    "height": 10,
    "translate":{ "x": 100, "y": 100 },
    "svg ": {
      "tag": "g",
      "content": "…"
    }
  },
  "footer": {
    "height": 10,
    "translate":{ "x": 100, "y": 100 },
    "svg ": {
      "tag": "g",
      "content": "…"
    }
  },
  "sections": {
    "section_id": {
      "height": 10,
      "translate":{ "x": 100, "y": 100 },
      "svg ": {
        "tag": "g",
        "content": "…"
      }
    },
    "section_id": {"…"},
    "section_id": {"…"}
    }
  },
  "svg": {
    "tag": "g",
    "attrs": {}
  }
}
SAHPE-->
```

### Page Number

```javascript
<!--SHAPE
{
  "type": "s-pageno",
  "id": "",
  "display": "true",
  "desc": "説明",
  "box":{
    "x": 100,
    "y": 100,
    "width": 100,
    "height": 100
  },
  "format": "{page} / {total}",
  "overflow": "truncate",
  "target": "",
  "svg": {
    "attrs": {
      "svgAttrKey": [svgAttrValue],
           :
    }
  }
}
SHAPE-->
```

## Description

### Basic

|Structure|Description|Value|Depth|
|---------|-----------|-----|-----|
|type|Shape種別|s-tblock, s-rect, s-ellipse, s-line, s-text, s-image, s-ibock, s-pageno, s-list|0|
|id|ShapeID。帳票Parse時にRailsから参照する際のキーになる||0|
|desc|この図形に対する説明|~~idが設定されている場合のみ有効~~|0|
|display|可視状態|**_true_**, false|0|
|svg|帳票Parse時に作成される実際のSVG定義||0|
|tag|SVGタグ名|rect, ellipse, line, image, text, textArea|1|
|attrs|SVGタグの属性||1|
|svgAttrKey|必要最小限の属性のみ。<br>class 属性やstyle属性など、描画される際に不要な属性は含めてはならない。||2|

### Image

|Structure|Description|Value|Depth|
|---------|-----------|-----|-----|
|background|背景へ（未実装）|**_false_**, true|0|

### Text

|Structure|Description|Value|Depth|
|---------|-----------|---------|-----------|
|content|子要素|**_BLANK_**, ANY|1|
|line-height|行間(一行の高さ)|**_BLANK_**, NUMBER|0|
|valign|box内の縦方向の配置|**_BLANK (=top)_**, top, center, bottom|0|
|box|描画時の領域を表す情報|{<br>"x": number,<br>"y": number,<br>"width": number,<br>"height": number<br>}|0|
|inline-format|インラインスタイルの許可|**_false_**, true|0|
|text|テキスト内容が保持されている配列であり、<br>単一行の場合は一つの要素を持つ配列、<br>複数行は、行数分の要素を持った配列となる|Array|0|

### Image Block

|Structure|Description|Value|Condition|Depth|
|---------|-----------|---------|-----------|---------|
|position-x|box内の横方向の配置|**_BLANK (=left)_**, left, center, right||0|
|position-y|box内の縦方向の配置|**_BLANK (=top)_**, top, center, bottom||0|
|box|描画時の領域を表す情報|{<br>"x": number,<br>"y": number,<br>"width": number,<br>"height": number<br>}||0|

### Text Block

|Structure|Description|Value|Condition|Depth|
|---------|-----------|---------|-----------|---------|
|ref-id|参照するTblockShapeID。|_BLANK_, ANY||0|
|value|デフォルト値|**_BLANK_**, ANY||0|
|multiple|複数行|true, **_false_**||0|
|line-height|行間(一行の高さ)|**_BLANK_**, NUMBER||0|
|valign|box内の縦方向の配置|**_BLANK (=top)_**, top, center, bottom||0|
|overflow|溢れたときの処理方法|**_BLANK (=truncate)_**, truncate, fit, expand||0|
|word-wrap|単語途中の改行設定|**_BLANK (=ja: none, en: break-word)_**, none, break-word||0|
|box|描画時の領域を表す情報|{<br>"x": number,<br>"y": number,<br>"width": number,<br>"height": number<br>}||0|
|inline-format|インラインスタイルの許可|**_false_**, true||0|
|format|簡易書式設定|||0|
|base|基本書式 ※ `{value}` に値が埋め込まれる|**_BLANK_**, ANY||1|
|type|書式種別|**_BLANK_**, datetime, number, padding||2|
|datetime|[日付時刻関連の書式設定を参照](#Datetime)||type == 'datetime' のみ存在|2|
|number|[数値関連の書式設定を参照](#Number)||type == 'number' のみ存在|2|
|padding|[文字詰め関連の書式設定を参照](#Padding)||type == 'padding' のみ存在|2|

#### Datetime

|Structure|Description|Value|Condition|Depth|
|---------|-----------|---------|-----------|---------|
|format|書式|**_BLANK_**, ANY|type == 'datetime' のみ存在|3|

#### Number

|Structure|Description|Value|Condition|Depth|
|---------|-----------|---------|-----------|---------|
|delimiter|カンマ区切り設定|**_BLANK_**, ANY|type == 'number' のみ存在|3|
|precision|小数点書式設定|**_0_**, NUMBER|type == 'number' のみ存在|3|


#### Padding

|Structure|Description|Value|Condition|Depth|
|---------|-----------|---------|-----------|---------|
|length|字詰めの長さ|**_0_**, NUMBER|type == 'padding' のみ存在|3|
|char|字詰め文字|**_0_**, NUMBER|type == 'padding' のみ存在|3|
|direction|字詰め方向|**_L_**, R|type == 'padding' のみ存在|3|

### List

|Structure|Description|Value|Depth|
|---------|-----------|-----|-----|
|content-height|有効な高さ（全体の高さ－ヘッダーの高さ）|NUMBER|0|
|page-break|改ページ対象|**_true_**, false|0|
|header-enabled|ヘッダーの有無|**_true_**, false|0|
|page-header-enabled|ページヘッダーの有無|**_true_**, false|0|
|page-footer-enabled|ページフッターの有無|**_true_**, false|0|
|footer-enabled|フッターの有無|**_true_**, false|0|
|header|[ヘッダー情報を参照](#Header)||0|
|page-header|[ページヘッダー情報を参照](PageHeader)||0|
|detail|[詳細部を参照](#Detail)||0|
|page-footer|[ページフッター（各ページの末尾に表示）を参照](PageFooter)||0|
|footer|[リストフッター（最終行の末尾に表示）を参照](Footer)||0|
|sections|未実装||0|
|svg|帳票Parse時に作成される実際のSVG定義||0|
|tag|SVGタグ名g固定||1|
|attrs|SVGタグの属性(空)||1|

#### Header

|Structure|Description|Value|Depth|
|---------|-----------|-----|-----|
|svg|SVG||1|
|tag|SVGコンテナタグg固定||2|
|content|SVGレイアウト( Shape Structure 要変換)|**_BLANK_**, ANY|2|
|attrs|SVGタグの属性||2|

#### Page Header

|Structure|Description|Value|Depth|
|---------|-----------|-----|-----|
|svg|SVG||1|
|tag|SVGコンテナタグg固定||2|
|content|SVGレイアウト( Shape Structure 要変換)|**_BLANK_**, ANY|2|
|attrs|SVGタグの属性||2|

#### Detail

|Structure|Description|Value|Depth|
|---------|-----------|-----|-----|
|height|一行の高さ|NUMBER|1|
|translate|現在のTranslate情報|NUMBER|1|
|svg|SVG||1|
|tag|SVGコンテナタグg固定||2|
|content|SVGレイアウト( Shape Structure 要変換)|**_BLANK_**, ANY|2|

#### Page Footer

|Structure|Description|Value|Depth|
|---------|-----------|-----|-----|
|height|高さ(Pixel)|NUMBER|1|
|translate|一行目の底辺に位置するようなtranslate値|NUMBER|1|
|svg|SVG||1|
|tag|SVGコンテナタグg固定||2|
|content|SVGレイアウト( Shape Structure 要変換)|**_BLANK_**, ANY|2|

#### Footer

|Structure|Description|Value|Depth|
|---------|-----------|-----|-----|
|height|高さ(Pixel)|NUMBER|1|
|translate|一行目の底辺に位置するようなtranslate値|NUMBER|1|
|svg|SVG||1|
|tag|SVGコンテナタグg固定||2|
|content|SVGレイアウト( Shape Structure 要変換)|**_BLANK_**, ANY|2|

### Page Number

|Structure|Description|Value|Condition|Depth|
|---------|-----------|---------|-----------|---------|
|box|描画時の領域を表す情報|{<br>"x": number,<br>"y": number,<br>"width": number,<br>"height": number<br>}||0|
|format|書式|**_BLANK_**, ANY||0|
|overflow|溢れたときの処理方法|**_BLANK (=truncate)_**, truncate, fit, expand||0|
|target|カウント対象|**_BLANK (=report)_**, List ID||0|
