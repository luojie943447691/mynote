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

## 3.腾讯地图开放平台

https://lbs.qq.com/miniProgram/jsSdk/jsSdkGuide/jsSdkOverview

我们需要使用的是逆地址解析



uniapp有个BUG 在配置page.json的时候 会让你复制一段permission 这个配置需要在微信开发工具的app.json和uniapp的page.json里面配置

```js
"permission": {
		"scope.userLocation": {
			"desc": "你的位置信息将用于小程序位置接口的效果展示"
		}
	}
```

## 4. uni.navigateTo()使用的注意事项

url的书写一定要注意 组件在哪里被调用，相对路径是根据父组件写的

## 5. 用路由来判断来自哪个界面

```js
//路由判断
			onLoad(){
				let pages = getCurrentPages();//获取页面栈
				let beforePage = pages[pages.length - 2];//上个页面
				let pathArr = beforePage.route.split('\/')
				this.fromPage = pathArr[pathArr.length - 1]
				log(this.fromPage)
			}
```

## 6. 微信获取用户登录授权

微信地址官方文档地址

https://developers.weixin.qq.com/community/develop/doc/000cacfa20ce88df04cb468bc52801?highLine=getUserProfile

```js
uni.getUserProfile({
				  desc: 'weixin',
				  success: (infoRes) => {
					console.log(infoRes.userInfo);
				  },
				  fail:(err) =>{
					  error(err)
				  }
				});
```

## 7. 用户上传的图片和视频都上传到云服务器，再从把云服务器的地址存储到数据库即可

推荐使用阿里云oss

## 8. 自然语言处理 百度AI开放平台

什么是自然语言处理？

比如我们所使发表的用户评价  就是自然语言
