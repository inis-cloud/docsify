### 获取【全部】公告数据

> 通过该接口，你可以获取到全部的公告数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/placard</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| limit | 否 | int | 5 | 数据数量 |
| page | 否 | int | 1 | 分页请求 |
| order | 否 | string | create_time desc | 排序方式 |
| cache | 否 | bool | true | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://api.inis.cc/api/placard',
  type:'GET',
  dataType:'JSON',
  success: (res) => {
	// 状态码 200 表示请求成功
	if(res.code === 200){
	  console.log(res.data)
	}else{
	  console.log(res)
	}
  }
})
</script>
```

#### ** axios **

```html
<!-- 导入axios -->
<script src="//unpkg.com/axios/dist/axios.min.js"></script>

<script>
axios.get('http://api.inis.cc/api/placard').then((res) => {
  // 状态码 200 表示请求成功
  if(res.data.code == 200){
	console.log(res.data)
  }else{
	console.log(res)
  }
})
</script>
```

#### ** php **

```php
<?php
// 定义头部信息
header('content-type:application/json');
// API接口
$url  = 'http://api.inis.cc/api/placard';

$curl = curl_init(); 
curl_setopt($curl,CURLOPT_URL,$url); 
curl_setopt($curl,CURLOPT_RETURNTRANSFER,true);
$data = curl_exec($curl); 
curl_close($curl);     

// 输出数据
echo $data;
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "code":200,
    "msg":"数据请求成功！",
    "data":[
        {
            "id":1,
            "title":"公告",
            "type":"wechat",
            "content":"这是一条测试的公告内容",
            "opt":null,
            "expand":null,
            "longtext":null,
            "create_time":"2021-10-26 20:02:56",
            "update_time":"2021-10-26 20:32:47"
        },
        {
            "id":2,
            "title":"QQ",
            "type":"qq",
            "content":"这是一条QQ公告",
            "opt":null,
            "expand":null,
            "longtext":null,
            "create_time":"2021-10-26 20:47:43",
            "update_time":"2021-10-26 20:47:43"
        },
        {
            "id":3,
            "title":"网站公告",
            "type":"web",
            "content":"这是一条网站公告",
            "opt":null,
            "expand":null,
            "longtext":null,
            "create_time":"2021-10-26 21:09:59",
            "update_time":"2021-10-26 21:10:25"
        }
    ]
}
```
</details>




### 获取【一条】公告数据

> 通过该接口，你可以获取指定公告的详细数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/placard</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| id | 否 | int | 无 | 公告ID |
| cache | 否 | bool | true | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://api.inis.cc/api/placard',
  type:'GET',
  dataType:'JSON',
  data: {"id":1},
  success: (res) => {
	// 状态码 200 表示请求成功
	if(res.code === 200){
	  console.log(res.data)
	}else{
	  console.log(res)
	}
  }
})
</script>
```

#### ** axios **

```html
<!-- 导入axios -->
<script src="//unpkg.com/axios/dist/axios.min.js"></script>

<script>
axios.get('http://api.inis.cc/api/placard',{
    params:{ "id":1 }
  }).then(res=>{
    // 状态码 200 表示请求成功
    if(res.data.code == 200){
      console.log(res.data)
    }else{
      console.log(res)
    }
})
</script>
```

#### ** php **

```php
<?php
// 定义头部信息
header('content-type:application/json');
// API接口
$url  = 'http://api.inis.cc/api/placard?id=1';

$curl = curl_init(); 
curl_setopt($curl,CURLOPT_URL,$url); 
curl_setopt($curl,CURLOPT_RETURNTRANSFER,true);
$data = curl_exec($curl); 
curl_close($curl);     

// 输出数据
echo $data;
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "code":200,
    "msg":"数据请求成功！",
    "data":{
        "id":1,
        "title":"公告",
        "type":"wechat",
        "content":"这是一条测试的公告内容",
        "opt":null,
        "expand":null,
        "longtext":null,
        "create_time":"2021-10-26 20:02:56",
        "update_time":"2021-10-26 20:32:47"
    }
}
```
</details>




### 【SQL】接口

> 通过该接口，你可以自己编写SQL语法获取更多自定义的数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/placard/sql</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| limit | 否 | int | 5 | 数据数量 |
| page | 否 | int | 1 | 分页请求 |
| order | 否 | string | create_time desc | 排序方式 |
| where | 否 | string | 无 | 条件查询 |
| whereOr | 否 | string | 无 | 条件查询 |
| cache | 否 | bool | true | 是否获取缓存数据 |

<br>
<details>
<br>
<summary class="violet">字段说明</summary>

| 参数名称 | 语法 | 说明 |
| :---- | :---- | :---- |
| where | id=1;type=qq; <span style="color:red">或</span> id=1 and type=qq | 用 ; 号或 and 隔开多个参数 |
| whereOr | type,=,qq;type,=,web; | 用 ; 号隔开多个查询条件，每个查询条件有三个参数，用 , 号隔开 |

</details>

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://api.inis.cc/api/placard/sql',
  type:'GET',
  dataType:'JSON',
  data:{
    "whereOr":"type,=,qq;type,=,web;"
  },
  success:function (res) {
	// 状态码 200 表示请求成功
	if(res.code === 200){
	  console.log(res.data)
	}else{
	  console.log(res)
	}
  }
})
</script>
```

#### ** axios **

```html
<!-- 导入axios -->
<script src="//unpkg.com/axios/dist/axios.min.js"></script>

<script>
axios.get('http://api.inis.cc/api/placard/sql',{
    params:{
      "whereOr": "type,=,qq;type,=,web;",    // 可以实现获取QQ和网站的分类数据
    }
  }).then(res=>{
    // 状态码 200 表示请求成功
    if(res.data.code == 200){
      console.log(res.data)
    }else{
      console.log(res)
    }
})
</script>
```

#### ** php **

```php
<?php
// 定义头部信息
header('content-type:application/json');
// API接口
$url  = 'http://api.inis.cc/api/placard/sql?whereOr=type,=,qq;type,=,web;';

$curl = curl_init(); 
curl_setopt($curl,CURLOPT_URL,$url); 
curl_setopt($curl,CURLOPT_RETURNTRANSFER,true);
$data = curl_exec($curl); 
curl_close($curl);     

// 输出数据
echo $data;
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "code":200,
    "msg":"ok",
    "data":{
        "page":1,
        "count":2,
        "data":[
            {
                "id":3,
                "title":"网站公告",
                "type":"web",
                "content":"这是一条网站公告",
                "opt":null,
                "expand":null,
                "longtext":null,
                "create_time":"2021-10-26 21:09:59",
                "update_time":"2021-10-26 21:10:25"
            },
            {
                "id":2,
                "title":"QQ",
                "type":"qq",
                "content":"这是一条QQ公告",
                "opt":null,
                "expand":null,
                "longtext":null,
                "create_time":"2021-10-26 20:47:43",
                "update_time":"2021-10-26 20:47:43"
            }
        ]
    }
}
```
</details>




