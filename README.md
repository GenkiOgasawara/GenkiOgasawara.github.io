# JavaScript ハンズオン

## コメント
```js
// これはコメントです。

/*

これはコメントブロックです。
複数行にわたってコメントアウトすることができます。

*/
```

### HTML-like コメント
```js
<!--
  HTML の記法でもコメントアウトされます。
-->
```

## 変数の定義
`let` または `const` で定義されます。`var` は非推奨です。

```js
let variable = 123;
variavle = 456;

const Variable = 123;
Variavle = 456; // error
```

### use strict モード
```js
'use strict'
variavle = 123; // error
```

## 型と値の評価
- String
- Number
- Boolean
- Null
- Undefined
- Object

```js
typeof "test"
typeof 123
typeof 1.23
typeof 0xEEE
typeof null
typeof undefiend
typeof true
typeof {}
```

`console.log("test")` でコンソールに `"test"` が出力されます。

### Tips
いろんな console なんとかがあります。

```js
let message = 
  `
  これはメッセージです。
  バッククオートで囲むと
  複数行のテキストを値として
  格納することができます。
  `;
  
console.log(message)
console.info(message)
console.warn(message)
console.error(message)
```

### object 型
プロパティにアクセスするときは、`obj.prop` とドットでつなぎます。
```js
let obj = {
  'city': 'sapporo',
  'weather': 'rainy'
};

obj.weather // "rainy"
```
### 分割代入
オブジェクトのプロパティをわざわざ指定する必要がない
```
const obj = {
  "city": "sapporo",
  "weather": "rainy"
}

let city = obj.city
let weather = obj.weather

let { city, weather } = obj
```

### スプレッド構文
ベースオブジェクトの中身をそのままコピーできる

```js
const kitagasProfile = {
  "city": "sapporo",
  "company": "kitagas"
}

const myProfile = {
  "name": "tenta",
  ...kitagasProfile
}
```

## if文
JavaScript には `if` と `else` があり、`elseif` はない。
```js
function tomorrowWeather(city="sapporo"){
  if (city === "sapporo") console.log("rainy")
  else if (city === "tokyo") console.log("cloudy")
  else console.log("sunny")
}

tomorrowWeather("tokyo")
```

## 演算子
### 厳密等価演算子
等価演算子は、型変換を暗黙的に行うのであまり利用しない方がいい。
`if` 文の時は、厳密等価演算子を使うこと推奨。
`===`

`!==`


### 三項演算子
if-else文と同じ
```js
if (city === "sapporo") console.log("rainy")
else console.log("sunny")

city === "sapporo" ? console.log("rainy") : console.log("sunny")
```


引数のデフォルト値や、可変長引数 `...args` を設定することもできます。 

```js
function f(x, y, ...args){
  console.log(args)
}

f(1, 2, "str", null) // ["str", null]

function f2(x, y="default") {
  console.log(y)
}

f(1, 2) // 2
f(1) // "default"
```

### 関数の引数に分割代入
オブジェクトのプロパティを関数に代入したい場合に便利です。

```js
function todayWeather({ city }) {
  console.log(`city:${city}`)
  return city === "sapporo" ? console.log("rainy") : console.log("sunny")
}

const testCity = {
  "city": "sapporo"
}

todayWeather(testCity)
```

### Tips: `${variable}`
文字列の表現の仕方は3つありますが、 `${variable}` という書き方をすると、
文字列の中に変数を埋め込むことができます。
この場合はバッククオートで囲む必要があります。


### Tips: `else` はいらない
`return` で値を返す関数などでは、 `else` はなくても良い
※宗教戦争になるので、あまり深入りはしません
```js
function yesterdayWeather({ city }) {
  if (city === "sapporo") return "rainy" //　sapporo だった場合、ここで関数を抜ける
  return "sunny"
}

const myProfile = {
  "city": "sapporo",
  "name": "tenta"
}

const friendProfile = {
  "city": "tokyo",
  "name": "kitagas"
}

yesterdayWeather(myProfile) // rainy
yesterdayWeather(friendProfile) // sunny
```
### 無名関数と即時関数
短く書くことができる記法があります。
`this` のスコープが違うので、使い所には注意（そのうち説明します）
```
const addFunction = function(x, y){
  return x + y;
}

const multipleFunction = (x, y) => {
  return x * y;
}

const exponentionFunction = x => {
  return x ** 2;
}
```
