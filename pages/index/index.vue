<template>
	<view>
		<!-- banner -->
		<view class="banner">
			<swiper class="swiper-box" indicator-dots="indicatorDots" autoplay="autoplay" interval="3000" duration="duration" indicator-active-color="#3395FD">
				<block>
					<swiper-item class="swiper-item">
						<image src="../../static/images/home-banner.png" mode=""></image>
					</swiper-item>
				</block>
				<block>
					<swiper-item class="swiper-item">
						<image src="../../static/images/information-img1.png" mode=""></image>
					</swiper-item>
				</block>
			</swiper>
		</view>
		
		<!-- 热门国家 -->
		<view class="line-h font-30 color2 mt-5 mb-3 mx-2 tit">热门国家</view>
		<view class="hotCountry mx-2 d-flex flex-wrap">
			<view class="country font-34 font-w colorf" @click="Router.redirectTo({route:{path:'/pages/submitInformation/submitInformation'}})"><image src="../../static/images/home-img0.png" mode=""></image><text>美国</text></view>
			<view class="country font-34 font-w colorf" @click="Router.redirectTo({route:{path:'/pages/submitInformation/submitInformation'}})"><image src="../../static/images/home-img.png" mode=""></image><text>日本</text></view>
			<view class="country font-34 font-w colorf" @click="Router.redirectTo({route:{path:'/pages/submitInformation/submitInformation'}})"><image src="../../static/images/home-img1.png" mode=""></image><text>欧洲</text></view>
			<view class="country">
				<view class="font-34 font-w colorf four" @click="Router.redirectTo({route:{path:'/pages/submitInformation/submitInformation'}})"><image src="../../static/images/home-img2.png" ></image><text>加拿大</text></view>
				<view class="font-34 font-w colorf four" @click="Router.redirectTo({route:{path:'/pages/submitInformation/submitInformation'}})"><image src="../../static/images/home-img3.png" ></image><text>墨西哥</text></view>
			</view>
			<view class="country font-34 font-w colorf" @click="Router.redirectTo({route:{path:'/pages/submitInformation/submitInformation'}})"><image src="../../static/images/home-img4.png" mode=""></image><text>澳门</text></view>
			<view class="country font-34 font-w colorf" @click="Router.redirectTo({route:{path:'/pages/submitInformation/submitInformation'}})"><image src="../../static/images/home-img5.png" mode=""></image><text>更多</text></view>
		</view>
		
		<!-- FBA -->
		<view class="line-h font-30 color2 mt-5 mx-2 tit">FBA双清包税</view>
		<view class="fba pl-2 d-flex flex-nowrap pt-3 pb-3">
			<view class="item font-24 color2 p-3 rounded10 shadow flex-shrink mr-3">
				<view class="font-30 font-w">美国FBA双清包税</view>
				<view>单价：<text>￥45/KG</text>起</view>
				<view>参考时间：3-5天</view>
				<view>可接货物：普货、带电磁炉产品</view>
			</view>
			<view class="item font-24 color2 p-3 rounded10 shadow flex-shrink mr-3">
				<view class="font-30 font-w">美国FBA双清包税</view>
				<view>单价：<text>￥45/KG</text>起</view>
				<view>参考时间：3-5天</view>
				<view>可接货物：普货、带电磁炉产品</view>
			</view>
			<view class="item font-24 color2 p-3 rounded10 shadow flex-shrink mr-3">
				<view class="font-30 font-w">美国FBA双清包税</view>
				<view>单价：<text>￥45/KG</text>起</view>
				<view>参考时间：3-5天</view>
				<view>可接货物：普货、带电磁炉产品</view>
			</view>
		</view>
		
		<!-- 新闻公告 -->
		<view class="line-h font-30 color2 mt-2 mb-3 mx-2 d-flex j-sb tit">
			<view>新闻公告</view>
			<view class="d-flex a-center" @click="Router.redirectTo({route:{path:'/pages/news/news'}})">
				<view class="font-24 color9 pr-1">查看更多</view>
				<image src="../../static/images/home-icon.png" mode=""></image>
			</view>
		</view>
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
		
		<!-- 合作伙伴 -->
		<view class="line- h font-30 color2 mt-2 mb-3 mx-2 tit">合作伙伴</view>
		<view class="d-flex flex-wrap j-sb mx-2 partner">
			<image src="../../static/images/home-img7.png" mode=""></image>
			<image src="../../static/images/home-img7.png" mode=""></image>
			<image src="../../static/images/home-img7.png" mode=""></image>
			<image src="../../static/images/home-img7.png" mode=""></image>
			<image src="../../static/images/home-img7.png" mode=""></image>
		</view>
		
		
		
		
		
		<view style="height: 120rpx;width: 100%;"></view>
		<!-- 底部 -->
		<view class="footer"> 
			<view class="item on">
				<image src="../../static/images/nabar2-a.png" mode=""></image>
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
				Router:this.$Router,
				is_show: false,
			}
		},
		onLoad() {
			const self = this;
			// self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			
		}
	};
</script>
<style>
.banner image{height: 320rpx;width: 100%;}
.tit{position: relative;text-indent: 18rpx;}
.tit image{height: 20rpx;width: 10rpx;}
.tit::before{content:'';background-color: #3395FD;height: 20rpx;width: 8rpx;position: absolute;top: 0;left: 0;}

.country{border-radius: 10rpx;overflow: hidden;position: relative;margin-right: 10rpx;margin-bottom: 10rpx;}
.country text{width: 100%;height: 100%;position: absolute;top: 0;left: 0;background-color: rgba(0,0,0,0.2);display: flex;align-items: center;justify-content: center;}
.country image{width: 100%;height: 100%;}
.country:nth-child(1){width: 380rpx;height: 200rpx;}
.country:nth-child(2){width: 320rpx;height: 200rpx;margin-right: 0;}
.country:nth-child(3){width: 210rpx;height: 220rpx;}
.country:nth-child(4){width: 160rpx;height: 220rpx;}
.four{height: 100rpx;margin-bottom: 10rpx;position: relative;}
.four:nth-child(2){height: 110rpx;}
.country:nth-child(5){width: 180rpx;height: 220rpx;}
.country:nth-child(6){width: 130rpx;height: 220rpx;margin-right: 0;}

.fba{overflow-x: auto;}
.fba .item{width: 456rpx;}

.news .item{height: 140rpx;box-sizing: content-box;}
.news .item:nth-child(1){border: none;padding-top: 0;}
.news image{width: 200rpx;height: 140rpx;}
.news .item .txt{width: 450rpx;}

.partner image{width: 25%;height: 120rpx;margin-bottom: 30rpx;}
</style>
