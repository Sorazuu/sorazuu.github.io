---
layout: post
---
### Files As Programs  
- Mỗi file .js là một file chương trình riêng. Lý do là để khi chạy nhiều file, nếu 1 file bị lỗi thì ko ảnh hưởng tới sự thực thi của file khác.
- Các file khi thực thi sẽ gộp chung thành 1 chương trình lớn (big program) bằng cách chia sẽ các state của nó thông qua "global scope"
### Values
- Giá trị là data, là cách mà chương trình duy trì các state của nó.
- Value có 2 dạng: **primitive** và **object**. Primitive bao gồm: strings, numbers, booleans, null, undefined cuối cùng là symbol.
- Dùng dấu back-tick `` ` `` bao một string nhằm để sử dụng biểu thức trong nó (${ .. })
- Có thể dùng `Math.PI` để biểu diễn số PI
- Giống như các ngôn ngữ khác, array index bắt đầu từ 0
### Variables
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

