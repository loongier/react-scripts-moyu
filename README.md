# react-scripts-moyu
creact-react-app 脚手架扩展 webpack配置扩展

> 运行npm run eject使其暴露webpack等配置文件
> 在根目录找到config文件夹，并找到文件夹下的webpack.config.dev.js文件

## antd 组件库按需加载配置以及主题配置

按照以下链接修改webpack.config.dev.js配置
> [antd配置create-react-app](https://ant.design/docs/react/use-with-create-react-app-cn)

* less loader 参数modifyVars 为主题颜色
* babel-plugin-import 按需加载插件  [babel-plugin-import](https://github.com/ant-design/babel-plugin-import)


## eslint配置

* 在项目根目录下添加.eslintrc文件
* 将以下代码添加到 webpack.config.dev.js
`
use: [{
  // @remove-on-eject-begin
  // Point ESLint to our predefined config.
  options: {
    //configFile: path.join(__dirname, '../.eslintrc'),
    useEslintrc: true
  },
  // @remove-on-eject-end
  loader: 'eslint-loader'
}],
`
添加为
`
preLoaders: [
  {
    test: /\.(js|jsx)$/,
    loader: 'eslint',
    enforce: 'pre',
    use: [{
      // @remove-on-eject-begin
      // Point ESLint to our predefined config.
      options: {
        //configFile: path.join(__dirname, '../.eslintrc'),
        useEslintrc: true
      },
      // @remove-on-eject-end
      loader: 'eslint-loader'
    }],
    include: paths.appSrc,
  }
],
`


