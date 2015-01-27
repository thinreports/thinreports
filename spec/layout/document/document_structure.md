# Layout Document Structure

## Internal Data Structure

### Meta Information

```javascript
{
  title: "Title",
  fileName: "test.tlf"
}
```

### Paper Information

```javascript
{
  type: "A4",
  orientation: "landscape",
  width: "100",
  height: "100"
}
```

### Shapes

```javascript
[
  {type: "s-tblock", name: "Text Block", shapes: [{id: "text", display: "Yes"}, {}]},
  {type: "s-iblock", name: "Image Block", shapes: [{}],
  {type: "s-pageno", name: "Page Number", shapes: [{}],
  {type: "basic", name: "Basic", shapes: [{}],
  {
    type: "s-list",
    name: "List",
    shapes: [
      {
        id: "list",
        display: "Yes",
        sections: [
          {name: "Header", shapes: [{type: "s-tblock",...}, {}]
        ]},
      {...}
    ]
  }
]
```

## Layout

|用紙|幅 |高さ|用紙の向き|上余白|下余白|左余白|右余白|
|---|---|---|--------|-----|-----|----|-----|
|A4 |   |   |縦       |20   |20   |20  |20   |

## Basic

* Rectangle
* Ellipse
* Line
* Text
* Image

|ID|種別|表示|説明|
|--|---|---|---|
|rect|四角形|Yes|オーバレイ用のダミー四角形|

## Text Block

<table>
  <tr>
    <th>ID</th>
    <th>参照ID</th>
    <th>表示</th>
    <th>複数行</th>
    <th>初期値</th>
    <th colspan="3">書式</th>
    <th>説明</th>
  </tr>
  <tr>
    <td rowspan="2">text</td>
    <td rowspan="2">origin_text</td>
    <td rowspan="2">Yes</td>
    <td rowspan="2">No</td>
    <td rowspan="2">0</td>
    <td>基本</td>
    <td>種別</td>
    <td>値</td>
    <td rowspan="2">日本円を3桁区切りで表示する</td>
  <tr>
    <td>`¥{value}`</td>
    <td>数値書式</td>
    <td>`桁区切り=[,]/小数点=0`</td>
  <tr>
  </tr>
</table>

## Page Number

|書式|ID|表示|カウント対象|説明|
|---|--|---|----------|----|
|`{page}/{total}`||Yes|レポート|帳票全体に対するページ番号|

## Image Block

|ID|表示|説明|
|---|--|---|
|chart|Yes|グラフ表示用|

## List

|ID|表示|自動改ページ|ヘッダー|ページフッター|フッター|説明|
|--|---|-------|------|-----------|-------|---|
|list|Yes|Yes|Yes|Yes|Yes|一覧表です|
