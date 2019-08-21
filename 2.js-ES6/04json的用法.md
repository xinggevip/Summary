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

## 2.json-server的增删查改

```js
$("#getBtn").click(function () {
    $.ajax({
        type: "GET", // 请求类型
        url: "http://localhost:3000/users",
        dataType: "json",  //预期服务器返回数据的类型
        success: function (data) {
            console.log(data);
            dataG = data;
            if (data) {
                //清除数据
                $("#oneTable tbody").html("");
                // 添加数据
                for (let i = 0; i < data.length; i++) {
                    $("#oneTable tbody").append("<tr><td>" + data[i]["id"] + "</td><td>" + data[i]["name"] + "</td><td>" + data[i]["phone"] + "</td><td>" + data[i]["email"] + "</td><td>" + data[i]["age"] + "</td><td>" + data[i]["companyId"] + "</td></tr>");

                };
            } else {
                alert("请求数据失败");
            }
        },
        error: function () {
            alert("发生错误");
        }
    });
});
$("#postBtn").click(function () {
    $.ajax({
        type: "POST", // 请求类型
        url: "http://localhost:3000/users",
        data: {
            "name": "测试post",
            "phone": "测试post",
            "email": "测试post",
            "age": "测试post",
            "companyId": "测试post"
        },
        dataType: "json",  //预期服务器返回数据的类型
        success: function (data) {
            console.log(data);
            if (data) {
                // 添加数据
                $("#oneTable tbody").append("<tr><td>" + data["id"] + "</td><td>" + data["name"] + "</td><td>" + data["phone"] + "</td><td>" + data["email"] + "</td><td>" + data["age"] + "</td><td>" + data["companyId"] + "</td></tr>");
                alert("添加成功");
            } else {
                alert("请求数据失败");
            }
        },
        error: function () {
            alert("发生错误");
        }
    });
});

$("#putBtn").click(function () {
    $.ajax({
        type: "PUT", // 请求类型
        url: "http://localhost:3000/users/1",
        data: {
            "name": "修改名字",
            "phone": "修改手机号",
            "email": "修改邮箱",
            "age": "修改年龄",
            "companyId": "2"
        },
        dataType: "json",  //预期服务器返回数据的类型
        success: function (data) {
            console.log(data);
            if (data) {
                // 执行getBtn得click事件 
                $("#getBtn").trigger("click");
                alert("修改成功");
            } else {
                alert("请求数据失败");
            }
        },
        error: function () {
            alert("发生错误");
        }
    });
});

$("#deltBtn").click(function () {

    $("#getBtn").trigger("click");
    let num = dataG.length - 1;
    let n = dataG[num]["id"];
    $.ajax({
        type: "DELETE", // 请求类型
        url: "http://localhost:3000/users/" + n,
        dataType: "json",  //预期服务器返回数据的类型
        success: function (data) {
            console.log(data);
            if (data) {
                // 执行getBtn得click事件 
                $("#getBtn").trigger("click");
                alert("删除成功");
            } else {
                alert("请求数据失败");
            }
        },
        error: function () {
            alert("发生错误");
        }
    });
});


$("#getBtn").trigger("click");
```

## 3.第三方Json存储平台

- ## [LeanCloud](https://leancloud.cn/)