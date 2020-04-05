本项目是为了学习jsonp而创建的。
# 什么是jsonp
1. jsonp是为了解决Ajax直接请求普通文件存在跨域无权限访问的问题而出现的。Web页面上调用js文件时不受跨域限制（不仅仅是script标签，我们知道所有含有src属性的标签都拥有跨域的能力，如script、img、iframe等）
2. 所以可以理解为：如果想通过纯Web端（Active控件、服务端代理、HTML5的Websocket等方式不算）跨域访问数据就只有一种可能，那就是在远程服务器上设法把数据装进js格式的文件里，供客户端调用和进一步处理。
3. 恰巧JSON格式的数据可以简洁的描述复杂数据，而且JSON还被js原生支持，所以在客户端几乎可以随心所欲地处理这种格式的数据。
4. 所以跨域的解决方案就是Web客户端通过像调用脚本的方式一样，来调用跨域服务器上动态生成的js格式文件（一般以JSON为后缀）。显然，客户端之所以要动态生成JSON文件，就是为了把客户端需要的数据装进去。
5. 所以就逐渐形成了一种非正式传输协议，成为jsonp，该协议的一个要点就是要允许用户传递一个callback参数给服务器，然后服务器返回数据时会将这个callback参数作为函数名来包裹住JSON数据，这样客户端就可以随意定制自己的函数来自动处理返回的数据了。

例如在本地服务器http://localhost/jsonpTest/public/remote.js文件内写入`alert('我是远程文件')`
则执行jsonpTest.html，毫无疑问会弹出“我是远程文件”的提醒窗口。
