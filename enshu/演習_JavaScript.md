# 演習(JavaScript)

このURLは https://github.com/koboriakira/javascript-training/blob/main/enshu/%E6%BC%94%E7%BF%92_JavaScript.md

はじめて取り組む場合は、末尾の「準備」をまず行ってください。

## 課題

後述のテーマ例、もしくは自身でテーマを決め、それを解決するプログラムを作成せよ。

### 提出方法

ページ右下の「ブックを終了する」ボタンをクリックすれば、勝手に提出されます。  
提出は何度でも可能ですので、保存機能として使ってもらって大丈夫です。

### 提出期限

本講義の最終日まで


### テーマ例

#### じゃんけんプログラム

選手A,Bそれぞれがランダムにグー、チョキ、パーを出すとして、勝利者を出力する。

利用する関数: `getRandonString`

#### 家計簿プログラム

CSVファイルに記録したデータをもとに、家計簿を作成する。
また何かしら分析を行う。

利用する関数: `readCSV`

#### 簡易RPGプログラム

勇者がランダムに出現するさまざまなモンスターを何体倒せるか。
HPがゼロになったら終了。敵を倒すとレベルアップして攻撃力が上がったりする。
モンスターのデータはCSVファイルで管理され、その中からランダムで1体出現する。

利用する関数: `readCSV`, `getRandomNumber`(もしくは`getRandonString`)

### 自身でテーマを決める場合

講師側で用意している関数は、次の通りです。

- CSVファイルの中身を読み取る: 表形式のデータを準備できます
- ランダムに数字を作成する: 「1から10の間でランダムに決める」ような操作ができます
- 選択肢の中からランダムに1つ選ぶ: 「好きな数の選択肢から1つを選ぶ」操作ができます

上記の機能（とくにCSVファイルの読込）を使う前提で、どんなプログラムが作れそうか考えてみてください。
また上記以外にも「こういう操作をやりたいんだけど」みたいな相談をしてもらえれば、都度判断します。

## 評価方法、アドバイス

- data.csvにデータを入れた状態で、自身の意図した通りになにかのプログラムが動けば原則OKです
  - 動作さえすれば提出物の中身に応じて大きく評価が異なることはありません
- そのうえでプラスアルファの評価は次の点で決まります
  - プログラムの面白さ。解決したい問題が明確で、解決できているかどうか
  - さまざまなデータを入れても動作するか
- 一方で「たくさんコードが書かれているかどうか（行数の長さ）」はとくに評価には入りません
- **より上級なエンジニアを目指したい生徒は、以下の観点で実装してみましょう**
  - 関数を切り出す。上から下にコードが流れて終了、ではなく、その途中の処理をひとつの独立した関数として切り出してみましょう
  - オブジェクトを利用する。データを取り扱うとき、あるひとかたまりのデータをオブジェクトとして表現してみましょう


## よくある質問

### プログラム実行中に入力をすることはできる？（ex.途中でじゃんけんの手を入力させる）

不可です。
通常は可能なのですが、このTrack Trainingの仕組み上だと難しく、今回は見送っています。すみません。

### 提出は必須ですか？

任意で結構です。提出がないと単位が取得できないことはありません。
ただし高評価をもらうためには提出が必須となります。

## 準備

### 1. ファイルを新規作成する

次の3つのファイルを新規作成してください。

- utils.js
- README.md
- data.csv

### 2. ファイルの中身をコピペで準備する

#### utils.js

```utils.js
/**
 * 【変更禁止】
 * 講師の準備した、各種関数です
 */
const fs = require('fs');

/*
 * 指定したCSVのファイルを読み込みます
 * 
 * [使い方]
 * 
 * ```
 * const data = readCSV('data.csv')
 * console.log(data[0]) // [ 'ジュース', '120' ]
 * console.log(data[1]) // [ '服', '1000' ]
 * ```
 *
 */
function readCSV(filePath) {
    try {
        const data = fs.readFileSync(filePath, 'utf8');
        const lines = data.split('\n');
        const results = lines.map(line => line.split(','));
        return results;
    } catch (error) {
        console.error(error)
        throw new Error("CSVファイルの読込に失敗しました。ファイル名とCSVの中身を確認してください。")
    }
}

/**
 * 指定したmix, maxに応じて、minからmaxの間の整数をランダムで返します
 * 
 * [使い方]
 * const number = getRandomNumber(-100, 100)
 * console.log(number) // 12　※-100から100の間のランダムな数
 */
function getRandomNumber(min, max) {
    if (min == null || max == null) {
      throw new Error("minおよびmaxを指定してください")
    } 
    return Math.floor(Math.random() * (max - min + 1)) + min;
}

/**
 * 指定した任意の数の文字列から、ランダムでひとつが選ばれます
 * 
 * [使い方]
 * const hand = getRandomString("グー", "チョキ", "パー")
 * console.log(hand) // チョキ　※グー、チョキ、パーからランダムで選ばれる
 */
function getRandomString(...strings) {
    const randomIndex = Math.floor(Math.random() * strings.length);
    return strings[randomIndex];
}



module.exports = {readCSV, getRandomNumber, getRandomString}
```

#### README.md

```README.md
## なにを作ったか？

（どんなプログラムをつくったかを簡潔に説明してください。「〜ができる」とか「〜を表示する」などです）

## 使い方のメモ

（とくにdata.csvの形式があれば教えてください。ex.1列目は商品名、2列目は金額）
```

#### data.csv

```data.csv
ジュース,120
本,500
```

### 3. main.jsの中身をコピペして上書きする

```main.js
const { readCSV, getRandomNumber, getRandomString } = require('./utils.js')

// 以下は利用例
const data = readCSV('data.csv')
console.log(data[0]) // [ 'ジュース', '120' ]
console.log(data[1]) // [ '服', '1000' ]

const hand = getRandomString("グー", "チョキ", "パー")
console.log(hand)

const number = getRandomNumber(-100, 100)
console.log(number) // 12　※-100から100の間のランダムな数
```
