<template>
	<view>
		<!-- banner -->
		<web-view :webview-styles="webviewStyles" src="https://www.szyuqi.com"></web-view>
		
		
		
		
		
		<view style="height: 120rpx;width: 100%;"></view>
		<!-- 底部 -->
		<view class="footer"> 
			<view class="item" @click="Router.redirectTo({route:{path:'/pages/index/index'}})">
				<image src="../../static/images/nabar2.png" mode=""></image>
				<view>首页</view>
			</view>
			<view class="item on">
				<image src="../../static/images/nabar1-a.png" mode=""></image>
				<view>公司官网</view>
			</view>
			<view class="item" @click="Router.redirectTo({route:{path:'/pages/aboutUs/aboutUs'}})">
				<image src="../../static/images/nabar3.png" mode=""></image>
				<view>关于我们</view>
			</view>
			<view class="item" @click="Router.redirectTo({route:{path:'/pages/contact/contact'}})">
				<image src="../../static/images/nabar4.png" mode=""></image>
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
.banner image{height: 363rpx;width: 100%;}

.tit{height: 68rpx;}
.tit .txt{padding-top:40rpx;}
.tit:nth-child(1) image{width: 126rpx;}
.tit2 image{width: 132rpx;height: 60rpx;margin-top: 8rpx;}
.tit3 image{width: 182rpx;height: 50rpx;margin-top: 18rpx;}
.partner image{width: 210rpx;height: 140rpx;box-shadow: 0 0 15rpx 0 #d1d1d1;margin-bottom: 30rpx;}

.conImg{position: relative;height: 350rpx;}
.conImg image{position: absolute;height: 260rpx;width: 410rpx;}
.conImg image:nth-child(1){bottom: 0;left: 0;}
.conImg image:nth-child(2){top: 0;right: 0;}
</style>
