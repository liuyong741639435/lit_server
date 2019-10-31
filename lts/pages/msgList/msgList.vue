<template>
	<view class="content">
		<view class="msglist">
			<view class="item" v-for="(item,index) of list" :key="index">
				<view>
					<image :src="item.imgUrl" mode=""></image>
				</view>
				<view class="text">
					<view>
						<text class="name">{{item.name}}</text>
						<text calss="time">{{item.time}}</text>
					</view>
					<view class="msg">{{item.msg}}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[
					{
						uid:"1001",name:"阿风",imgUrl:"../../static/img/qq.png",msg:"吃了吗",time:"下午3点"
					}
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.content{
		width:100%;
	}
	.msglist{
		width:100%
	}
	.msglist>.item{
		width: 100%;
		display: flex;
	}
	.msglist>.item>.text{
		width: 100%;
	}
	.msglist>.item>.text>:first-child{
		display: flex;
		justify-content:space-between;
	}
	.msglist image{
		width:100upx;height:100upx;
	}
	.msglist .msg{
		width:450upx;
		overflow: hidden;
		white-space: nowrap;
		text-overflow: ellipsis;
	}
</style>
