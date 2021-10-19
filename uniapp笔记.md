# 注意事项

创建 vue create -p dcloudio/uni-preset-vue my-project
在调创建wx项目的时候  需要进入微信开发工具设置-》安全-》服务端接口

# 常用方法

## 1. 获取布局信息 比如距离顶部多少

直接给组件一个ID即可

```js
const query = uni.createSelectorQuery().in(this);
			query.select('#content').boundingClientRect(data => {
			  console.log("得到布局位置信息" + JSON.stringify(data));
			  console.log("节点离页面顶部的距离为" + data.top);
			}).exec();
```

## 2. 往上拉加载 onReachBottom

页面生命周期只会在父组件生效 也就是说如果一个组件在另一个组件中 那么这个子组件即使到底了也不会生效
