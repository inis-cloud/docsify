### 获取【全部】页面数据

> 通过该接口，你可以获取到全部的页面数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/page</p>

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
  url:'http://api.inis.cc/api/page',
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
axios.get('http://api.inis.cc/api/page').then((res) => {
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
$url  = 'http://api.inis.cc/api/page';

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
        "page":1,
        "count":2,
        "data":[
            {
                "id":1,
                "title":"友链库",
                "alias":"page",
                "is_show":1,
                "opt":null,
                "expand":null,
                "create_time":"2021-06-20 17:01:25",
                "update_time":"2021-06-21 22:12:50"
            },
            {
                "id":2,
                "title":"留言墙",
                "alias":"message",
                "is_show":1,
                "opt":null,
                "expand":null,
                "create_time":"2021-06-20 17:39:37",
                "update_time":"2021-06-20 19:14:52"
            }
        ]
    }
}
```
</details>




### 获取【单个】页面数据

> 通过该接口，你可以获取指定页面的详细数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/page</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| id | 否 | int | 无 | 页面ID |
| alias | 否 | string | 无 | 别名 |
| cache | 否 | bool | true | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://api.inis.cc/api/page',
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
axios.get('http://api.inis.cc/api/page',{
    params:{ "alias":"links" }
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
$url  = 'http://api.inis.cc/api/page?id=1';

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
        "title":"友链库",
        "alias":"links",
        "content":"<h3>个人信息</h3>\n<p><div class=\"row\">\r\n<div class=\"col-lg-12\">\r\n<div class=\"card\">\r\n<div class=\"card-body\">\r\n<h4 class=\"header-title mb-3\"style=\"display:none;\"></h4>\r\n<ul class=\"nav nav-tabs nav-bordered mb-3\">\r\n<li class=\"nav-item\">\r\n<a href=\"#tab-f6d789c482dabac2b7209792eeb6fbb2500\"data-toggle=\"tab\"aria-expanded=\"false\"class=\"nav-link active\">\r\n<span style=\"\">自我介绍</span>\r\n</a>\r\n</li><li class=\"nav-item\">\r\n<a href=\"#tab-c05df4e3e9dd421834244a236131ebff951\"data-toggle=\"tab\"aria-expanded=\"false\"class=\"nav-link\">\r\n<span style=\"color:#ff0000;font-weight:bold;\">博主友链信息</span>\r\n</a>\r\n</li>\r\n</ul>\r\n<div class=\"tab-content\">\r\n<div class=\"tab-pane show active\"id=\"tab-f6d789c482dabac2b7209792eeb6fbb2500\">\n<div class=\"alert alert-primary bg-white text-primary\"role=\"alert\">\r\n</p>\n<ul>\n<li>我是一个非常热爱计算机的人，搭建本站的最初目的是为了整理我堆积如山的学习笔记，也为了方便一起探讨和学习。</li>\n<li>我10岁开始喜欢上计算机，13岁深入学习计算机基础知识，16岁开始学习编程知识，19岁在大学计算机网络专业学习。</li>\n<li>现今对计算机的热爱已经有十年余载，学习计算机完全是兴趣，是热爱。</li>\n<li>未来打算往IT行业的集成发展，属于计算机的技术，我都会逐一学习完，用尽我的一生。</li>\n</ul>\n<p>\r\n</div>\n</div><div class=\"tab-pane\"id=\"tab-c05df4e3e9dd421834244a236131ebff951\">\n<div class=\"alert alert-danger bg-white text-danger\"role=\"alert\">\r\n</p>\n<ul>\n<li>名称：萌卜兔's</li>\n<li>地址：https://racns.com</li>\n<li>描述：你有多努力，就有多特殊！</li>\n<li>头像：https://racns.com/usr/images/rabbit.jpg</li>\n</ul>\n<p><code>友链申请须知：</code><strong>如果你想申请本站的友链，你可以在你的博客上随便找个位置填写上我的友链信息，然后在本页评论区向我提交你的友链信息，我会根据你提交的信息拜访贵方博客，根据评定后在本站相对于的位置填写你的友链信息</strong></p>\n<hr />\n<p><button type=\"button\" class=\"btn btn-primary btn-sm\" onclick=\"window.open('https:",
        "is_show":1,
        "opt":null,
        "expand":null,
        "create_time":"2021-06-20 17:01:25",
        "update_time":"2021-06-21 22:12:50"
    }
}
```
</details>




### 【SQL】接口

> 通过该接口，你可以自己编写SQL语法获取更多自定义的数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/page/sql</p>

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
| where | id=1;is_show=1; <span style="color:red">或</span> id=1 and is_show=1 | 用 ; 号或 and 隔开多个参数 |
| whereOr | title,like,%友链%;is_show,=,1; | 用 ; 号隔开多个查询条件，每个查询条件有三个参数，用 , 号隔开 |

</details>

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://api.inis.cc/api/page/sql',
  type:'GET',
  dataType:'JSON',
  data:{
    "limit":3,
    "where":"id=1;is_show=1;"
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
axios.get('http://api.inis.cc/api/page/sql',{
    params:{
      "order"  : "id acs",
      "whereOr": "title,like,%友链%",    // 可以实现模糊搜索
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
$url  = 'http://api.inis.cc/api/page/sql?where=id=1;is_show=1;';

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
        "title":"友链库",
        "alias":"links",
        "content":"<h3>个人信息</h3>\n<p><div class=\"row\">\r\n<div class=\"col-lg-12\">\r\n<div class=\"card\">\r\n<div class=\"card-body\">\r\n<h4 class=\"header-title mb-3\"style=\"display:none;\"></h4>\r\n<ul class=\"nav nav-tabs nav-bordered mb-3\">\r\n<li class=\"nav-item\">\r\n<a href=\"#tab-f6d789c482dabac2b7209792eeb6fbb2500\"data-toggle=\"tab\"aria-expanded=\"false\"class=\"nav-link active\">\r\n<span style=\"\">自我介绍</span>\r\n</a>\r\n</li><li class=\"nav-item\">\r\n<a href=\"#tab-c05df4e3e9dd421834244a236131ebff951\"data-toggle=\"tab\"aria-expanded=\"false\"class=\"nav-link\">\r\n<span style=\"color:#ff0000;font-weight:bold;\">博主友链信息</span>\r\n</a>\r\n</li>\r\n</ul>\r\n<div class=\"tab-content\">\r\n<div class=\"tab-pane show active\"id=\"tab-f6d789c482dabac2b7209792eeb6fbb2500\">\n<div class=\"alert alert-primary bg-white text-primary\"role=\"alert\">\r\n</p>\n<ul>\n<li>我是一个非常热爱计算机的人，搭建本站的最初目的是为了整理我堆积如山的学习笔记，也为了方便一起探讨和学习。</li>\n<li>我10岁开始喜欢上计算机，13岁深入学习计算机基础知识，16岁开始学习编程知识，19岁在大学计算机网络专业学习。</li>\n<li>现今对计算机的热爱已经有十年余载，学习计算机完全是兴趣，是热爱。</li>\n<li>未来打算往IT行业的集成发展，属于计算机的技术，我都会逐一学习完，用尽我的一生。</li>\n</ul>\n<p>\r\n</div>\n</div><div class=\"tab-pane\"id=\"tab-c05df4e3e9dd421834244a236131ebff951\">\n<div class=\"alert alert-danger bg-white text-danger\"role=\"alert\">\r\n</p>\n<ul>\n<li>名称：萌卜兔's</li>\n<li>地址：https://racns.com</li>\n<li>描述：你有多努力，就有多特殊！</li>\n<li>头像：https://racns.com/usr/images/rabbit.jpg</li>\n</ul>\n<p><code>友链申请须知：</code><strong>如果你想申请本站的友链，你可以在你的博客上随便找个位置填写上我的友链信息，然后在本页评论区向我提交你的友链信息，我会根据你提交的信息拜访贵方博客，根据评定后在本站相对于的位置填写你的友链信息</strong></p>\n<hr />\n<p><button type=\"button\" class=\"btn btn-primary btn-sm\" onclick=\"window.open('https:",
        "is_show":1,
        "opt":null,
        "expand":null,
        "create_time":"2021-06-20 17:01:25",
        "update_time":"2021-06-21 22:12:50"
    }
}
```
</details>