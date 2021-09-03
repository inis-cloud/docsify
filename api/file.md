### 【上传】文件

> 通过该接口，你可以上传文件到系统中   
> 前提条件是必须 登录 且 未被禁用 的用户  
> 目前只允许上传jpg,jpeg,png,gif,webp,svg,ico,zip,gz,mp3,mp4,avi的文件类型，且限制20MB大小上传，之后会在后台中动态限制上传规则

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/file</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 是 | string | null | null | 登录密钥 | 用于判断是否拥有权限 |
| mode | 是 | string | null | upload | 模式 | 无 |
| file | 否 | file | null | null | 文件 | 无 |


<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<input type="file" id="upload" />

<script>
$("#upload").click(()=>{
    
    let upload = document.querySelector("#upload")
    let file   = upload.files[0];
    
    let params = new FormData
    params.append("login-token", "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...")
    params.append("mode", 'upload')
    params.append("file", file)
    
    $.ajax({
        type: "POST",      // 数据提交类型
        url: "http://api.inis.cc/api/file", // 发送地址
        data: params,      // 发送数据
        async: true,       // 是否异步
        processData: false,// processData 默认为false，当设置为true的时候,jquery ajax 提交的时候不会序列化 data，而是直接使用data
        contentType: false,
        success: (res)=>{
            console.log(res)
        },
        error: (err)=>{
            console.log(err)
        }

    });
});
</script>
```

#### ** axios **

```html
<!-- 导入axios -->
<script src="//unpkg.com/axios/dist/axios.min.js"></script>

<input type="file" id="upload" />

<script>
    let upload = document.querySelector("#upload")
    // 监听 #upload 的change事件
    upload.addEventListener("change", (event) => {
        
        // 获取到选中的文件
        let file = upload.files[0];
        
        let params = new FormData
        params.append("login-token", "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...")
        params.append("mode", 'upload')
        params.append("file", file)
        
        // axios 配置，可以获取上传进度
        const config = {
            headers: { "Content-Type": "multipart/form-data" },
            onUploadProgress: (speed) => {
                if (speed.lengthComputable) {
                    let ratio = speed.loaded / speed.total;
                    // 只是上传到后端，后端并未真正保存成功
                    if (ratio < 1) console.log("当前的上传进度：", ratio)
                }
            }
        }
        
        axios.post("http://api.inis.cc/api/file", params, config).then((res) => {
            if(res.data.code == 200){
                console.log("上传成功", res.data)
            } else {
                console.log("上传失败", res.data.msg)
            }
        })
        
        // 清空选中的文件，方便无刷新再次上传
        event.target.value = ''
        
    }, true)
</script>
```

#### ** php **

```php
<?php
// 晚点再写
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "code": 200,
    "msg": "图片上传成功！",
    "data": "https://api.inis.cn/storage/users/files/uid-2/2021-08/3.jpg"
}
```
</details>






### 【随机图】

> 在inis系统目录`public/storage/random/images/`下新建文件夹或txt文件存储图片   
> 参数 `file=新建的文件夹或txt名`   
> 本地模式：文件夹为随机图本地模式，里面存放的是需要被随机的图片，调用加载需要消耗服务器带宽资源（不推荐）   
> 外链模式：txt文件内存放的是图片地址，一行一个，调用加载不需要占用服务器带宽资源（推荐）

!> 应用场景：`可分类的随机图API`

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/file/random</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| file | 否 | string | null | null | 对应的随机图文件或者文件夹 | 如果不填写，默认随机整站的随机图 |
| json | 否 | bool | false | true、false | 获取JSON格式数据 | 无 |
| sole | 否 | string | null | null | 推荐提交，防止多次请求，返回同一结果 | 参数的值随便，只要是唯一的就行 |


<!-- tabs:start -->

#### ** html **

```html
<img src="http://api.inis.cc/api/file/random?sole=value" />
```

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://api.inis.cc/api/file/random',
  type:'GET',
  dataType:'JSON',
  data:{json:true,sole:Math.round(new Date)},
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
axios.get('http://api.inis.cc/api/file/random',{
    params:{
        json:true,
        sole:Math.round(new Date)
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
$url  = 'http://api.inis.cc/api/file/random?sole=value';

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
    "data":"https://picabstract-preview-ftn.weiyun.com/ftn_pic_abs_v3/34758c568f8f29c23a09910b439e5ff19f29ff580ac3bf11049f0e2d9c9b9187eebeee4dfef6834034a58d097403249f?pictype=scale&amp;from=30013&amp;version=3.3.3.3&amp;uin=97783391&amp;fname=3.jpg&amp;size=750\n"
}
```
</details>





### 【随机文本】

> 在inis系统目录`public/storage/random/words/`下新建txt文件存储内容   
> 参数 `file=新建的txt文件名`   

!> 应用场景：`一言` `舔狗日记`

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/file/words</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| file | 否 | string | null | null | 对应的随机文件 | 如果不填写，默认随机整站的随机文本 |
| sole | 否 | string | null | null | 推荐提交，防止多次请求，返回同一结果 | 参数的值随便，只要是唯一的就行 |


<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://api.inis.cc/api/file/words',
  type:'GET',
  dataType:'JSON',
  data:{sole:Math.round(new Date)},
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
axios.get('http://api.inis.cc/api/file/words',{
    params:{
        sole:Math.round(new Date)
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
$url  = 'http://api.inis.cc/api/file/words?sole=value';

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
    "data":"许一人以偏爱，尽此生之慷慨。"
}
```
</details>