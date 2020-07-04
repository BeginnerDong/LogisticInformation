<template>
	<view>
		
		<view class="news mx-2">
			<view class="item position-relative d-flex borderT-e1 py-3" @click="Router.redirectTo({route:{path:'/pages/newsDetails/newsDetails'}})">
				<image src="../../static/images/home-img6.png" mode=""></image>
				<view class="d-flex flex-column j-sb h-100 ml-2 txt">
					<view class="font-28 color2 avoidOverflow2">关于2020年“端午节”假期运作通知</view>
					<view class="font-24 color6">YQWL通告 | 2020-06-23</view>
				</view>
			</view>
			<view class="item position-relative d-flex borderT-e1 py-3" @click="Router.redirectTo({route:{path:'/pages/newsDetails/newsDetails'}})">
				<image src="../../static/images/home-img6.png" mode=""></image>
				<view class="d-flex flex-column j-sb h-100 ml-2 txt">
					<view class="font-28 color2 avoidOverflow2">关于2020年“端午节”假期运作通知关于2020年“端午节”假期运作通知关于2020年“端午节”假期运作通知</view>
					<view class="font-24 color6">YQWL通告 | 2020-06-23</view>
				</view>
			</view>
			<view class="item position-relative d-flex borderT-e1 py-3" @click="Router.redirectTo({route:{path:'/pages/newsDetails/newsDetails'}})">
				<image src="../../static/images/home-img6.png" mode=""></image>
				<view class="d-flex flex-column j-sb h-100 ml-2 txt">
					<view class="font-28 color2 avoidOverflow2">关于2020年“端午节”假期运作通知</view>
					<view class="font-24 color6">YQWL通告 | 2020-06-23</view>
				</view>
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
.news .item{height: 140rpx;box-sizing: content-box;}
.news .item:nth-child(1){border: none;}
.news image{width: 200rpx;height: 140rpx;}
.news .item .txt{width: 450rpx;}
</style>
