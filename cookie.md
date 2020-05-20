## cookie

### 基础

- cookie体积较小，40k左右
- 默认随每次请求发送，可以通过`xhr.withCredentail`设置是否携带cookie
- 不设置过期时间的话，即为会话存储，页面卸载就消失
- 不可跨域，不同域下的cookie不能交互

### cookie的属性

![cookieAttr](https://user-gold-cdn.xitu.io/2017/10/2/88a294c5374093cedd41bb1ce50cd9d4?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

- name和value，组成键值对
- domain，指域名，即cookie所绑定的域名，默认为当前域。设置为一级域名的，则所有的子域名都能访问，若在子域名中domain设置为当前域，则上级域名无权访问。[详细解释](https://blog.csdn.net/supermao1013/article/details/83827310)
- path，设置当前cookie可访问的路由范围，默认为"/"，即根目录，表示所有的路由都能访问当该cookie
- expires/Max-Age，该属性控制当前cookie的存活时间
- httpOnly，是否允许脚本访问cookie

### 服务端设置cookie

在请求通的Set-Cookie字段中设置

`response.setHeader('Set-Cookie', 'isvisit=1');`

### 客户端设置cookie

```javascript
		var oUserName = document.querySelector(".username");
        var oPassWord = document.querySelector(".password");
        var oForm = document.querySelector("form");
        var oGet = document.querySelector(".get");
        var oRemove = document.querySelector(".remove");

        //设置cookie
        oForm.onsubmit = function () {
            setCookie(oPassWord.name, oPassWord.value, 7);
            return false;
        }
        // 删除cookie
        oRemove.onclick = function () {
            removeCookie(oPassWord.name);
        }

        //设置cookie
        function setCookie(name, value, time) {
            var newDate = new Date();
            newDate.setDate(newDate.getDate() + time);
            document.cookie = `${name}=${value};expires=${time==null?"":newDate}`;
        }
        //获取cookie
        function getCookie(name) {
            var allCookie = document.cookie;
            var nameIndex = allCookie.search(`${name}=`);
            var valueIndex = 0;
            // 判断当前cookie是否为最后一个，最后一个无“;”
            allCookie.indexOf(";", nameIndex) > 0 ? valueIndex = allCookie.indexOf(";", nameIndex) : valueIndex = allCookie.length;
            return allCookie.slice(nameIndex + (`${name}=`.length), valueIndex);
        }
        // 删除cookia
        function removeCookie(name) {
            setCookie(name, "123", -1);
        }
```

