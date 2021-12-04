## 获取【全部】评论数据

> 通过该接口，你可以获取到全部的评论数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/comments</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| limit | 否 | int | 5 | 数据数量 |
| page | 否 | int | 1 | 分页请求 |
| order | 否 | string | create_time desc | 排序方式 |
| type | 否 | string | null | 根据字段type指定获取对应的全部评论 |
| cache | 否 | bool | true | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/comments',
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
axios.get('http://test.inis.cn/api/comments').then((res) => {
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
$url  = 'http://test.inis.cn/api/comments';

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
        "page":7,
        "count":32,
        "data":[
            {
                "id":69,
                "article_id":1,
                "users_id":null,
                "pid":0,
                "content":"评论测试",
                "nickname":"兔子",
                "email":"racns@qq.com",
                "url":null,
                "ip":"171.108.238.179",
                "status":1,
                "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.85 Safari/537.36",
                "is_show":1,
                "expand":{
                    "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=1211515059&amp;s=640",
                    "url":"javascript:;",
                    "article":"inis系统",
                    "agent":{
                        "browser":{
                            "browser":"Chrome",
                            "browser_ver":"90.0.4430.85"
                        },
                        "os":{
                            "os":"Windows(x64)",
                            "os_ver":"10",
                            "equipment":"PC"
                        },
                        "mobile":{
                            "mobile_brand":"其他",
                            "mobile_ver":""
                        }
                    }
                },
                "opt":null,
                "create_time":"2021-05-11 20:53:30",
                "update_time":"2021-05-11 20:53:30"
            },
            {... ...},
            {... ...},
            {... ...},
            {... ...},
        ]
    }
}
```
</details>




## 获取【单条】评论数据

> 通过该接口，你可以获取到单条的评论数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/comments</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| id | 否 | int | null | 评论ID |
| tree | 否 | bool | true | 评论无极限（抖音或QQ空间评论类型） |
| cache | 否 | bool | true | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/comments',
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
axios.get('http://test.inis.cn/api/comments',{
    params:{ "id":1 }
  }).then((res) => {
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
$url  = 'http://test.inis.cn/api/comments?id=1';

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
        "id":76,
        "pid":0,
        "content":"这将会是你见过最美的网站！",
        "nickname":"测试",
        "email":"97783391@qq.com",
        "url":"",
        "ip":"171.108.238.63",
        "type":"msg_wall",
        "status":1,
        "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36",
        "is_show":1,
        "users_id":2,
        "article_id":null,
        "opt":{
            "bg":"bg-primary",
            "great":1
        },
        "expand":{
            "head_img":"https://q.qlogo.cn/g?b=qq&amp;nk=97783391&amp;s=640",
            "url":"https://inis.cn",
            "agent":{
                "browser":{
                    "browser":"Chrome",
                    "browser_ver":"91.0.4472.77"
                },
                "os":{
                    "os":"Windows(x64)",
                    "os_ver":"10",
                    "equipment":"PC"
                },
                "mobile":{
                    "mobile_brand":"其他",
                    "mobile_ver":""
                }
            }
        },
        "create_time":"2021-06-24 16:20:35",
        "update_time":"2021-06-24 16:20:35",
        "son":[
            {
                "id":73,
                "pid":76,
                "content":"测试邮箱评论通知 - 第二次测试",
                "nickname":"test",
                "email":"inis.cn@qq.com",
                "url":"",
                "ip":"171.108.238.78",
                "type":"article",
                "status":1,
                "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36",
                "is_show":1,
                "users_id":null,
                "article_id":1,
                "opt":null,
                "expand":{
                    "head_img":"https://api.inis.cn/storage/users/anime/9.jpg",
                    "url":null,
                    "agent":{
                        "browser":{
                            "browser":"Chrome",
                            "browser_ver":"91.0.4472.77"
                        },
                        "os":{
                            "os":"Windows(x64)",
                            "os_ver":"10",
                            "equipment":"PC"
                        },
                        "mobile":{
                            "mobile_brand":"其他",
                            "mobile_ver":""
                        }
                    },
                    "article":{
                        "id":1,
                        "title":"inis系统"
                    }
                },
                "create_time":"2021-06-10 16:22:44",
                "update_time":"2021-06-22 16:58:58",
                "son":[
                    {
                        "id":71,
                        "pid":73,
                        "content":"谢谢，谢谢",
                        "nickname":"兔子",
                        "email":"racns@qq.com",
                        "url":null,
                        "ip":"171.108.238.189",
                        "type":"article",
                        "status":1,
                        "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36",
                        "is_show":1,
                        "users_id":null,
                        "article_id":66,
                        "opt":null,
                        "expand":{
                            "head_img":"https://api.inis.cn/storage/users/anime/1.jpg",
                            "url":null,
                            "agent":{
                                "browser":{
                                    "browser":"Chrome",
                                    "browser_ver":"91.0.4472.77"
                                },
                                "os":{
                                    "os":"Windows(x64)",
                                    "os_ver":"10",
                                    "equipment":"PC"
                                },
                                "mobile":{
                                    "mobile_brand":"其他",
                                    "mobile_ver":""
                                }
                            },
                            "article":{
                                "id":66,
                                "title":"新的测试"
                            }
                        },
                        "create_time":"2021-06-04 17:23:10",
                        "update_time":"2021-06-04 17:23:10",
                        "son":[
                            {
                                "id":69,
                                "pid":71,
                                "content":"评论测试",
                                "nickname":"兔子",
                                "email":"racns@qq.com",
                                "url":"",
                                "ip":"171.108.238.179",
                                "type":"article",
                                "status":1,
                                "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.85 Safari/537.36",
                                "is_show":1,
                                "users_id":null,
                                "article_id":1,
                                "opt":null,
                                "expand":{
                                    "head_img":"https://api.inis.cn/storage/users/anime/7.jpg",
                                    "url":null,
                                    "agent":{
                                        "browser":{
                                            "browser":"Chrome",
                                            "browser_ver":"90.0.4430.85"
                                        },
                                        "os":{
                                            "os":"Windows(x64)",
                                            "os_ver":"10",
                                            "equipment":"PC"
                                        },
                                        "mobile":{
                                            "mobile_brand":"其他",
                                            "mobile_ver":""
                                        }
                                    },
                                    "article":{
                                        "id":1,
                                        "title":"inis系统"
                                    }
                                },
                                "create_time":"2021-05-11 20:53:30",
                                "update_time":"2021-05-26 21:32:02",
                                "son":[]
                            }
                        ]
                    }
                ]
            },
            {
                "id":72,
                "pid":76,
                "content":"评论测试",
                "nickname":"兔子",
                "email":"racns@qq.com",
                "url":"inis.cn",
                "ip":"171.108.238.78",
                "type":"article",
                "status":1,
                "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36",
                "is_show":1,
                "users_id":null,
                "article_id":1,
                "opt":null,
                "expand":{
                    "head_img":"https://api.inis.cn/storage/users/anime/2.jpg",
                    "url":"inis.cn",
                    "agent":{
                        "browser":{
                            "browser":"Chrome",
                            "browser_ver":"91.0.4472.77"
                        },
                        "os":{
                            "os":"Windows(x64)",
                            "os_ver":"10",
                            "equipment":"PC"
                        },
                        "mobile":{
                            "mobile_brand":"其他",
                            "mobile_ver":""
                        }
                    },
                    "article":{
                        "id":1,
                        "title":"inis系统"
                    }
                },
                "create_time":"2021-06-10 16:11:32",
                "update_time":"2021-06-10 16:11:32",
                "son":[

                ]
            }
        ]
    }
}
```
</details>




## 获取【文章下】的评论数据

> 通过该接口，你可以获取到全部的评论数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/comments</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| article_id | 否 | int | 无 | 文章ID |
| tree | 否 | bool | true | 评论无极限（抖音或QQ空间评论类型） |
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
  url:'http://test.inis.cn/api/comments',
  type:'GET',
  dataType:'JSON',
  data: {"article_id":1},
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
axios.get('http://test.inis.cn/api/comments',{
    params:{ "article_id":1 }
  }).then((res) => {
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
$url  = 'http://test.inis.cn/api/comments?article_id=1';

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
        "page":3,
        "count":11,
        "data":[
            {
                "id":69,
                "article_id":1,
                "users_id":null,
                "pid":0,
                "content":"评论测试",
                "nickname":"兔子",
                "email":"racns@qq.com",
                "url":null,
                "ip":"171.108.238.179",
                "status":1,
                "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.85 Safari/537.36",
                "is_show":1,
                "expand":{
                    "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=1211515059&amp;s=640",
                    "url":"javascript:;",
                    "article":"inis系统",
                    "agent":{
                        "browser":{
                            "browser":"Chrome",
                            "browser_ver":"90.0.4430.85"
                        },
                        "os":{
                            "os":"Windows(x64)",
                            "os_ver":"10",
                            "equipment":"PC"
                        },
                        "mobile":{
                            "mobile_brand":"其他",
                            "mobile_ver":""
                        }
                    }
                },
                "opt":null,
                "create_time":"2021-05-11 20:53:30",
                "update_time":"2021-05-11 20:53:30",
                "son":[
                    {
                        "id":68,
                        "article_id":1,
                        "users_id":null,
                        "pid":69,
                        "content":"评论测试",
                        "nickname":"兔子",
                        "email":"racns@qq.com",
                        "url":null,
                        "ip":"171.108.238.179",
                        "status":1,
                        "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.85 Safari/537.36",
                        "is_show":1,
                        "expand":{
                            "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=1211515059&amp;s=640",
                            "url":"javascript:;",
                            "article":"inis系统",
                            "agent":{
                                "browser":{
                                    "browser":"Chrome",
                                    "browser_ver":"90.0.4430.85"
                                },
                                "os":{
                                    "os":"Windows(x64)",
                                    "os_ver":"10",
                                    "equipment":"PC"
                                },
                                "mobile":{
                                    "mobile_brand":"其他",
                                    "mobile_ver":""
                                }
                            }
                        },
                        "opt":null,
                        "create_time":"2021-05-11 20:44:37",
                        "update_time":"2021-05-11 20:44:37",
                        "son":[
                            {
                                "id":67,
                                "article_id":1,
                                "users_id":null,
                                "pid":68,
                                "content":"期待",
                                "nickname":"anlan",
                                "email":"1223414839@qq.com",
                                "url":"myienote.com",
                                "ip":"218.58.59.72",
                                "status":1,
                                "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.85 Safari/537.36 Edg/90.0.818.46",
                                "is_show":1,
                                "expand":{
                                    "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=1223414839&amp;s=640",
                                    "url":"//myienote.com",
                                    "article":"inis系统",
                                    "agent":{
                                        "browser":{
                                            "browser":"Chrome",
                                            "browser_ver":"90.0.4430.85"
                                        },
                                        "os":{
                                            "os":"Windows(x64)",
                                            "os_ver":"10",
                                            "equipment":"PC"
                                        },
                                        "mobile":{
                                            "mobile_brand":"其他",
                                            "mobile_ver":""
                                        }
                                    }
                                },
                                "opt":null,
                                "create_time":"2021-04-25 17:01:34",
                                "update_time":"2021-04-25 20:39:30",
                                "son":[
                                    {
                                        "id":66,
                                        "article_id":1,
                                        "users_id":null,
                                        "pid":67,
                                        "content":"大佬带带我",
                                        "nickname":"旧云",
                                        "email":"1393756859@qq.com",
                                        "url":null,
                                        "ip":"171.43.237.192",
                                        "status":1,
                                        "agent":"Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/70.0.3538.25 Safari/537.36 Core/1.70.3861.400 QQBrowser/10.7.4313.400",
                                        "is_show":1,
                                        "expand":{
                                            "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=1393756859&amp;s=640",
                                            "url":"javascript:;",
                                            "article":"inis系统",
                                            "agent":{
                                                "browser":{
                                                    "browser":"Chrome",
                                                    "browser_ver":"70.0.3538.25"
                                                },
                                                "os":{
                                                    "os":"Windows",
                                                    "os_ver":"10",
                                                    "equipment":"PC"
                                                },
                                                "mobile":{
                                                    "mobile_brand":"其他",
                                                    "mobile_ver":""
                                                }
                                            }
                                        },
                                        "opt":null,
                                        "create_time":"2021-04-19 11:25:20",
                                        "update_time":"2021-04-19 11:25:20",
                                        "son":[
                                            {
                                                "id":65,
                                                "article_id":1,
                                                "users_id":null,
                                                "pid":66,
                                                "content":"123",
                                                "nickname":"123",
                                                "email":"123123@123.com",
                                                "url":"123",
                                                "ip":"58.246.252.121",
                                                "status":1,
                                                "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.198 Safari/537.36",
                                                "is_show":1,
                                                "expand":{
                                                    "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=1211515059&amp;s=640",
                                                    "url":"//123",
                                                    "article":"inis系统",
                                                    "agent":{
                                                        "browser":{
                                                            "browser":"Chrome",
                                                            "browser_ver":"86.0.4240.198"
                                                        },
                                                        "os":{
                                                            "os":"Windows(x64)",
                                                            "os_ver":"10",
                                                            "equipment":"PC"
                                                        },
                                                        "mobile":{
                                                            "mobile_brand":"其他",
                                                            "mobile_ver":""
                                                        }
                                                    }
                                                },
                                                "opt":null,
                                                "create_time":"2021-04-19 07:15:48",
                                                "update_time":"2021-04-19 07:15:48",
                                                "son":[

                                                ]
                                            }
                                        ]
                                    },
                                    {
                                        "id":60,
                                        "article_id":1,
                                        "users_id":null,
                                        "pid":67,
                                        "content":"异世相遇，尽享美味",
                                        "nickname":"谦夏",
                                        "email":"1589472813@qq.com",
                                        "url":null,
                                        "ip":"117.140.124.103",
                                        "status":1,
                                        "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.72 Safari/537.36",
                                        "is_show":1,
                                        "expand":{
                                            "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=1589472813&amp;s=640",
                                            "url":"javascript:;",
                                            "article":"inis系统",
                                            "agent":{
                                                "browser":{
                                                    "browser":"Chrome",
                                                    "browser_ver":"89.0.4389.72"
                                                },
                                                "os":{
                                                    "os":"Windows(x64)",
                                                    "os_ver":"10",
                                                    "equipment":"PC"
                                                },
                                                "mobile":{
                                                    "mobile_brand":"其他",
                                                    "mobile_ver":""
                                                }
                                            }
                                        },
                                        "opt":null,
                                        "create_time":"2021-03-22 17:28:00",
                                        "update_time":"2021-03-22 17:28:00",
                                        "son":[

                                        ]
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "id":64,
                        "article_id":1,
                        "users_id":null,
                        "pid":69,
                        "content":"异世相遇，尽享美味",
                        "nickname":"秋谦",
                        "email":"2383788433@qq.com",
                        "url":null,
                        "ip":"117.183.120.233",
                        "status":1,
                        "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.72 Safari/537.36",
                        "is_show":1,
                        "expand":{
                            "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=2383788433&amp;s=640",
                            "url":"javascript:;",
                            "article":"inis系统",
                            "agent":{
                                "browser":{
                                    "browser":"Chrome",
                                    "browser_ver":"89.0.4389.72"
                                },
                                "os":{
                                    "os":"Windows(x64)",
                                    "os_ver":"10",
                                    "equipment":"PC"
                                },
                                "mobile":{
                                    "mobile_brand":"其他",
                                    "mobile_ver":""
                                }
                            }
                        },
                        "opt":null,
                        "create_time":"2021-03-23 18:07:41",
                        "update_time":"2021-03-23 18:07:41",
                        "son":[
                            {
                                "id":45,
                                "article_id":1,
                                "users_id":null,
                                "pid":64,
                                "content":"更多美味尽在＿＿＿＿＿",
                                "nickname":"谦夏",
                                "email":"1589472813@qq.com",
                                "url":"",
                                "ip":"117.140.125.30",
                                "status":1,
                                "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.72 Safari/537.36",
                                "is_show":1,
                                "expand":{
                                    "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=1589472813&amp;s=640",
                                    "url":"javascript:;",
                                    "article":"inis系统",
                                    "agent":{
                                        "browser":{
                                            "browser":"Chrome",
                                            "browser_ver":"89.0.4389.72"
                                        },
                                        "os":{
                                            "os":"Windows(x64)",
                                            "os_ver":"10",
                                            "equipment":"PC"
                                        },
                                        "mobile":{
                                            "mobile_brand":"其他",
                                            "mobile_ver":""
                                        }
                                    }
                                },
                                "opt":null,
                                "create_time":"2021-03-09 16:47:37",
                                "update_time":"2021-03-18 01:30:48",
                                "son":[

                                ]
                            }
                        ]
                    }
                ]
            },
            {... ...},
            {... ...},
            {... ...},
            {... ...},
        ]
    }
}
```
</details>




## 获取【聚合】评论数据

> 通过该接口，你可以获取到根据评论者邮箱聚合的评论   
> mode=group：可用于统计评论者在本站的评论次数或用于实现总评论排行榜   
> mode=type ：可用于实现类似于默认主题中的留言墙功能

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/comments</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| mode | 否 | string | 无 | group、type | 模式 |
| limit | 否 | int | 20 | 无 | 数据数量 |
| page | 否 | int | 1 | 无 | 分页请求 |
| order | 否 | string | desc | desc、acs | 排序方式 |
| type | 否 | string | null | 自定义参数 | 数据库评论表中的type字段 |
| tree | 否 | bool | true | 评论无极限（抖音或QQ空间评论类型） |
| cache | 否 | bool | true | 无 | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/comments',
  type:'GET',
  dataType:'JSON',
  data: {"mode":"group"},
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
axios.get('http://test.inis.cn/api/comments',{
    params:{ "mode":"group" }
  }).then((res) => {
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
$url  = 'http://test.inis.cn/api/comments?mode=group';

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
        "page":1,
        "count":16,
        "data":[
            {
                "id":28,
                "email":"1589472813@qq.com",
                "nickname":"谦夏",
                "url":null,
                "expand":{
                    "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=1589472813&amp;s=640",
                    "url":"javascript:;",
                    "article":"inis系统",
                    "agent":{
                        "browser":{
                            "browser":"Chrome",
                            "browser_ver":"88.0.4324.190"
                        },
                        "os":{
                            "os":"Windows(x64)",
                            "os_ver":"10",
                            "equipment":"PC"
                        },
                        "mobile":{
                            "mobile_brand":"其他",
                            "mobile_ver":""
                        }
                    }
                },
                "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.190 Safari/537.36",
                "article_id":1,
                "count":16   // 在本站评论次数
            },
            {
                "id":26,
                "email":"2383788433@qq.com",
                "nickname":"秋谦",
                "url":null,
                "expand":{
                    "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=2383788433&amp;s=640",
                    "url":"javascript:;",
                    "article":"inis系统",
                    "agent":{
                        "browser":{
                            "browser":"Chrome",
                            "browser_ver":"88.0.4324.190"
                        },
                        "os":{
                            "os":"Windows(x64)",
                            "os_ver":"10",
                            "equipment":"PC"
                        },
                        "mobile":{
                            "mobile_brand":"其他",
                            "mobile_ver":""
                        }
                    }
                },
                "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.190 Safari/537.36",
                "article_id":1,
                "count":10   // 在本站评论次数
            },
            {
                "id":24,
                "email":"racns@qq.com",
                "nickname":"用户昵称",
                "url":"inis.cn",
                "expand":{
                    "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=1211515059&amp;s=640",
                    "url":"//http://inis.cn",
                    "article":"inis系统",
                    "agent":{
                        "browser":{
                            "browser":"Chrome",
                            "browser_ver":"88.0.4324.190"
                        },
                        "os":{
                            "os":"Windows(x64)",
                            "os_ver":"10",
                            "equipment":"PC"
                        },
                        "mobile":{
                            "mobile_brand":"其他",
                            "mobile_ver":""
                        }
                    }
                },
                "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.190 Safari/537.36",
                "article_id":1,
                "count":8   // 在本站评论次数
            }
        ]
    }
}
```
</details>




## 【新增】评论

> 通过该接口，你可以获取到全部的评论数据

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/comments</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 否 | string | 无 | 登录密钥 | 用于判断是否登录后提交的评论，优先级最高（可以在参数或headers中提交，推荐header提交） |
| pid | 否 | int | 0 | 评论的父级ID | 用于判断是否为回复 |
| content | 否 | string | 无 | 评论的内容 | 无 |
| nickname | 否 | string | 无 | 用户昵称 | 如果提交了login-token，该字段会自动获取 |
| email | 否 | string | 无 | 邮箱 | 如果提交了login-token，该字段会自动获取 |
| url | 否 | string | 无 | 用户网址 | 如果提交了login-token，该字段会自动获取 |
| ip | 否 | string | null | 客户端IP | 不提交系统会自动获取 |
| agent | 否 | string | null | UA信息 | 不提交系统会自动获取 |
| type | 否 | string | article | 属性 | 用于区别不同场景的评论 |
| users_id | 否 | string | null | 用户ID | 如果提交了login-token，该字段会自动获取 |
| article_id | 否 | string | null | 文章ID | 无 |
| opt | 否 | object | 无 | JSON字段，必须为对象结构 | 用于不同场景的拓展字段 |

<br>
<details>
<summary class="violet">接口规范<span class="text-danger ml-1">[ 推荐 ]</span></summary>

!> 为了方便`主题间切换`，推荐主题开发者针对以下字段参数进行规范化提交

| 字段名称 | 值 | 说明 |
| :---- | :---- | :---- |
| type | article | 文章评论 |
| type | links | 友链库评论 |
| type | msg_wall | 留言墙评论 |
| type | about | 关于我页面评论 |
| type | moving | 时光机评论 |

</details>

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 发表评论按钮
$('#btn-save').on('click', () => {
	
    let article_id  = 1;
    let content     = '评论内容';
    let nickname	= '用户昵称';
	let email	   = 'racns@qq.com';
	let pid 		= 15;
	let url 		= 'http://inis.cn';

    let data = {article_id,content,nickname,email,pid,url};

    $.ajax({
          url:'http://test.inis.cn/api/comments',
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
axios.post('http://test.inis.cn/api/comments',{},{
	headers: {
		'Content-Type':'application/x-www-form-urlencoded'
	},
	params: {
		"login-token"  : "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
		article_id  : 1,
		pid         : 15,
		content     : '评论内容',
		opt         : {"test":"使用演示","test1":"可以提交多个字段"}
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
    'article_id' => 1,
    'content'    => '评论内容',
    'nickname'   => '用户昵称',
    'email'      => 'racns@qq.com',
    'pid'        => 15,
    'url'        => 'http://inis.cn'
];

// 提交评论接口
$url = 'http://test.inis.cn/api/comments';

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
    "code":200,
    "msg":"评论成功！",
    "data":"15"
}
```
</details>





## 【SQL】接口

> 通过该接口，你可以自己编写SQL语法获取更多自定义的数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/comments/sql</p>

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
| where | nickname=兔子;article_id=1; <span style="color:red">或</span> nickname=兔子 and article_id=1 | 用 ; 号或 and 隔开多个参数 |
| whereOr | nickname,like,%兔子%;article_id,=,1; | 用 ; 号隔开多个查询条件，每个查询条件有三个参数，用 , 号隔开 |

</details>

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/comments/sql',
  type:'GET',
  dataType:'JSON',
  data:{
    "where":"nickname=兔子;article_id=1;"
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
axios.get('http://test.inis.cn/api/comments/sql',{
    params:{
      "order"  : "id acs",
      "whereOr": "nickname,like,%兔子%",    // 可以实现模糊搜索
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
$url  = 'http://test.inis.cn/api/comments/sql?where=article_id=1';

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
        "page":2,
        "count":10,
        "data":[
            {
                "id":72,
                "article_id":1,
                "users_id":null,
                "pid":48,
                "content":"评论测试",
                "nickname":"兔子",
                "email":"racns@qq.com",
                "url":"inis.cn",
                "ip":"171.108.238.78",
                "status":1,
                "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.77 Safari/537.36",
                "is_show":1,
                "expand":{
                    "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=1211515059&amp;s=640",
                    "url":"//inis.cn",
                    "article":"inis系统",
                    "agent":{
                        "browser":{
                            "browser":"Chrome",
                            "browser_ver":"91.0.4472.77"
                        },
                        "os":{
                            "os":"Windows(x64)",
                            "os_ver":"10",
                            "equipment":"PC"
                        },
                        "mobile":{
                            "mobile_brand":"其他",
                            "mobile_ver":""
                        }
                    }
                },
                "opt":null,
                "create_time":"2021-06-10 16:11:32",
                "update_time":"2021-06-10 16:11:32"
            },
            {
                "id":69,
                "article_id":1,
                "users_id":null,
                "pid":0,
                "content":"评论测试",
                "nickname":"兔子",
                "email":"racns@qq.com",
                "url":"",
                "ip":"171.108.238.179",
                "status":1,
                "agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.85 Safari/537.36",
                "is_show":1,
                "expand":{
                    "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=1211515059&amp;s=640",
                    "url":"javascript:;",
                    "article":"inis系统",
                    "agent":{
                        "browser":{
                            "browser":"Chrome",
                            "browser_ver":"90.0.4430.85"
                        },
                        "os":{
                            "os":"Windows(x64)",
                            "os_ver":"10",
                            "equipment":"PC"
                        },
                        "mobile":{
                            "mobile_brand":"其他",
                            "mobile_ver":""
                        }
                    }
                },
                "opt":null,
                "create_time":"2021-05-11 20:53:30",
                "update_time":"2021-05-26 21:32:02"
            }
        ]
    }
}
```
</details>





## 【修改】评论

> 通过该接口，你可以新增或者修改配置数据   
> 前提条件是必须登录且拥有权限的用户   
> 只允许账号为 管理员 且 未被禁用 的账号进行提交   

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/comments</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 是 | string | 无 | null | 登录密钥 | 用于判断是否拥有权限（可以在参数或headers中提交，推荐header提交） |
| mode | 是 | string | null | edit | 模式 | edit为修改 |
| id | 是 | int | null | null | 评论ID | 无 |
| content | 否 | string | null | null | 评论内容 | 无 |
| nickname | 否 | object | null | null | 用户昵称 | 无 |
| email | 否 | bool | false | null | 用户邮箱 | 无 |
| url | 否 | bool | false | null | 用户网址 | 无 |
| opt | 否 | object | 无 | null | JSON字段，必须为对象结构 | 用于不同场景的拓展字段 |


<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 提交
$('#btn-save').on('click', () => {
	
	let token       = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...';
	let mode        = 'edit';
    let id          = 1;
    let content     = '这是一个评论测试的内容！';

    let data = {'login-token':token, id, mode, content};

    $.ajax({
          url:'http://test.inis.cn/api/comments',
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
axios.post('http://test.inis.cn/api/comments',{},{
	headers: {
		'Content-Type':'application/x-www-form-urlencoded'
	},
	params: {
		"login-token"  : "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
		mode           : 'edit',
		id             : 1,
		content        : '这是一个评论测试的内容！',
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
    mode           => 'edit',
    id             => 1,
	content        => '这是一个评论测试的内容！',
];

// 提交接口
$url = 'http://test.inis.cn/api/comments';

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





## 【删除】评论

> 通过该接口，你可以删除一条或者多条文章数据   
> 前提条件是必须登录且拥有权限的用户   
> 只允许账号为 管理员 且 未被禁用 的账号进行提交   

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/comments</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 是 | string | 无 | 无 | 登录密钥 | 用于判断是否拥有权限（可以在参数或headers中提交，推荐header提交） |
| mode | 是 | string | null | remove | 模式 | 无 |
| id | 否 | int、string | null | 无 | 评论ID | 支持批量，用 , 号隔开多个ID |


<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 发表评论按钮
$('#btn-save').on('click', () => {
	
	let token       = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...';
    let mode        = 'remove';
    let id          = '1';

    let data = {'login-token':token, mode, id};

    $.ajax({
          url:'http://test.inis.cn/api/comments',
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
axios.post('http://test.inis.cn/api/comments',{},{
	headers: {
		'Content-Type':'application/x-www-form-urlencoded'
	},
	params: {
		"login-token"  : "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
		mode           : 'remove',
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
    mode           => 'remove',
	id             => '1',
];

// 提交接口
$url = 'http://test.inis.cn/api/comments';

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