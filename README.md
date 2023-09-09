### 小程序分包配置

> 随着业务代码和组件的引入越来越多，主包的大小一定会越来越大，超过 2m 的主包以后微信开发工具就无法使用预览的功能，为了提前做好准备在一开始就进行分包处理，主包只包含组件和公共代码，分包里放入业务代码

```js
// app.config.ts
export default {
	pages: ["pages/index/index"],
	window: {
		backgroundColor: "#fff",
		backgroundTextStyle: "light",
		navigationBarBackgroundColor: "#fff",
		navigationBarTitleText: "Taro3",
		navigationBarTextStyle: "black",
	},
	subpackages: [
		{
			root: "pages/packageA",
			pages: ["index/index"],
		},
	],
};
```

### 主题定制

- 使用 unocss 完善主题定制，需在每个页面引入<basic-layout></basic-layout>作为根组件， 实现方案[ConfigProvider](https://nutui.jd.com/taro/vue/4x/#/zh-CN/component/configprovider)

### 小程序配置细节

需要注意开发者工具的项目设置：

- 需要设置关闭 ES6 转 ES5 功能，开启可能报错
- 需要设置关闭上传代码时样式自动补全，开启可能报错
- 需要设置关闭代码压缩上传，开启可能报错

### 其他限制

- 小程序中不支持 `<style scoped>`，建议使用 cssModules 代替。
- 自定义 navbar 在模拟器上 safe-area-inset-top 失效，真机可以[微信社区](https://developers.weixin.qq.com/community/develop/doc/0000c21ff082c8cefc9a5986b51800?highLine=safe-area-inset-top%25E5%25A4%25B1%25E6%2595%2588)
- 自定义 tabbar 使用 svg 或者 icon，图片会出现抖动问题[微信社区](https://developers.weixin.qq.com/community/develop/doc/000c84de0cc590bbe54b97edf5e414?highline=tabbar)
