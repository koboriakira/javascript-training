```index.html
<!doctype html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>Hello World</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

<form>
  <div>
    <label for="name">名前:</label>
    <input type="text" name="name" id="name" />
  </div>
  <div>
    <label for="number">年齢:</label>
    <input type="number" name="age" id="age" />
  </div>
  <div>
    <label for="birthdate">誕生日:</label>
    <input type="date" name="birthdate" id="birthdate" />
  </div>
  <div>
    <label for="color">好きな色:</label>
    <input type="color" name="color" id="color" />
  </div>
  <div>
    <label for="range">範囲:</label>
    <input type="range" name="range" id="range" />
  </div>
  <div>
    <label for="memo">メモ:</label>
    <textarea name="textarea" id="memo"></textarea>
  </div>
  <div>
    <label for="breakfast">今日の朝食:</label>
    <select name="breakfast" id="breakfast">
      <option value="rice">ご飯</option>
      <option value="bread">パン</option>
      <option value="noeat">食べてない</option>
    </select>
  </div>
  <div>
    <h3>アウトドア派？ インドア派？　</h3>
    <label for="indoor">インドア派:</label>
    <input type="radio" name="radio" id="indoor" value="indoor" /><br/>
    <label for="outdoor">アウトドア派:</label>
    <input type="radio" name="radio" id="outdoor" value="outdoor" />
  </div>
  <div>
    <h3>いろんな質問</h3>
    <label for="enjoyable">JavaScriptを書くのは楽しい:</label>
    <input type="checkbox" name="enjoyable" id="enjoyable" value="enjoyable" /><br/>
    <label for="difficult">JavaScriptは難しい:</label>
    <input type="checkbox" name="difficult" id="difficult" value="difficult" />
  </div>
  <div>
    <button>実行</button>
  </div>
  <div>
    <p class="result1">
      <!-- 「実行」ボタンを押すと、この中にテキストが反映される -->
    </p>
    <p class="result2">
      <!-- 「実行」ボタンを押すと、この中にテキストが反映される -->
    </p>
  </div>
</form>

<script src="main.js"></script>
</body>
</html>
```
