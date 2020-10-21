<template>
	<view>
		<!-- banner -->
		<view class="banner">
			<swiper class="swiper-box" indicator-dots="indicatorDots" autoplay="autoplay" interval="3000" indicator-active-color="#3395FD">
				<block v-for="(item,index) in sliderData.mainImg" :key="index">
					<swiper-item class="swiper-item">
						<image :src="item.url" mode=""></image>
					</swiper-item>
				</block>
			</swiper>
		</view>
		
		<!-- 热门国家 -->
		<view class="line-h font-30 color2 mt-5 mb-3 mx-2 tit">热门国家</view>
		<view class="hotCountry mx-2 d-flex flex-wrap">
			<view class="country font-34 font-w colorf" @click="Router.navigateTo({route:{path:'/pages/submitInformation/submitInformation?name=美国'}})">
				<image :src="image['美国']&&image['美国'][0]?image['美国'][0].url:''" mode=""></image><text>美国</text>
			</view>
			<view class="country font-34 font-w colorf" @click="Router.navigateTo({route:{path:'/pages/submitInformation/submitInformation?name=日本'}})">
				<image :src="image['日本']&&image['日本'][0]?image['日本'][0].url:''" mode=""></image><text>日本</text>
			</view>
			<view class="country font-34 font-w colorf" @click="Router.navigateTo({route:{path:'/pages/submitInformation/submitInformation?type=欧洲'}})">
				<image :src="image['欧洲']&&image['欧洲'][0]?image['欧洲'][0].url:''" mode=""></image><text>欧洲</text>
			</view>
			<view class="country">
				<view class="font-34 font-w colorf four" @click="Router.navigateTo({route:{path:'/pages/submitInformation/submitInformation?name=加拿大'}})">
					<image :src="image['加拿大']&&image['加拿大'][0]?image['加拿大'][0].url:''"></image><text>加拿大</text>
				</view>
				<view class="font-34 font-w colorf four" @click="Router.navigateTo({route:{path:'/pages/submitInformation/submitInformation?name=墨西哥'}})">
					<image :src="image['墨西哥']&&image['墨西哥'][0]?image['墨西哥'][0].url:''"></image><text>墨西哥</text>
				</view>
			</view>
			<view class="country font-34 font-w colorf" @click="Router.navigateTo({route:{path:'/pages/submitInformation/submitInformation?name=澳大利亚'}})">
				<image :src="image['澳大利亚']&&image['澳大利亚'][0]?image['澳大利亚'][0].url:''" mode=""></image><text>澳大利亚</text>
			</view>
			<view class="country font-34 font-w colorf" @click="Router.navigateTo({route:{path:'/pages/submitInformation/submitInformation?type=其他'}})">
				<image :src="image['更多']&&image['更多'][0]?image['更多'][0].url:''" mode=""></image><text>更多</text>
			</view>
		</view>
	
		<!-- FBA -->
		<view class="line-h font-30 color2 mt-5 mx-2 tit">FBA双清包税</view>
		<view class="fba pl-2 d-flex flex-nowrap pt-3 pb-3">
			<view class="item font-24 color2 p-3 rounded10 shadow flex-shrink mr-3" v-for="(item,index) in FbaData" :key="item.id">
				<view class="font-30 font-w" style="color: #3395FD;">{{item.title}}</view>
				<view>单价：{{item.small_title}}</view>
				<view>参考时效：{{item.keywords}}</view>
				<view>可接货物：{{item.description}}</view>
			</view>

		</view>

		<!-- 新闻公告 -->
		<view class="line-h font-30 color2 mt-2 mb-3 mx-2 d-flex j-sb tit">
			<view>新闻公告</view>
			<view class="d-flex a-center" @click="Router.navigateTo({route:{path:'/pages/news/news'}})">
				<view class="font-24 color9 pr-1">查看更多</view>
				<image src="../../static/images/home-icon.png" mode=""></image>
			</view>
		</view>
		<view class="news mx-2">
			<view class="item position-relative d-flex borderT-e1 py-3" v-for="(item,index) in newsData" :key="item.id" :data-id="item.id"
			 @click="Router.navigateTo({route:{path:'/pages/newsDetails/newsDetails?id='+$event.currentTarget.dataset.id}})">
				<image :src="item.mainImg&&item.mainImg[0]?item.mainImg[0].url:''" mode=""></image>
				<view class="d-flex flex-column j-sb h-100 ml-2 txt">
					<view class="font-28 color2 avoidOverflow2">{{item.title}}</view>
					<view class="font-24 color6">{{item.description}} | {{item.create_time}}</view>
				</view>
			</view>
		</view>

		<!-- 合作伙伴 -->
		<view class="line-h font-30 color2 mt-2 mb-3 mx-2 tit">合作伙伴</view>
		<view class="d-flex j-sb flex-nowrap  mx-2 partner" style="overflow-x: auto;">
			<view v-for="(item,index) in partnerData" :key="item.id" style="margin-right: 30rpx;width: 180rpx;display: flex;justify-content: center;align-items: center;">
				<image  :src="item.mainImg&&item.mainImg[0]?item.mainImg[0].url:''"
				 mode=""></image>
			</view>
		</view>
		
		<!-- 实时订单 -->
		<view class="order d-flex a-center j-sb px-2">
			<image src="../../static/images/home-icon1.png" class="img"></image>
			<swiper class="order-swiper" circular="true" vertical="true" interval="3000" autoplay="autoplay" display-multiple-items="2">
				<block> 
					<swiper-item class="item colorf font-22"  v-for="(item,index) in orderData" :key="item.id">
						<view class="line-h d-flex s-jb pt-2">
							<view>{{item.title}}</view>
							<view class="flex-1 pl-2">{{item.description}}</view>
							<view>{{item.create_time}}</view>
						</view>
					</swiper-item>
				</block>
			</swiper>
		</view>





		<view style="height: 100rpx;width: 100%;"></view>
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
			<button class="item" open-type="contact">
				<image src="../../static/images/nabar4.png" mode=""></image>
				<view>联系客服</view>
			</button>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				Router: this.$Router,
				sliderData: {},
				FbaData: [],
				newsData: [],
				partnerData: [],
				orderData:[],
				image:{
					'美国':'',
					'日本':'',
					'欧洲':'',
					'加拿大':'',
					'墨西哥':'',
					'澳大利亚':'',
					'更多':''
				}
			}
		},
		onLoad() {
			const self = this;
			self.$Utils.loadAll(['getSliderData','getImageData','getFbaData', 'getNewsData', 'getPartnerData','getOrderData'], self);
		},
		
		onShareAppMessage(ops) {
			console.log(ops)
			const self = this;
			if (ops.from === 'button') {
				
				return {
					title:'宇骐国际物流',
					path: '/pages/index/index', //点击分享的图片进到哪一个页面
					//imageUrl:self.mainData&&self.mainData.mainImg&&self.mainData.mainImg[0]&&self.mainData.mainImg[0].url?self.mainData.mainImg[0].url:'',
					success: function(res) {
						// 转发成功
						
						console.log("转发成功:" + JSON.stringify(res));
					},
					fail: function(res) {
						// 转发失败
						console.log("转发失败:" + JSON.stringify(res));
					}
				}
			}else{
				return {
					title:'宇骐国际物流',
					path: '/pages/index/index', //点击分享的图片进到哪一个页面
					//imageUrl:self.mainData&&self.mainData.mainImg&&self.mainData.mainImg[0]&&self.mainData.mainImg[0].url?self.mainData.mainImg[0].url:'',
					success: function(res) {
						// 转发成功
						
						console.log("转发成功:" + JSON.stringify(res));
					},
					fail: function(res) {
						// 转发失败
						console.log("转发失败:" + JSON.stringify(res));
					}
				}
			}
		},

		methods: {
			
			getImageData() {
				const self = this;
				const postData = {};
				postData.searchItem = {
					thirdapp_id: 2,
				};
				postData.getBefore = {
					article: {
						tableName: 'Label',
						middleKey: 'parentid',
						key: 'id',
						searchItem: {
							title: ['in', ['首页背景图']],
						},
						condition: 'in'
					}
				};
				const callback = (res) => {
					if (res.info.data.length > 0) {
						self.imageData = res.info.data;
						for (var i = 0; i < self.imageData.length; i++) {
							self.image[self.imageData[i].title] = self.imageData[i].mainImg
						}
					}
					self.$Utils.finishFunc('getImageData');
				};
				self.$apis.labelGet(postData, callback);
			},

			getSliderData() {
				const self = this;
				const postData = {};
				postData.searchItem = {
					thirdapp_id: 2,
					title: "首页轮播"
				};
				const callback = (res) => {
					if (res.info.data.length > 0) {
						self.sliderData = res.info.data[0]
					}
					self.$Utils.finishFunc('getSliderData');
				};
				self.$apis.labelGet(postData, callback);
			},

			getFbaData() {
				const self = this;
				const postData = {};
				postData.searchItem = {
					thirdapp_id: 2,
					type: 1
				};
				const callback = (res) => {
					if (res.info.data.length > 0) {
						self.FbaData = res.info.data
					};
					self.$Utils.finishFunc('getFbaData');
				};
				self.$apis.articleGet(postData, callback);
			},

			getNewsData() {
				const self = this;
				const postData = {};
				postData.paginate = {
					count: 0,
					currentPage: 1,
					is_page: true,
					pagesize: 3
				};
				postData.searchItem = {
					thirdapp_id: 2,
					type: 2
				};
				const callback = (res) => {
					if (res.info.data.length > 0) {
						self.newsData = res.info.data
					};
					self.$Utils.finishFunc('getNewsData');
				};
				self.$apis.articleGet(postData, callback);
			},

			getPartnerData() {
				const self = this;
				const postData = {};
				postData.searchItem = {
					thirdapp_id: 2,
					type: 3
				};
				const callback = (res) => {
					if (res.info.data.length > 0) {
						self.partnerData = res.info.data
					};
					self.$Utils.finishFunc('getPartnerData');
				};
				self.$apis.articleGet(postData, callback);
			},
			
			getOrderData() {
				const self = this;
				const postData = {};
	/* 			postData.paginate = {
					count: 0,
					currentPage: 1,
					is_page: true,
					pagesize: 2
				}; */
				postData.searchItem = {
					thirdapp_id: 2,
					type: 4
				};
				postData.order = {
					create_time:'desc'
				};
				const callback = (res) => {
					if (res.info.data.length > 0) {
						self.orderData = res.info.data;
						for (var i = 0; i < self.orderData.length; i++) {
							self.orderData[i].create_time = self.orderData[i].create_time.substr(0,10)
						}
					};
					self.$Utils.finishFunc('getOrderData');
				};
				self.$apis.articleGet(postData, callback);
			},

		}
	};
</script>
<style>
	.banner image {
		height: 320rpx;
		width: 100%;
	}

	.tit {
		position: relative;
		text-indent: 18rpx;
	}

	.tit image {
		height: 20rpx;
		width: 10rpx;
	}

	.tit::before {
		content: '';
		background-color: #3395FD;
		height: 20rpx;
		width: 8rpx;
		position: absolute;
		top: 0;
		left: 0;
	}

	.country {
		border-radius: 10rpx;
		overflow: hidden;
		position: relative;
		margin-right: 10rpx;
		margin-bottom: 10rpx;
	}

	.country text {
		width: 100%;
		height: 100%;
		position: absolute;
		top: 0;
		left: 0;
		background-color: rgba(0, 0, 0, 0.2);
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.country image {
		width: 100%;
		height: 100%;
	}

	.country:nth-child(1) {
		width: 380rpx;
		height: 200rpx;
	}

	.country:nth-child(2) {
		width: 320rpx;
		height: 200rpx;
		margin-right: 0;
	}

	.country:nth-child(3) {
		width: 210rpx;
		height: 220rpx;
	}

	.country:nth-child(4) {
		width: 160rpx;
		height: 220rpx;
	}

	.four {
		height: 100rpx;
		margin-bottom: 10rpx;
		position: relative;
	}

	.four:nth-child(2) {
		height: 110rpx;
	}
	button{border: 0;padding: 0;margin: 0;background: none;line-height: 1.5;}
	button:after{border: 0;}
	.country:nth-child(5) {
		width: 180rpx;
		height: 220rpx;
	}

	.country:nth-child(6) {
		width: 130rpx;
		height: 220rpx;
		margin-right: 0;
	}

	.fba {
		overflow-x: auto;
	}

	.fba .item {
		width: 456rpx;
	}

	.news .item {
		height: 140rpx;
		box-sizing: content-box;
	}

	.news .item:nth-child(1) {
		border: none;
		padding-top: 0;
	}

	.news image {
		width: 200rpx;
		height: 140rpx;
		border-radius: 8rpx;
	}

	.news .item .txt {
		width: 450rpx;
	}

	.partner image {
		width: 180rpx;
		height: 120rpx;
		margin-bottom: 30rpx;
	}
	
	.order{height: 110rpx;background-color: #182431;}
	.order .img{width: 118rpx;height: 28rpx;}
	.order-swiper{width: 565rpx;height: 100%;}
</style>
