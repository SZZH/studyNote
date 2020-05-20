# umi的基本使用
最近接手到一个UMI项目，出于想加深自己对该应用框架的理解，故写下这篇文章，供自己或对此不太了解的朋友，快速熟悉UMI。

[为什么选择umi](https://umijs.org/zh-CN/docs)
 
## 创建一个umi项目
- 下载脚手架	`yarn create @umijs/umi-app`
- 下载依赖	`yarn`

## 目录结构
- package.json			(npm依赖)
- .umirc.ts		(umi配置)
- .env (环境变量)
- dist （项目输出目录）
- mock	
- public （静态文件目录）
- src 
  - .umi （临时文件目录，umi运行时生成的各种文件）
  - layout/index.tsx （全局布局，在约定式路由下生效）
  - pages （组件目录）
     - index.less
     - index.tsx
  - app.ts （运行时配置文件，即浏览器端所需依赖）


## 路由
- 配置式路由：
在.umirc.ts中配置routes项，[参考这里](https://umijs.org/zh-CN/docs/routing)
- 约定式路由：按照src/pages下的目录结构，umi进行自动设置路由
  - 动态路由：文件名以$开头，如：在users目录下定义$id.tsx，$表示匹配任意字符串，此时访问users下的任何路由都会转到该组件
  - 嵌套路由：pages下的目录有_layout.tsx文件时，会以此为当前组件的布局模板
  - 404路由：pages下的404.tsx