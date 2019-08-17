# 查缺补漏

## 1.js中的赋值和引用

|         | =    | Function参数 |
| ------- | ---- | ------------ |
| String  | 赋值 | 赋值         |
| Number  | 赋值 | 赋值         |
| Array   | 引用 | 引用         |
| Object  | 引用 | 引用         |
| Boolean | 赋值 | 赋值         |

```js
// 利用解构赋值
let arr1 = [1, 2, 3];
let arr2 = [...arr1];

let obj1 = {a:1, b:2, c:3};
let obj2 = {...obj1};
```

