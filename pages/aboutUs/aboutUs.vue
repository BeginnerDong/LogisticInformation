<template>
	<view>
		<view class="list px-2 bg-white">
			<view class="listLi d-flex a-center py-3 borderB-f5">
				<image src="../../static/images/about-icon.png" mode=""></image>
				<view class="color6 font-28 pl-2 flex-1">客服微信</view>
				<view class="color2 font-26">{{mainData.title}}</view>
			</view>
			<view class="listLi d-flex a-center py-3 borderB-f5">
				<image src="../../static/images/about-icon1.png" mode=""></image>
				<view class="color6 font-28 pl-2 flex-1">联系电话</view>
				<view class="color2 font-26">{{mainData.phone}}</view>
			</view>
			<view class="listLi d-flex a-start py-3 borderB-f5">
				<image src="../../static/images/about-icon2.png" mode=""></image>
				<view class="color6 font-28 pl-2 flex-1">公司地址</view>
				<view class="color2 font-26 dz">{{mainData.description}}</view>
			</view>
		</view>
		<view class="fg"></view>

		<view class="aboutBox p-3">
			<view class="content ql-editor" style="padding:0;" v-html="mainData.content">
			</view>
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
			<button class="item" open-type="contact">
				<image src="../../static/images/nabar4.png" mode=""></image>
				<view>联系客服</view>
			</button>
		</view>


	</view>
</template>

<script>
	const app = getApp();
	export default {

		data() {
			return {
				Router: this.$Router,
				mainData: {}
			}
		},


		onLoad() {
			const self = this;
			self.$Utils.loadAll(['getMainData'], self);
		},

		methods: {

			getMainData() {
				const self = this;
				const postData = {};
				postData.searchItem = {
					thirdapp_id: 2,
					type: 5
				};
				const callback = (res) => {
					if (res.info.data.length > 0) {
						self.mainData = res.info.data[0];
						const regex = new RegExp('<img', 'gi');
						self.mainData.content = self.mainData.content.replace(regex, `<img style="max-width: 100%;"`);
					};
					console.log(self.mainData)
					self.$Utils.finishFunc('getMainData');
				};
				self.$apis.articleGet(postData, callback);
			},

		},
	}
</script>


<style>
	button{border: 0;padding: 0;margin: 0;background: none;line-height: 1.5;}
	button:after{border: 0;}
	.fg {
		width: 100%;
		height: 20rpx;
		background-color: #f5f5f5;
	}

	.listLi image {
		width: 50rpx;
		height: 50rpx;
	}

	.dz {
		width: 400rpx;
		text-align: right;
	}

	.aboutBox image {
		width: 690rpx;
		height: 400rpx;
		margin-top: 30rpx;
	}
</style>
