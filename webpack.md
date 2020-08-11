## webpack
### 核心属性
- entry 入口文件路径，单入口chunk名为main，多入口时名为自己定义的名字
- output 输出文件路径，必须为绝对路径，当前是多入口时，filename的文件名要写成变量
  - **path**:path.join(__dirname,'xxx')
  - **filename**:'xxx.js' /  '*[name]*.js'
  - **publicPath**:'/'，静态文件的读取路径
- module 指定文件，使用loader 
- alias 配置路径别名
- plugin 功能扩展插件
- chunk 代码片段
- mode 优化模式，development/production
- devServer 开发服务配置
  - **contentBase**:path.join(__dirname,'')
  - **port**:xxxx
  - **host**:'localhost'
  - **compress**:true/false(**是否压缩**)
###基本配置
- **loader**
  - style-loader,css-loader，打包并解释css文件
  - file-loader，用于打包图片
  - url-loader，内置file-loader，小于定值大小时，仅生成base64
  - html-withimg-loader，html文件中加载图片
- **plugin**
  - clean-webpack-plugin，重新打包时删除旧的文件
  - html-webpack-plugin，打包html文件
  - mini-css-extract-plugin,单独引入css文件，不再使用style-loader
  - optimize-css-assets-webpack-plugin,压缩css样式
  - terser-webpack-plugin,用来替换uglifyjs-webpack-plugin，以压缩js代码
  - sourceMapDevToolPlugin，追踪代码错误
  - commons-chunks-plugin，代码分片，提取公共代码减少打包体积，[详情](https://www.jianshu.com/p/c0fce0c764ed)，webpack4 中被移除，使用optimization.splitChunks 来代替
  - dllPlugin，将三方依赖库单独打包，即每次重新打包只打包自己的代码。与commonsChunkPlugin 不同的是，不用每次都将三方依赖打包，使用 dllPlugin 需要单独创建一个配置文件 webpack.dll.config.js ，[详情](https://segmentfault.com/a/1190000012925212)
  - happyPack，启用多线程打包 [地址](https://juejin.im/post/5c6e0c3a518825621f2a6f45)
  - compression-webpack-plugin，http压缩，打包后将生成以`.gz`为后缀的文件，部署到服务器上后需要手动配置，以是否需要发送压缩过的文件

### 优化

[地址](https://www.jianshu.com/p/4f58b179c626)

按需加载：使用 es6 提供的 import 语法 [地址](https://juejin.im/post/5bf61082f265da616a474b5c)

