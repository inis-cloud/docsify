## 【代理】接口

> 通过这个接口，你可以发起代理请求，以后端作为代理，请求目标URL数据   
> 如：小程序平台有合法域名这一说法，无法请求合法域名以外的API数据，因此你只需要借用这个接口实现向第三方API发起请求

!> 应用场景：`小程序` `代理请求`

<details>
<summary class="violet">注意事项</summary>

> 由于系统占用了name参数，提交name参数会不生效，因此name参数这里用p_name代替    
> 例如你的API请求中用到了name参数，原先的请求应该是这样 api?name=value ，现在你需要用 api?p_name=value 表示，给name加个前缀p_表示，效果一致

</details>

### 代理 GET 请求

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/proxy</p>

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/proxy/get</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| p_url | 是 | string | null | 代理请求的URL地址 | 无 |
| p_headers | 否 | array | null | 代理请求的header头部信息 | 无 |
| * | 否 | string | null | 自定义参数 | 键值对形式 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/proxy',
  type:'GET',
  dataType:'JSON',
  data:{
    p_url: "https://v1.hitokoto.cn",
    p_headers: ["Content-Type:application/json;charset=utf-8"],
    encode:'json',      // 自定义参数
  },
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
axios.get('http://test.inis.cn/api/proxy/get',{
    params:{
        p_url: "https://v1.hitokoto.cn",
        p_headers: ["Content-Type:application/json;charset=utf-8"],
        encode:'json',      // 自定义参数
    }
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
$url  = 'http://test.inis.cn/api/proxy?p_url=https://v1.hitokoto.cn&encode=json';

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
    "id":1349,
    "uuid":"7305461e-1962-4186-ad31-6730ded3e74a",
    "hitokoto":"末将于禁，愿为曹家世代赴汤蹈火。",
    "type":"b",
    "from":"镇魂街",
    "from_who":null,
    "creator":"死木芽",
    "creator_uid":1033,
    "reviewer":0,
    "commit_from":"web",
    "created_at":"1515592778",
    "length":16
}
```
</details>





### 代理 PUT 请求

<p class="api-request put" data-lang="API"><em></em>http://[域名]/api/proxy</p>

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/proxy/put</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| p_url | 是 | string | null | 代理请求的URL地址 | 无 |
| p_headers | 否 | array | null | 代理请求的header头部信息 | 无 |
| * | 否 | string | null | 自定义参数 | 键值对形式 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/proxy',
  type:'PUT',
  dataType:'JSON',
  data:{
    p_url: "https://v1.hitokoto.cn",
    p_headers: ["Content-Type:application/json;charset=utf-8"],
    encode:'json',      // 自定义参数
  },
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
axios.put('http://test.inis.cn/api/proxy',{
    p_url: "https://v1.hitokoto.cn",
    p_headers: ["Content-Type:application/json;charset=utf-8"],
    encode:'json',      // 自定义参数
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
$url  = 'http://test.inis.cn/api/proxy';

// 参数
$params = json_encode([
    "p_url"     =>  "https://v1.hitokoto.cn",
    "p_headers" =>  ["Content-Type:application/json;charset=utf-8"],
    "encode"    =>  "json",      // 自定义参数
]);

$curl   = curl_init();

// 设置请求的URL
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_HTTPHEADER, ["Content-type:application/json;charset='utf-8'"]);
// 设为TRUE把curl_exec()结果转化为字串，而不是直接输出 
curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
// 设置请求方式
curl_setopt($curl, CURLOPT_CUSTOMREQUEST, "PUT");
// 设置提交的字符串
curl_setopt($curl, CURLOPT_POSTFIELDS, $params);

$result = curl_exec($curl);
curl_close($curl);
$result = json_decode($result,true);

// 输出数据
var_dump($result);
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "id":1349,
    "uuid":"7305461e-1962-4186-ad31-6730ded3e74a",
    "hitokoto":"末将于禁，愿为曹家世代赴汤蹈火。",
    "type":"b",
    "from":"镇魂街",
    "from_who":null,
    "creator":"死木芽",
    "creator_uid":1033,
    "reviewer":0,
    "commit_from":"web",
    "created_at":"1515592778",
    "length":16
}
```
</details>





### 代理 POST 请求

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/proxy</p>

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/proxy/post</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| p_url | 是 | string | null | 代理请求的URL地址 | 无 |
| p_headers | 否 | array | null | 代理请求的header头部信息 | 无 |
| * | 否 | string | null | 自定义参数 | 键值对形式 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/proxy',
  type:'POST',
  dataType:'JSON',
  data:{
    p_url: "https://v1.hitokoto.cn",
    p_headers: ["Content-Type:application/json;charset=utf-8"],
    encode:'json',      // 自定义参数
  },
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
axios.post('http://test.inis.cn/api/proxy',{},{
    params:{
        p_url: "https://v1.hitokoto.cn",
        p_headers: ["Content-Type:application/json;charset=utf-8"],
        encode:'json',      // 自定义参数
    }
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
$url  = 'http://test.inis.cn/api/proxy';

// 参数
$params = json_encode([
    "p_url"     =>  "https://v1.hitokoto.cn",
    "p_headers" =>  ["Content-Type:application/json;charset=utf-8"],
    "encode"    =>  "json",      // 自定义参数
]);

$curl   = curl_init();

curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, FALSE);
curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, FALSE);
curl_setopt($curl, CURLOPT_POST, 1);    // POST请求
curl_setopt($curl, CURLOPT_POSTFIELDS, $params);
curl_setopt($curl, CURLOPT_HTTPHEADER, ["Content-type:application/json;charset='utf-8'","Accept:application/json"]);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);

$result = curl_exec($curl);
curl_close($curl);
$result = json_decode($result,true);

// 输出数据
var_dump($result);
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "id":1349,
    "uuid":"7305461e-1962-4186-ad31-6730ded3e74a",
    "hitokoto":"末将于禁，愿为曹家世代赴汤蹈火。",
    "type":"b",
    "from":"镇魂街",
    "from_who":null,
    "creator":"死木芽",
    "creator_uid":1033,
    "reviewer":0,
    "commit_from":"web",
    "created_at":"1515592778",
    "length":16
}
```
</details>





### 代理 PATCH 请求

<p class="api-request patch" data-lang="API"><em></em>http://[域名]/api/proxy</p>

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/proxy/patch</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| p_url | 是 | string | null | 代理请求的URL地址 | 无 |
| p_headers | 否 | array | null | 代理请求的header头部信息 | 无 |
| * | 否 | string | null | 自定义参数 | 键值对形式 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/proxy',
  type:'PATCH',
  dataType:'JSON',
  data:{
    p_url: "https://v1.hitokoto.cn",
    p_headers: ["Content-Type:application/json;charset=utf-8"],
    encode:'json',      // 自定义参数
  },
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
axios.patch('http://test.inis.cn/api/proxy',{
    p_url: "https://v1.hitokoto.cn",
    p_headers: ["Content-Type:application/json;charset=utf-8"],
    encode:'json',      // 自定义参数
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
$url  = 'http://test.inis.cn/api/proxy';

// 参数
$params = json_encode([
    "p_url"     =>  "https://v1.hitokoto.cn",
    "p_headers" =>  ["Content-Type:application/json;charset=utf-8"],
    "encode"    =>  "json",      // 自定义参数
]);

$curl   = curl_init();

curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_HTTPHEADER, ["Content-type:application/json;charset='utf-8'","Accept:application/json"]);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($curl, CURLOPT_CUSTOMREQUEST, "PATCH");     // PATCH请求
curl_setopt($curl, CURLOPT_POSTFIELDS, $params);

$result = curl_exec($curl);
curl_close($curl);
$result = json_decode($result,true);

// 输出数据
var_dump($result);
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "id":1349,
    "uuid":"7305461e-1962-4186-ad31-6730ded3e74a",
    "hitokoto":"末将于禁，愿为曹家世代赴汤蹈火。",
    "type":"b",
    "from":"镇魂街",
    "from_who":null,
    "creator":"死木芽",
    "creator_uid":1033,
    "reviewer":0,
    "commit_from":"web",
    "created_at":"1515592778",
    "length":16
}
```
</details>





### 代理 DELETE 请求

<p class="api-request del" data-lang="API"><em></em>http://[域名]/api/proxy</p>

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/proxy/delete</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| p_url | 是 | string | null | 代理请求的URL地址 | 无 |
| p_headers | 否 | array | null | 代理请求的header头部信息 | 无 |
| * | 否 | string | null | 自定义参数 | 键值对形式 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/proxy',
  type:'DELETE',
  dataType:'JSON',
  data:{
    p_url: "https://v1.hitokoto.cn",
    p_headers: ["Content-Type:application/json;charset=utf-8"],
    encode:'json',      // 自定义参数
  },
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
axios.delete('http://test.inis.cn/api/proxy',{
    p_url: "https://v1.hitokoto.cn",
    p_headers: ["Content-Type:application/json;charset=utf-8"],
    encode:'json',      // 自定义参数
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
$url  = 'http://test.inis.cn/api/proxy';

// 参数
$params = json_encode([
    "p_url"     =>  "https://v1.hitokoto.cn",
    "p_headers" =>  ["Content-Type:application/json;charset=utf-8"],
    "encode"    =>  "json",      // 自定义参数
]);

$curl   = curl_init();

curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_HTTPHEADER, ["Content-type:application/json;charset='utf-8'","Accept:application/json"]);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($curl, CURLOPT_CUSTOMREQUEST, "DELETE");    // DELETE请求
curl_setopt($curl, CURLOPT_POSTFIELDS, $params);

$result = curl_exec($curl);
curl_close($curl);
$result = json_decode($result,true);

// 输出数据
var_dump($result);
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "id":1349,
    "uuid":"7305461e-1962-4186-ad31-6730ded3e74a",
    "hitokoto":"末将于禁，愿为曹家世代赴汤蹈火。",
    "type":"b",
    "from":"镇魂街",
    "from_who":null,
    "creator":"死木芽",
    "creator_uid":1033,
    "reviewer":0,
    "commit_from":"web",
    "created_at":"1515592778",
    "length":16
}
```
</details>





### 其他代理接口

> 这是一个通过发起一个GET请求来代理请求其他类型的接口   
> 你可以发起一个GET请求，来获取原本需要POST或者其他请求方式才能获取的数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/proxy/[ method = get | put | post | patch | delete ]</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| p_url | 是 | string | null | 代理请求的URL地址 | 无 |
| p_headers | 否 | array | null | 代理请求的header头部信息 | 无 |
| * | 否 | string | null | 自定义参数 | 键值对形式 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/proxy/get',
  type:'GET',
  dataType:'JSON',
  data:{
    p_url: "https://v1.hitokoto.cn",
    p_headers: ["Content-Type:application/json;charset=utf-8"],
    encode:'json',      // 自定义参数
  },
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
axios.get('http://test.inis.cn/api/proxy/get/post',{
    params:{
        p_url: "https://v1.hitokoto.cn",
        p_headers: ["Content-Type:application/json;charset=utf-8"],
        encode:'json',      // 自定义参数
    }
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
$url  = 'http://test.inis.cn/api/proxy/delete?p_url=https://v1.hitokoto.cn&encode=json';

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
    "id":1349,
    "uuid":"7305461e-1962-4186-ad31-6730ded3e74a",
    "hitokoto":"末将于禁，愿为曹家世代赴汤蹈火。",
    "type":"b",
    "from":"镇魂街",
    "from_who":null,
    "creator":"死木芽",
    "creator_uid":1033,
    "reviewer":0,
    "commit_from":"web",
    "created_at":"1515592778",
    "length":16
}
```
</details>





## 获取【客户端】信息

> 通过这个接口你可以获取客户端的信息（包括：系统、手机和浏览器信息）   
> 也可以自己上传UA（user-agent）数据进行解析客户端信息

!> 应用场景：`欢迎信息`

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/other/ua</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| ua | 否 | string | null | user-agent信息 | 如果不提交，系统会自动获取 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/other/ua',
  type:'GET',
  dataType:'JSON',
  data:{
    ua: "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/92.0.4515.159 Safari/537.36"
  },
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
axios.get('http://test.inis.cn/api/other/ua',{
    params:{
        ua: "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/92.0.4515.159 Safari/537.36"
    }
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
$url  = 'http://test.inis.cn/api/other/ua?ua=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/92.0.4515.159 Safari/537.36';

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
        "os":{
            "system":"Windows(x64)",
            "version":"10",
            "equipment":"PC"
        },
        "mobile":{
            "brand":"其他",
            "version":""
        },
        "browser":{
            "kernel":"Chrome",
            "version":"92.0.4515.159"
        }
    }
}
```
</details>
