# 小程序
### 生命周期
https://developers.weixin.qq.com/miniprogram/dev/reference/api/App.html

https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#entryPagePath

### 小程序顶部 tabBar
[参考](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#tabBar)
```
text：选项卡的文字。
pagePath：选项卡对应的页面路径。
iconPath：选项卡的图标的路径。
selectedIconPath：选项卡被选中时的图标路径。
badge：数字显示在图标上方的红色小圆点，用于表示未读消息的数量。
```

### 小程序底部
#### 自定义tabBar
```
1. 在pages.json中配置
{
    "tabBar": {
		"custom": true,
        "list": [
            ... // 理论上这里可以没有，但是也要填，不然会报错，并且建议跟自定义的保持一致，因为涉及到switchTab还是navigateTo
        ]
    }
}
```

### 小程序怎么构建组件
[参考](https://developers.weixin.qq.com/miniprogram/dev/framework/custom-component/)


