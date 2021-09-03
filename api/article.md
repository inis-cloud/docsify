### 获取【全部】文章数据

> 通过该接口，你可以获取到全部的文章数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/article</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| limit | 否 | int | 5 | 数据数量 |
| page | 否 | int | 1 | 分页请求 |
| order | 否 | string | <span class="violet">create_time desc</span> | 排序方式 |
| mode | 否 | string | <span class="violet">html</span> | 文章渲染模式 |
| search | 否 | string | null | 文章标题或内容搜索 |
| login-token | 否 | string | 无 | [登录密钥] 用于判断是否拥有显示隐藏文章的权限 |
| cache | 否 | bool | true | 是否获取缓存数据 |

<br>
<details>
<summary class="violet">字段说明</summary>

> `acs`　升序排列 (即：从小到大排序)   
> `desc` 降序排列 (即：从大到小排序)

| 参数名称 | 可选值 | 说明 |
| :---- | :---- | :---- |
| order | id | 根据ID排序 |
| order | is_top | 根据置顶排序 |
| order | views | 根据浏览量排序 |
| order | font_count | 根据文章字数排序 |
| order | create_time | 根据创建时间排序 |
| order | update_time | 根据更新时间排序 |
| model | md | Markdown文本 |
| model | html | HTML文本 |

</details>

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://api.inis.cc/api/article',
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
axios.get('http://api.inis.cc/api/article').then((res) => {
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
$url  = 'http://api.inis.cc/api/article';

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

> `expand` 内的数据为后端优化并处理过的数据，请优先使用 `expand` 内的数据

```json
{
    "code":200,
    "msg":"数据请求成功！",
    "data":{
        "data":[
            {
                "id":68,
                "title":"cedsss测试分页",
                "description":"&lt;p&gt;&lt;br&gt;&lt;/p&gt;",
                "is_top":0,
                "is_show":1,
                "img_src":"",
                "views":1,
                "font_count":null,
                "sort_id":"|14|",
                "tag_id":null,
                "users_id":1,
                "expand":{
                    "sort":[
                        {
                            "id":14,
                            "name":"ThinkPHP6"
                        }
                    ],
                    "author":{
                        "nickname":"兔子",
                        "head_img":"https://racns.com/usr/images/userHead.gif",
                        "email":"racns@qq.com",
                        "address_url":"https://inis.cn",
                        "description":"许一人以偏爱，尽此生之慷慨！"
                    },
                    "comments":0
                },
                "opt":null,
                "create_time":"2021-01-21 12:57:56",
                "update_time":"2021-01-21 13:22:58"
            },
    		... ... 
    		{...},
    		{...}
        ],
        "page":1,
        "count":4
    }
}
```
</details>




### 获取【一篇】文章数据

> 通过该接口，你可以获取指定文章的详细数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/article</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| id | 否 | int | null | 文章ID |
| mode | 否 | string | <span class="violet">html</span> | 文章渲染模式 |
| password | 否 | string | null | 如果文章设置了密码可见，需要提交密码，才能看到内容 |
| login-token | 否 | string | 无 | [登录密钥] 用于判断是否拥有显示隐藏文章的权限 |
| cache | 否 | bool | true | 是否获取缓存数据 |

<br>
<details>
<br>
<summary class="violet">字段说明</summary>

| 参数名称 | 可选值 | 说明 |
| :---- | :---- | :---- |
| model | md | Markdown文本 |
| model | html | HTML文本 |

</details>

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://api.inis.cc/api/article',
  type:'GET',
  dataType:'JSON',
  data:{"id":1},
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
axios.get('http://api.inis.cc/api/article',{
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
$url  = 'http://api.inis.cc/api/article?id=1';

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

> `expand` 内的数据为后端优化并处理过的数据，请优先使用 `expand` 内的数据

```json
{
    "code":200,
    "msg":"数据请求成功",
    "data":{
        "id":1,
        "title":"inis系统",
        "description":"这是一个描述",
        "content":"&lt;div&gt;&lt;h2&gt;&lt;span style="color: rgb(102, 102, 102); font-family: "Source Sans Pro", "Hiragino Sans GB", "Microsoft Yahei", SimSun, Helvetica, Arial, sans-serif, monospace; font-size: 24px;"&gt;简介呀&lt;/span&gt;&lt;/h2&gt;&lt;ul&gt;&lt;li&gt;很久以前就有想过要自己做一个网站，一个类似博客的网站，但是一直担心自己做不好，所以一年前开始使用Typecho系统和handsome主题，并做出了AliceStyle插件。&lt;/li&gt;&lt;li&gt;身为一个前端，就针对Typecho而言，在众多Typecho插件中，我觉得我的AliceStyle已经是一款优秀的作品，我没有愧对各位小伙伴对我的信任。&lt;/li&gt;&lt;li&gt;AliceStyle插件是Typecho系统中第一个插件定义美化的插件，将一切美化全部交付给插件处理，在AliceStyle诞生之前，没有任何一款插件是对前台和后台进行美化的，只有AliceStyle是第一款这么做的插件。&lt;/li&gt;&lt;li&gt;这一年来的频繁更新和不断的插件升级，已经让大家的AliceStyle插件接近完美。&lt;/li&gt;&lt;li&gt;据不完全统计，这一年里AliceStyle插件的用户增长量已经突破1000+用户量，可以说这是一件很优秀的作品。&lt;/li&gt;&lt;li&gt;过一段时间，我将不再使用Typecho系统，也不再使用handsome主题，尽管他们已经足够完善，但我希望我能做出比他们更好的作品。&lt;/li&gt;&lt;li&gt;届时我会带着全新的作品归来，inis，这是我对我的下一件作品的命名，希望各位小伙伴能喜欢。&lt;/li&gt;&lt;/ul&gt;&lt;h2&gt;&lt;span style="color: rgb(102, 102, 102); font-family: "Source Sans Pro", "Hiragino Sans GB", "Microsoft Yahei", SimSun, Helvetica, Arial, sans-serif, monospace; font-size: 24px;"&gt;inis - 博客新系统&lt;/span&gt;&lt;/h2&gt;&lt;ol&gt;&lt;li&gt;前后端分离系统 - 提高响应和渲染的速度&lt;/li&gt;&lt;li&gt;以美为主 - 创新的布局，优雅的配色&lt;/li&gt;&lt;li&gt;操作简单 - 大大降低操作难度，个性化程度高&lt;/li&gt;&lt;li&gt;svg动画 - 让页面充满活性&lt;/li&gt;&lt;/ol&gt;&lt;ul style="margin: 1.5em 0px; color: rgb(119, 119, 119); font-family: "Source Sans Pro", "Hiragino Sans GB", "Microsoft Yahei", SimSun, Helvetica, Arial, sans-serif, monospace; font-size: 12px;"&gt;&lt;li&gt;所有的设计都在我的脑海里，这里我们只谈未来方向。&lt;/li&gt;&lt;li&gt;未来我希望能开放inis系统，让更多的开发者进来开发插件或主题。&lt;/li&gt;&lt;li&gt;其次主题的开发程度将会大大的降低，即便不懂代码的用户也能通过调色的方式，随意改变任何区域的样式&lt;/li&gt;&lt;li&gt;并且我希望能建立一个生态，类似一个交流的社区，供大家分享自己的教程和使用技巧&lt;/li&gt;&lt;/ul&gt;&lt;h2&gt;&lt;br&gt;&lt;/h2&gt;&lt;/div&gt;",
        "is_top":0,
        "is_show":1,
        "img_src":"https://racns.com/usr/uploads/2020/09/3993362207.jpg",
        "views":697,
        "font_count":10000,
        "sort_id":"|1|14|",
        "tag_id":"",
        "users_id":1,
        "expand":{
            "sort":[
                {
                    "id":1,
                    "name":"Vue"
                },
                {
                    "id":14,
                    "name":"ThinkPHP6"
                }
            ],
            "author":{
                "nikename":"兔子",
                "head_img":"http://inis.racns.com/img/userHead.gif",
                "email":"racns@qq.com",
                "address_url":"https://inis.cn",
                "description":"许一人以偏爱，尽此生之慷慨！"
            },
            "comments":7
        },
        "create_time":"2020-10-01 15:26:47",
        "update_time":"2020-12-15 12:04:46"
    }
}
```
</details>





### 【SQL】接口

> 通过该接口，你可以自己编写SQL语法获取更多自定义的数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/article/sql</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| limit | 否 | int | 5 | 数据数量 |
| page | 否 | int | 1 | 分页请求 |
| order | 否 | string | create_time desc | 排序方式 |
| where | 否 | string | 无 | 条件查询 |
| whereOr | 否 | string | 无 | 条件查询 |
| login-token | 否 | string | 无 | [登录密钥] 用于判断是否拥有显示隐藏文章的权限 |
| cache | 否 | bool | true | 是否获取缓存数据 |

<br>
<details>
<br>
<summary class="violet">字段说明</summary>

| 参数名称 | 语法 | 说明 |
| :---- | :---- | :---- |
| where | is_top=1;is_show=1; <span style="color:red">或</span> is_top=1 and is_show=1 | 用 ; 号或 and 隔开多个参数 |
| whereOr | title,like,%inis系统%;users_id,=,1; | 用 ; 号隔开多个查询条件，每个查询条件有三个参数，用 , 号隔开 |

</details>

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://api.inis.cc/api/article/sql',
  type:'GET',
  dataType:'JSON',
  data:{
    "limit":3,
    "where":"is_top=1;is_show=1;"
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
axios.get('http://api.inis.cc/api/article/sql',{
    params:{
      "order"  : "id acs",
      "whereOr": "title,like,%inis系统%",    // 可以实现模糊搜索
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
$url  = 'http://api.inis.cc/api/article/sql?where=is_top=1;is_show=1;';

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

> `expand` 内的数据为后端优化并处理过的数据，请优先使用 `expand` 内的数据

```json
{
    "code":200,
    "msg":"ok",
    "data":{
        "page":1,
        "count":2,
        "data":[
            {
                "id":66,
                "title":"新的测试",
                "description":"&lt;p&gt;&lt;br&gt;&lt;/p&gt;",
                "is_top":1,
                "is_show":1,
                "img_src":"https://picabstract-preview-ftn.weiyun.com/ftn_pic_abs_v3/6e111d4cfec8eb6ff4700a62cab984ec31420655d279b17fda9ef19fbb09005e93c393b40b4da61c765ca4b1f2e51df4?pictype=scale&amp;from=30013&amp;version=3.3.3.3&amp;uin=1211515059&amp;fname=74364959_p0_master1200.jpg&amp;size=750",
                "views":388,
                "font_count":0,
                "sort_id":"|14|",
                "tag_id":"|102|",
                "users_id":1,
                "expand":{
                    "author":{
                        "nickname":"兔子",
                        "head_img":"https://api.inis.cn/storage/users/uid-1/my-head.gif",
                        "email":"racns@qq.com",
                        "address_url":"https://inis.cn",
                        "description":"许一人以偏爱，尽此生之慷慨！"
                    },
                    "tag":[
                        {
                            "id":102,
                            "name":"标签5",
                            "color":"dark"
                        }
                    ],
                    "sort":[
                        {
                            "id":14,
                            "name":"ThinkPHP6"
                        }
                    ],
                    "comments":9
                },
                "opt":null,
                "delete_time":null,
                "create_time":"2020-11-21 15:16:28",
                "update_time":"2021-06-11 19:01:52"
            },
            {
                "id":1,
                "title":"inis系统",
                "description":"这是一个描述",
                "is_top":1,
                "is_show":1,
                "img_src":"https://picabstract-preview-ftn.weiyun.com/ftn_pic_abs_v3/db2fbee75ac661567e101c1e7a03d2782387b64a4d02a9b700da9e17015e4c3b0557ac15f2a072dbc94d9f44bb36c01c?pictype=scale&amp;from=30013&amp;version=3.3.3.3&amp;uin=1211515059&amp;fname=83041290_p0.jpg&amp;size=750",
                "views":4894,
                "font_count":5608,
                "sort_id":"|1|",
                "tag_id":"|89|102|",
                "users_id":1,
                "expand":{
                    "author":{
                        "nickname":"兔子",
                        "head_img":"https://api.inis.cn/storage/users/uid-1/my-head.gif",
                        "email":"racns@qq.com",
                        "address_url":"https://inis.cn",
                        "description":"许一人以偏爱，尽此生之慷慨！"
                    },
                    "tag":[
                        {
                            "id":89,
                            "name":"标签3",
                            "color":"success"
                        },
                        {
                            "id":102,
                            "name":"标签5",
                            "color":"dark"
                        }
                    ],
                    "sort":[
                        {
                            "id":1,
                            "name":"Vue"
                        }
                    ],
                    "comments":38
                },
                "opt":null,
                "delete_time":null,
                "create_time":"2020-10-01 15:26:47",
                "update_time":"2021-06-11 17:42:03"
            }
        ]
    }
}
```
</details>





### 【新增或修改】文章

> 通过该接口，你可以新增或者修改文章数据   
> 前提条件是必须登录且拥有权限的用户   
> 只允许账号为 管理员 且 未被禁用 的账号进行提交   
> 普通用户只允许修改属于自己的文章

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/article</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 是 | string | 无 | 登录密钥 | 用于判断是否拥有权限 |
| id | 否 | int | null | 文章ID | 存在则修改，反之新增 |
| title | 否 | string | 未命名文章 | 文章标题 | 无 |
| content | 否 | string | null | 文章内容 | 无 |
| description | 否 | string | null | 文章描述 | 无 |
| img_src | 否 | string | null | 文章封面 | 为空会分配一个随机图 |
| font_count | 否 | int | null | 文章字数 | 无 |
| sort_id | 否 | array | null | 分类ID | 无 |
| tag_id | 否 | string、array | null | 标签ID | 无 |
| tag_name | 否 | string、array | null | 新增标签名称 | 无 |
| is_show | 否 | int | 1 | 是否显示 | 无 |
| is_top | 否 | int | 0 | 是否置顶 | 无 |


<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 发表评论按钮
$('#btn-save').on('click', () => {
	
	let token       = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...';
    let title       = '欢迎使用，inis 博客系统';
    let content     = '当你看到这篇文章，就表示您的系统已经搭建成功！';
    let sort_id	    = '1,2';    // 用 , 分割多个ID
	let tag_id	    = '1,2,3';  // 用 , 分割多个ID
	let tag_name    = '新增标签1,新增标签2';    // 用 , 分割多个ID
	let is_top 	    = 1;

    let data = {'login-token':token, title, content, sort_id, tag_id, tag_name, is_top};

    $.ajax({
          url:'http://api.inis.cc/api/article',
          type:'POST',
          data:data,
          dataType:'JSON',
          success: (res) => {
              if(res.code === 200){
                console.log(res.data)
              }else{
                console.log(res)
              }
          }
      })
  })
</script>
```

#### ** axios **

```html
<!-- 导入axios -->
<script src="//unpkg.com/axios/dist/axios.min.js"></script>

<script>
axios.post('http://api.inis.cc/api/article',{},{
	headers: {
		'Content-Type':'application/x-www-form-urlencoded'
	},
	params: {
		"login-token"  : "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
		title          : '欢迎使用，inis 博客系统',
		content        : '当你看到这篇文章，就表示您的系统已经搭建成功！',
		sort_id        : '1,2',       // 用 , 分割多个ID
		tag_id         : '1,2,3',     // 用 , 分割多个ID
		tag_name       : '新增标签1,新增标签2',    // 用 , 分割多个ID
		is_top         : 1
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

// 设置POST数据
$data = [
    'login-token'  => "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
    title          => '欢迎使用，inis 博客系统',
	content        => '当你看到这篇文章，就表示您的系统已经搭建成功！',
	sort_id        => '1,2',     // 用 , 分割多个ID
	tag_id         => '1,2,3',     // 用 , 分割多个ID
	tag_name       => '新增标签1,新增标签2',    // 用 , 分割多个ID
	is_top         => 1
];

// 提交接口
$url = 'http://api.inis.cc/api/article';

$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, $url);

curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);

curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, FALSE);

curl_setopt($ch, CURLOPT_POST, 1);

// 设置 user-agent 
curl_setopt($ch,CURLOPT_USERAGENT,'Mozilla/5.0 (Linux; Android 10; Mi9 Pro 5G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.117 Mobile Safari/537.36');

curl_setopt($ch, CURLOPT_POSTFIELDS, $data);

$output = curl_exec($ch);

curl_close($ch);

// 输出数据
echo $output;
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "code": 200,
    "msg": "ok",
    "data": []
}
```
</details>






### 【删除】文章

> 通过该接口，你可以删除一条或者多条文章数据   
> 前提条件是必须登录且拥有权限的用户   
> 只允许账号为 未被禁用 的账号进行提交   
> 管理员可以删除任意文章，普通用户只允许删除属于自己的文章

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/article</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 是 | string | 无 | 无 | 登录密钥 | 用于判断是否拥有权限 |
| mode | 是 | string | null | remove | 模式 | 无 |
| id | 否 | string、array | null | 无 | 文章ID | 可以用 , 号隔开多个ID |
| destroy | 否 | bool | false | true、false | 是否真删除 | false的情况下、被删除的文章会存放在回收站 |


<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 发表评论按钮
$('#btn-save').on('click', () => {
	
	let token       = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...';
    let mode        = 'delete';
    let id          = '1,2,3';

    let data = {'login-token':token, mode, id};

    $.ajax({
          url:'http://api.inis.cc/api/article',
          type:'POST',
          data:data,
          dataType:'JSON',
          success: (res) => {
              if(res.code === 200){
                console.log(res.data)
              }else{
                console.log(res)
              }
          }
      })
  })
</script>
```

#### ** axios **

```html
<!-- 导入axios -->
<script src="//unpkg.com/axios/dist/axios.min.js"></script>

<script>
axios.post('http://api.inis.cc/api/article',{},{
	headers: {
		'Content-Type':'application/x-www-form-urlencoded'
	},
	params: {
		"login-token"  : "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
		mode           : 'delete',
		id             : '1,2,3',
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

// 设置POST数据
$data = [
    'login-token'  => "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
    mode           => 'delete',
	id             => '1,2,3',
];

// 提交接口
$url = 'http://api.inis.cc/api/article';

$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, $url);

curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);

curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, FALSE);

curl_setopt($ch, CURLOPT_POST, 1);

// 设置 user-agent 
curl_setopt($ch,CURLOPT_USERAGENT,'Mozilla/5.0 (Linux; Android 10; Mi9 Pro 5G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.117 Mobile Safari/537.36');

curl_setopt($ch, CURLOPT_POSTFIELDS, $data);

$output = curl_exec($ch);

curl_close($ch);

// 输出数据
echo $output;
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "code": 200,
    "msg": "ok",
    "data": []
}
```
</details>