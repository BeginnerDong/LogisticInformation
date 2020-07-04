<template>
	<view>
		<!-- banner -->
		<view class="banner mb-2">
			<image src="../../static/images/website-img.png" mode=""></image>
		</view>
		
		<view class="mx-3">
			<!-- 企业介绍 -->
			<view class="tit my-4 color2 font-26 d-flex">
				<image src="../../static/images/website-icon1.png" mode=""></image>
				<view class="txt pl-1">企业介绍</view>
			</view>
			<view class="font-30 color2">
				<view class="pb-3">指企业的组织形式。以营利为目的的社团法人。在资本主义社会获得高度发展。</view>
				<view class="pb-3">国营工、商、建筑、运输等部门中实行独立经济核算的经营管理组织和某些城市中按行业划分的专业管理机构，也通称公司。 </view>
				<view class="pb-3">指企业的组织形式。以营利为目的的社团法人。在资本主义社会获得高度发展。</view>
			</view>
			
			<!-- 企业文化 -->
			<view class="tit my-4 color2 font-26 d-flex tit2">
				<image src="../../static/images/website-icon2.png" mode=""></image>
				<view class="txt pl-1">企业文化</view>
			</view>
			<view class="font-30 color2">
				<view class="pb-3">指企业的组织形式。以营利为目的的社团法人。在资本主义社会获得高度发展。</view>
				<view class="pb-3">国营工、商、建筑、运输等部门中实行独立经济核算的经营管理组织和某些城市中按行业划分的专业管理机构，也通称公司。 </view>
				<view class="conImg">
					<image src="../../static/images/about-img.png" mode=""></image>
					<image src="../../static/images/website-img.png" mode=""></image>
				</view>
			</view>
			
			<!--合作伙伴 -->
				<view class="tit my-4 color2 font-26 d-flex tit3">
					<image src="../../static/images/website-icon3.png" mode=""></image>
					<view class="txt pl-1">合作伙伴</view>
				</view>
				<view class="font-30 color2 partner d-flex flex-wrap j-sb">
					<image src="../../static/images/home-img7.png" mode=""></image>
					<image src="../../static/images/home-img7.png" mode=""></image>
					<image src="../../static/images/home-img7.png" mode=""></image>
					<image src="../../static/images/home-img7.png" mode=""></image>
				</view>
				
		</view>
		
		
		
		
		
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
