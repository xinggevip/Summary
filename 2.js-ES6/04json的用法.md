# json的用法

## 1.json的增删查改

### 1.1增

`json.key = value;`

`json["key"] = value;`

```js
let json4 = {
    a:1,
    b:2,
    c:3
};
json4.name = "Tom";
json4["age"] = 18;
console.log( json4 );	// {a: 1, b: 2, c: 3, name: "Tom", age: 18}
```

### 1.2删

`delete json.key;`

`delete.json["key"];`

```js
// 删除属性
let json5 = {
    a:1,
    b:2,
    c:3
};
delete json5.a;
delete json5["b"];
console.log( json5 );   //{c: 3}
```

### 1.3读取

`json.key;`

`json["key"];`

```js
// 获取属性值
let json6 = {
    a:1,
    b:2,
    c:3
};
console.log( json6.a, json6["b"] );	// 1 2
```

### 1.4修改

`json.key = value;`

`json["key"] = value;`

```js
// 修改属性值
let json7 = {
    a:1,
    b:2,
    c:3
};
json7.a = "修改a";
json7["b"] = "修改b";
console.log( json7 );   // {a: "修改a", b: "修改b", c: 3}
```

### 1.5遍历

```js
// 遍历Object
let json8 = {
    name:"Tom",
    sex:"boy",
    age:18
};
for(let key of Object.entries(json8)){
    // name sex age    Object.keys(Obj)
    // Tom boy 18    Object.values(Obj)
    // ["name", "Tom"] ["sex", "boy"] ["age", 18]    Object.entries(Obj)
    console.log( key );
};

// 解构Object
let {keys, values, entries} = Object;
for(let key of keys(json8)){
    console.log(key);   // name sex age
};

for(let key of values(json8)){
    console.log(key);   // Tom boy 18
};

for(let key of entries(json8)){
    console.log(key);   // ["name", "Tom"] ["sex", "boy"] ["age", 18]
};

// 解构json，设置默认值
let json9 = {
    b:2,
    c:3,
    d:4,
    e:5
};

function getJson({a=10,b,c,...x}){
    console.log(a,b,c,x);
};
getJson(json9); // 10 2 3 {d: 4, e: 5}
```

