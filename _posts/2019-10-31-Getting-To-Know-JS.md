---
layout: post
---
# Files As Programs

- Mỗi file .js là một file chương trình riêng. Lý do là để khi chạy nhiều file, nếu 1 file bị lỗi thì ko ảnh hưởng tới sự thực thi của file khác.
- Các file khi thực thi sẽ gộp chung thành 1 chương trình lớn (big program) bằng cách chia sẽ các state của nó thông qua "global scope"

# Values

- Giá trị là data, là cách mà chương trình duy trì các state của nó.
- Value có 2 dạng: **primitive** và **object**. Primitive bao gồm: strings, numbers, booleans, null, undefined cuối cùng là symbol.
- Dùng dấu back-tick `` ` `` bao một string nhằm để sử dụng biểu thức trong nó (${ .. })
- Có thể dùng `Math.PI` để biểu diễn số PI
- Giống như các ngôn ngữ khác, array index bắt đầu từ 0

# Variables

- Trong JS, value có thể xuất hiện một các nguyên thủy như `console.log("abc")` hoặc được giữ trong 1 biến (variable) `a = "abc"`.
- keyword để khai báo biến trong JS: var, let, const. `let` bị giớn hạn nhiều hơn `var`, dùng trong block như `if{}` (block scoping). `const` thì giống như `let` nhưng phải được gán giá trị lúc khai báo và không thể được gán lại, `const` nếu khai báo cho object thì vẫn có thể thay đổi giá trị vd:

```js
const actors = [ "Morgan Freeman", "Jennifer Anniston" ];

actors[2] = "Tom Cruise";   // OK :(

actors = [];                // Error!
```

- Ngoài ra còn 1 cách khai báo biến nữa là khai báo function bằng tên và biến tham số của function hoặc try catch block. Vd: 
name và hello tương tự như được khai báo bằng var, err thì như bằng let

```js
function hello(name) {
    console.log(`Hello, ${name}.`);
}

hello("Kyle");

try {
    someError();
}
catch (err) {
    console.log(err);
}
```

# Functions

- Có nhiều cách để khai báo một function (function declaration) như generator, async, export... và các function expression như IIFE, arrow function expressions. Vd:

```js
// generator function declaration
function *two() { .. }

// async function declaration
async function three() { .. }

// async generator function declaration
async function *four() { .. }

// named function export declaration (ES6 modules)
export function five() { .. }
// IIFE
(function(){ .. })();
(function namedIIFE(){ .. })();

// asynchronous IIFE
(async function(){ .. })();
(async function namedAIIFE(){ .. })();

// arrow function expressions
var f;
f = () => 42;
f = x => x * 2;
f = (x) => x * 2;
f = (x,y) => x * y;
f = x => ({ x: x * 2 });
f = x => { return x * 2; };
f = async x => {
    var y = await doSomethingAsync(x);
    return y * 2;
};
someOperation( x => x * 2 );
// ..
```

- Function nên có 1 cái tên
- Function có thể được định nghĩa trong Class hoặc Object. Vd:

```js
class SomethingKindaGreat {
    // class methods
    coolMethod() { .. }   // no commas!
    boringMethod() { .. }
}

var EntirelyDifferent = {
    // object methods
    coolMethod() { .. },   // commas!
    boringMethod() { .. },

    // (anonymous) function expression property
    oldSchool: function() { .. }
};
```
# Comparisons

- Biểu thức so sánh `===` thường được hiểu là "kiểm tra đồng thời giá trị và kiểu dữ liệu". Nó không cho phép ép kiểu trong lúc so sánh.
- Khi so sánh với NaN (not a number) thì nên sử dụng `Number.isNaN(..)` hoặc `Object.is(..)`

- Đối với object phép so `===` không dùng *structural equality* mà dùng  *identity equality*. Các object so sánh với nhau bằng reference của chúng. Vd:

```js
var x = [ 1, 2, 3 ];

// assignment is by reference-copy, so
// y references the *same* array as x,
// not another copy of it.
var y = x;

y === x;              // true
y === [ 1, 2, 3 ];    // false
x === [ 1, 2, 3 ];    // false
```

- Nếu a và b cùng kiểu dữ liệu thì dùng `==` không khác gì dùng `===`
- Nếu a và b khác kiểu nhau thì `==` ép kiểu a hoặc b về cùng 1 kiểu rồi so sánh (ưu tiên so sánh numberic, ép thành Number). Các toán tử `>`, `<`, `>=`, `<=` cũng tương tự. Vd: 

```js
var arr = [ "1", "10", "100", "1000" ];
for (let i = 0; i < arr.length && arr[i] < 500; i++) {
    // will run 3 times
}
```
- Biểu thức so sánh trong `if` statement sẽ trong như thế này:

```js
var x = 1;

if (x) {
    // will run!
}

while (x) {
    // will run, once!
    x = false;
}
```
```js
var x = "hello";

if (Boolean(x) == true) {
    // will run
}

// which is the same as:

if (Boolean(x) === true) {
    // will run
}
```
