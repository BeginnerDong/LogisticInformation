<template>
	<view>
		<view class="text-center mx-2">
			<view class="font-22 color9 py-4">5月23日 上午10:00</view>
			<view class="font-24 color6 pb-4">hello baby可为您服务</view>
			<view class="chat text-left pb-3 user">
				<image src="../../static/images/user.png" mode=""></image>
				<view class="chatTxt font-26 color2 rounded10">你好，在吗？想咨询一下关于物流的有关注意事项</view> 
			</view>
			<view class="chat text-left pb-3 service">
				<image src="../../static/images/user.png" mode=""></image>
				<view class="chatTxt font-26 color2 rounded10">你好！很高心为您服务！您想要咨询什么问题呢？</view> 
			</view>
		</view>
		
		
		<!-- 发送按钮 -->
		<view class="bg-white borderT-e1 d-flex j-sb a-center px-3 sendBox">
			<input type="text" value="" />
			<view class="send colorf font-24 text-center">发送</view>
		</view>
		
		<view style="height: 120rpx;width: 100%;"></view>
		<!-- 底部 -->
		<view class="footer"> 
			<view class="item" @click="Router.redirectTo({route:{path:'/pages/index/index'}})">
				<image src="../../static/images/nabar2.png" mode=""></image>
				<view>首页</view>
			</view>
			<view class="item" @click="Router.redirectTo({route:{path:'/pages/website/website'}})">
				<image src="../../static/images/nabar1.png" mode=""></image>
				<view>公司官网</view>
			</view>
			<view class="item" @click="Router.redirectTo({route:{path:'/pages/aboutUs/aboutUs'}})">
				<image src="../../static/images/nabar3.png" mode=""></image>
				<view>关于我们</view>
			</view>
			<view class="item on">
				<image src="../../static/images/nabar4-a.png" mode=""></image> 
				<view>联系客服</view>
			</view>
		</view>
		
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router
			}
		},
		methods: {
			
		}
	}
</script>

<style>
page{background-color: #f5f5f5;}
.chat{overflow: hidden;}
.chat image{width: 80rpx;height: 80rpx;float: left;}
.chatTxt{max-width: 510rpx;padding: 30rpx;position: relative;background-color: #fff;margin-left: 20rpx;float: left;}
.chatTxt::before{content: "";border: 15rpx solid rgba(0,0,0,0);border-top: 15rpx solid #fff;position: absolute;top: 15rpx;left: -8rpx;}
.service image{float: right;}
.service .chatTxt{background-color: #07C160;margin-right: 20rpx;color: #fff;float: right;}
.service .chatTxt::before{border-top: 15rpx solid #07C160;right: -8rpx;left: auto;}

.sendBox{height: 100rpx;position: fixed;bottom: 100rpx;left: 0;right: 0;}
.sendBox input{height: 55rpx;width: 540rpx;border-radius: 10rpx;background-color: #f5f5f5;}
.send{background-color: #3395FD;width: 100rpx;line-height: 55rpx;border-radius: 10rpx;}
</style>
