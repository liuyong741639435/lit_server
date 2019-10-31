<template>
	<view class="conversation">
		<!-- 头部 -->
		<!-- <view class="head"> -->
			<!-- <view>返回</view> -->
			<!-- <view>小绩</view> -->
			<!-- <view>更多</view> -->
		<!-- </view> -->
		<!-- 消息区间 -->
		<view class="con_body">
			<view v-for="(item,index) of list" :key="index" :title="item.isRight">
				<view class="icon">
					<image :src="item.imgurl" mode=""></image>
				</view>
				<view>
					<view class="msg">{{item.msg}}</view>
				</view>
			</view>
		</view>
		<!-- 消息区间 -->
		<!-- 发送区域 -->
		<view class="enter">
			<input type="text" v-model="msg">
			<button @click="WSenter" type="primary">发送</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				oneself:{uid:""},
				uid:"",
				list:[],
				msg:"",//输入框输入
			}
		},
		methods: {
			// ws初始化
			webScoketInit(){
				// 连接服务器
				console.log("调用初始化")
				// 事件  服务器回复消息
				uni.onSocketMessage((res)=>{
					console.log(res.data);
					this.list.push(res.data);
				})
				// 事件 监听错误
				uni.onSocketError(function (res) {
				  console.log('WebSocket连接打开失败，请检查！');
				});
				// 事件
				uni.onSocketOpen(function (res){
				console.log('WebSocket连接已打开！');
				})
				console.log("调用初始化完毕")
			},
			// 发送消息
			WSenter(){
				var obj={imgurl:"../../static/img/qq.png",fsuid:this.oneself.uid,nickname:"阿风",time:"下午3点",msg:this.msg}
				var data=JSON.stringify(obj);
				uni.sendSocketMessage({
					data
				})
				console.log("发送了");
			}
		},
		onLoad(option){
			this.uid=option.uid;
			this.webScoketInit();
		}
	}
</script>
<style>
	/*  */
	.conversation{
		width: 100%;
		/* position:fixed; */
	}
	/* 头部 */
	.conversation>.head{
		width:100%;height:120upx;
		background-color:#0FAEFF;
		position:fixed;
		left:0;top:0;
		display: flex;
		/* justify-content: space-between;	 */
		z-index: 100;
	}
	
	
	/* 聊天区域 */
	.conversation>view.con_body{
		width: 100%;
		height:100%;
		background: #e4e4e4;
		display: flex;
		flex-direction: column;
		padding-top: 140upx;
		margin-bottom: 50upx;  /*要和enter 高度一致*/
		/* overflow-y: hidden; */
		z-index: -100;
	}
	/* 聊天消息 */
	.conversation>view.con_body>view{
		width:100%;
		/* border: 1px solid red; */
		display: flex;
		padding-bottom: 20upx;
	}
	/* 头像的父元素 */
	.conversation>view.con_body>view>.icon{
		width: 100upx;height: 100upx;
		margin: 0 20upx;
		overflow: hidden;
	}
	/* 头像的父元素 */
	.conversation>view.con_body>view>.icon>image{
		width: 100%;
		height: 100%;
		background: #0FAEFF;
		border-radius: 20%;
	}
	
	.conversation .msg{
		word-break: break-all;
		width:460upx;
	}
	.conversation>view.con_body>[title]{
		flex-direction: row-reverse;
	}
	.conversation>view.con_body>[title]>view>view{
		display: flex;
		flex-direction: row-reverse;
	}
	.conversation>view.con_body>[title] .msg{
	}
	
	/* enter */
	.enter{
		width: 100%;height: 120upx; /*高度要和聊天区域下外边距一致*/
		background-color:#0FAEFF;
		position:fixed;
		left:0;bottom:0;
		display: flex;
		align-items: center;
		justify-content:center;
	}
	.conversation .enter>input{
		width:75%;height:70%;
		background-color:#0f0;
	}
	.conversation .enter>button{
		width:20%;height:70%;
	}
</style>
