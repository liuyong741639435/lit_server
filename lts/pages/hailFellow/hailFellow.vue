<template>
	<view class="fellow">
		
		<view class="top">
			<text>通讯录</text>
			<view>
				<button class="ss" @tap="ss()"></button>
				<view class="add" @tap="add()"></view>
			</view>
		</view>

		<view class="body">
			<view v-for="(item,index) of list" :key="index" @click="conversation(item.uid)">
				<image class="icon" :src="item.imgurl" mode=""></image>
					<text>{{item.nickname}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[
					{uid:"10000",nickname:"阿风",imgurl:"http://src.onlinedown.net/d/imgjpg/99a41834cda8ef0b003cbe15cef6c112.jpg"},
					{uid:"10001",nickname:"阿风",imgurl:"http://src.onlinedown.net/d/imgjpg/99a41834cda8ef0b003cbe15cef6c112.jpg"},
					{uid:"10002",nickname:"阿风",imgurl:"http://src.onlinedown.net/d/imgjpg/99a41834cda8ef0b003cbe15cef6c112.jpg"},
					{uid:"10003",nickname:"阿风",imgurl:"http://src.onlinedown.net/d/imgjpg/99a41834cda8ef0b003cbe15cef6c112.jpg"},
					{uid:"10004",nickname:"阿风",imgurl:"http://src.onlinedown.net/d/imgjpg/99a41834cda8ef0b003cbe15cef6c112.jpg"},
				]
			}
		},
		methods: {
			conversation(uid){
				// 跳转到私聊页面
				uni.navigateTo({
					url:`../conversation/conversation?uid=${uid}`
				})
			},
			ss(){
				console.log("搜索");
			},
			add(){
				console.log("添加")
				uni.navigateTo({
					url:"../add/add";
				})
			}
		}
	}
</script>
<style>
	.body{
		width: 100%;
	}
	.fellow{
		width:100%;
	}
	.body>view:not(:last-child){
		border-bottom:1px solid #8F8F94 ;
	}
	.body>view{
		width:100%;
		height:100upx;
		background: #eef;
		display: flex;
	}
	.body>view>image.icon{
		width: 100upx;height: 100upx;
		margin: 0 20upx;
		border-radius: 20%;
		overflow: hidden;
	}
	.body>view>text{
		font-size: 70upx;
		line-height: 100upx;
	}
	/* top部分 */
	.top{
		width:100%;height:88upx;
		position:fixed;
		top:0;left:0;
		z-index: 1000;
		display: flex;
		justify-content:space-between;
		align-items: center;
	}
	.top>view{
		display: flex;
	}
	.fellow .top text:first-child{
		margin-left: 30upx;
		font-size:40upx;
		font-weight: 600;
	}
	.fellow .top .ss{
		width:60upx;height:60upx;
		/* background: #00FF00; */
		background: url("https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1572530412973&di=aece461195f24b08f9741532cc99d1ce&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F00%2F86%2F85%2F4756ec346692cd0.jpg");
		background-size:100% 100% ;
		margin-right: 10upx;
	}
	.fellow .top .add{
		width:60upx;height:60upx;
		/* background: #00FF00; */
		background: url("https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1572530446991&di=face188ca7151543d69612c5d4472b2c&imgtype=0&src=http%3A%2F%2Fku.90sjimg.com%2Felement_pic%2F00%2F92%2F73%2F3956f2322ea8dd4.jpg");
		background-size:100% 100% ;
		margin-right: 30upx;
	}
</style>
