## NodePress 开发文档

> Author By Surmon Surmon@foxmail.com
>
> Site: https://surmon.me
>
> 前端前台PC端：[vue-blog](https://github.com/surmon-china/vue-blog) By Vue2 + Vuex + Nuxt.js
>
> 前端后台：[angular-admin](https://github.com/surmon-china/angular-admin) By Angular2 + Bootstrap4
>

# Todos & Issues
- 驱动搜索引擎ping接口 文章发布后自动ping给搜索引擎xml
- ~~更新readme~~
- ~~rss订阅接口 https://github.com/dylang/node-rss~~
- ~~加入网站地图接口~~
- ~~网站地图由于缓存或者primise不能及时更新~~
- ~~网站地图的数据构成中文章需要筛选公开一发布的文章~~
- ~~对接百度统计开放平台api~~
- ~~密码存储需要使用md5加密机制~~
- ~~token... 等config信息使用node命令参数在shell中配置覆盖~~
- ~~lean 和 翻页插件一起使用，返回的id字段是_id bug~~
- ~~整理统一result的返回结构~~
- ~~围观后计数功能~~
- ~~多说转发热门文章接口~~
- ~~相关文章接口~~

## 开发命令
```bash
# 启动开发模式
npm run dev

# 生产模式
npm start
pm2 start ***
```

## 文件目录

  - 入口文件

    ```
    index.js -> 主程序入口

    启动Express程序，启动并连接数据库，路由分发，引入配置
    ```

  - 配置文件

    ```
    np-config.js -> 主程序配置

    数据库配置（程序内部），全局使用（程序内部），基本信息，其他配置
    ```

  - 数据库

    ```
    np-mongo.js -> 数据库连接启动

    连接并启动数据库
    ```

  - 公共封装函数

    ```
    np-handle.js -> 请求处理器

    handleRequest -> API类型识别器

    handleError -> 控制器失败时解析

    handleSuccess -> 控制器成功时解析
    ```

  - np-auth.js

    ```
    权限验证方法，抽象出的对象
    首先会校验jwt的合理性，然后核对加密信息，核对时间戳
    ```

  - np-sitemap.js

    ```
    网站地图xml生成，抽象出的对象
    包含Tag、Article、Category及一些死数据（页面）的集合，生成xml并写入本地
    实际上，在每次访问sitemap-api和有相关CRUD操作的时候都会被执行
    ```

  - 路由

    ```
    np-routes.js -> 路由控制集合

    ```

  - 控制器

    ```
    np-controller -> 控制器文件夹

    ***.controller.js -> 各功能控制器

    ```

  - 数据模型

    ```
    np-model -> 数据模型文件夹

    ***.model.js -> 各功能数据模型，映射Mongoose对应的模型方法

    ```

## 接口概述

稍后补充...

## 数据结构

  - 通用
    * extend 通用扩展
    ···

  - 分类 CRUD
    * name         - 分类名称 required
    * slug         - 分类名称 required onlyone 唯一!
    * description  - 分类名称
    * pid          - 父分类ID false || null || 0 || ObjectID
    ···

  - 文章 CRUD
    * title        - 文章标题
    * content      - 文章内容
    * description  - 文章描述
    * status       - 文章发布状态 => -1已删除，0草稿，1发布
    * public       - 文章公开状态 =>  0非公开，1公开
    * password     - 文章密码 => 非公开状态生效
    * date         - 发布日期
    * tag          - 文章标签 数组 ObjID
    * category     - 文章分类 数组 ObjID
    * comment      - 数组（对象）
    * meta         - 元数据
    ···

  - 其他...

## 程序架构

  - 服务端

    * [Express](http://www.expressjs.com.cn/ )

    * [node-jsonwebtoken](https://github.com/auth0/node-jsonwebtoken) JWT Json Web Token

  - 后台

    * [ng2-admin](https://akveo.github.io/ng2-admin/) [Angular 2](https://angular.cn/) MVVM

    * [Bootstrap 4](http://v4.bootcss.com/) UI

    * JQuery

    * 富文本编辑器 ---

    * [Simditor](http://simditor.tower.im/) Simditor

    * [Quill](http://quilljs.com/) Quill

    * [Draft.js](http://facebook.github.io/draft-js/) Draft for React

    * [bootstrap-wysiwyg](http://www.bootcss.com/p/bootstrap-wysiwyg/) bootstrap-wysiwyg

    * [wangEditor](http://www.wangeditor.com/) wangEditor

    * MarkDown (最终使用codemirror创建了适用于自己的markdown)

    * [Editor.md](http://pandao.github.io/editor.md/) MarkDown编辑器 - Editor

    * [MarkdownEditor](https://github.com/alecgorge/MarkdownEditor) 简单的MarkDown编辑器 - MarkdownEditor

    * WebIDE （此项目中不再实现）

    * [Codiad](https://github.com/Codiad/Codiad) WebIDE

    * [CodeMirror](http://codemirror.net/) CodeMirror WebIDE

    * Other （此项目中不再实现）

    * [谷歌云输入法]() 云输入法

    * [Web Audio Editor](http://audiee.io/) 音频处理（剪切处理）

    * [webgl-filter](https://github.com/evanw/webgl-filter) WebGL 图片处理 - webgl-filter

    * [h5slides](https://github.com/Jinjiang/h5slides) h5slides 幻灯放映

    * [H5lock](https://github.com/lvming6816077/H5lock) H5手势解锁

    * [favico.js](http://lab.ejci.net/favico.js/) 网站通知徽标

    * [OS.js](https://github.com/os-js/OS.js) OS.js Web OS

    * [Antiscroll](https://github.com/Automattic/antiscroll) Dom代替原生滚动条

    * [APlayer](https://github.com/DIYgod/APlayer) APlayer音频播放器

    * [CommentCoreLibrary](https://github.com/jabbany/CommentCoreLibrary) JS栈弹幕解决方案

    * [CommentCoreLibrary](https://github.com/jabbany/CommentCoreLibrary) JS栈弹幕解决方案

  - 搜索引擎 （使用了Nuxt.js服务端首屏渲染）

    * [Prerender.io](https://prerender.io/) SEO

    * [Handlebars](http://handlebarsjs.com/) HTML 渲染

    * [Vue服务端渲染](https://vuefe.cn/guide/ssr.html)

  - 前台PC端 （仅参考）

    * [Vue2](http://cn.vuejs.org/) MVVM

    * [SOCKET.IO](http://socket.io/) 实时通讯

    * [HOWLER.JS](https://howlerjs.com/) 音频库

    * [Video.js](http://videojs.com/) 播放器

    * [vue-awesome-swiper](https://github.com/surmon-china/vue-awesome-swiper) 跑马灯

  - 前台WAP端

    * [Vue2](http://cn.vuejs.org/) MVVM

    * [Vux](https://github.com/airyland/vux) UI

  - Android/IOS客户端

    * [Weex](https://alibaba.github.io/weex/)

    * [NativeScript 2.0](https://www.nativescript.org/)

    * [React Native](http://reactnative.cn/)
