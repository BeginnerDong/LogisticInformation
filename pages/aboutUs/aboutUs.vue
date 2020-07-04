<template>
	<view>
		<view class="list px-2 bg-white">
			<view class="listLi d-flex a-center py-3 borderB-f5">
				<image src="../../static/images/about-icon.png" mode=""></image>
				<view class="color6 font-28 pl-2 flex-1">客服微信</view>
				<view class="color2 font-26">xianhua001</view>
			</view>
			<view class="listLi d-flex a-center py-3 borderB-f5">
				<image src="../../static/images/about-icon1.png" mode=""></image>
				<view class="color6 font-28 pl-2 flex-1">联系电话</view>
				<view class="color2 font-26">156824587963</view>
			</view>
			<view class="listLi d-flex a-start py-3 borderB-f5">
				<image src="../../static/images/about-icon2.png" mode=""></image>
				<view class="color6 font-28 pl-2 flex-1">公司地址</view>
				<view class="color2 font-26 dz">陕西省西安市雁塔区科技路高新大都荟A座2007</view>
			</view>
		</view>
		<view class="fg"></view>
		
		<view class="aboutBox p-3">
			<view class="content ql-editor" style="padding:0;">国营工、商、建筑、运输等部门中实行独立经济核算的经营管理组织和某些城市中按行业划分的专业管理机构，也通称公司。国营工、商、建筑、运输等部门中实行独立经济核算的经营管理组织和某些城市中按行业划分的专业管理机构，也通称公司。
			</view>
			<image src="../../static/images/about-img.png" mode=""></image>
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
			<view class="item on">
				<image src="../../static/images/nabar3-a.png" mode=""></image>
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

	const app = getApp();
	export default {
		
		data() {
			return {
				Router: this.$Router
			}
		},
	}
	methods: {

	}
</script>


<style>
.fg{width: 100%;height: 20rpx;background-color: #f5f5f5;}

.listLi image{width: 50rpx;height: 50rpx;}
.dz{width: 400rpx;text-align: right;}

.aboutBox image{width: 690rpx;height: 400rpx;margin-top: 30rpx;}
</style>
