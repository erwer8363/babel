# babel
babel笔记
*****************
### babel能做什么
- 语法转换
- 通过Polyfill方式在目标环境中添加缺失的特性(@babel/polyfill模块)
- 源码转换
### @babel/core babel的核心库 cli的命令行工具@babel/cli
- @babel/preset-env 主要作用是对我们所使用的并且目标浏览器中缺失的功能进行代码转换和加载 polyfill，在不进行任何配置的情况下，@babel/preset-env 所包含的插件将支持所有最新的JS特性ES2015,ES2016等，不包含 stage 阶段)，将其转换成ES5代码
- @babel/polyfill 模块包括 core-js 和一个自定义的 regenerator runtime 模块，可以模拟完整的 ES2015+ 环境(会导致构建出来的包的体积增大)
- @babel/preset-env 提供了一个 useBuiltIns 参数，设置值为 usage 时，就只会包含代码需要的 polyfill,必须要同时设置corejs,建议使用core-js@3
- 使用 @babel/plugin-transform-runtime 插件，所有帮助程序都将引用模块 @babel/runtime，这样就可以避免编译后的代码中出现重复的帮助程序，有效减少包体积
- @babel/plugin-transform-runtime 是一个可以重复使用 Babel 注入的帮助程序，以节省代码大小的插件。
- 首先安装依赖，@babel/plugin-transform-runtime 通常仅在开发时使用，但是运行时最终代码需要依赖 @babel/runtime，所以 @babel/runtime 必须要作为生产依赖被安装
- 如果我们希望 @babel/plugin-transform-runtime 不仅仅处理帮助函数，同时也能加载 polyfill 的话，我们需要给 @babel/plugin-transform-runtime 增加配置信息。