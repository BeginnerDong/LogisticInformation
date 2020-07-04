<template>
	<view>
		<view class="search color6 mx-3 d-flex a-center j-sb mt-2">
			<view class="ss font-28 position-relative">
				<input type="text"/>
				<image src="../../static/images/information-icon8.png" mode=""></image>
			</view>
			<view class="colorB font-30">搜索</view>
		</view>
		
		<view class="font-24 color9 mx-2 pt-4 pb-3">热门站点</view>
		<view class="d-flex flex-wrap j-sb hot mx-2 text-center">
			<view class="item border-e1 font-28 color2 mb-3">日本</view>
			<view class="item border-e1 font-28 color2 mb-3">日本</view>
			<view class="item border-e1 font-28 color2 mb-3">日本</view>
			<view class="item border-e1 font-28 color2 mb-3">日本</view>
			<view class="item border-e1 font-28 color2 mb-3">日本</view>
			<view class="item border-e1 font-28 color2 mb-3">日本</view>
		</view>
		
		
		<view style="height: 120rpx;width: 100%;"></view>
		<view class="bg-white borderT-e1 d-flex j-sb a-center px-2 btnBox">
			<view class="submit colorf font-24 text-center my-2">发送</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
.ss input{width: 620rpx;height: 60rpx;border-radius: 30rpx;background-color: #f5f5f5;padding-left: 76rpx;box-sizing: border-box;}
.ss image{position: absolute;width: 36rpx;height: 34rpx;left: 20rpx;top: 13rpx;}

.hot .item{width: 210rpx;height: 70rpx;line-height: 70rpx;}
.btnBox{position: fixed;bottom: 0;left: 0;right: 0;}
</style>
