<template>
	<view>
		<view class="head position-relative">
			<image src="../../static/images/information-img1.png" class="bjImg"></image>
			<view class="mask"></view>
			<view class="headInfor position-absoluteXY m-a d-flex j-sb a-center">
				<view class="colorf">
					<view class="font-24 d-flex a-center"><image src="../../static/images/information-icon1.png" class="icon1"></image>起运地</view>
					<view class="font-30 pl-1 pt-5 text-center">深圳市</view>
				</view>
				<image src="../../static/images/information-icon.png" class="icon3"></image>
				<view class="colorf">
					<view class="font-24 d-flex a-center"><image src="../../static/images/information-icon2.png" class="icon2"></image>目的地</view>
					<view v-if="name==''">
						<view class="font-30 pl-1 pt-5 d-flex a-center"
						@click="Router.navigateTo({route:{path:'/pages/selectAddress/selectAddress?type='+type}})">请选择
						<image src="../../static/images/information-icon7.png" class="sj"></image></view>
					</view>
					
					<view class="font-30 pl-1 pt-5 text-center" v-else>{{name}}</view>
				</view>
			</view>
		</view>
		
		<view class="card mx-2 px-3 rounded10 bg-white position-relative">
			<!-- 运输方式 -->
			<view class="font-30 color2 pt-4">运输方式</view>
			<view class="select d-flex flex-wrap">
				<view class="font-28 color9 d-flex a-center label" 
					v-for="(item,index) in transportType" :key="item.id"
					v-if = "transportType.length>0"
					@click="choose(1,index)"
				>
					<image :src="submitData.gender==item.id?'../../static/images/information-icon3.png':'../../static/images/information-icon4.png'"
					 mode=""></image><text>{{item.title}}</text>
				</view>
				<view v-if="transportType.length==0&&name!=''" class="color9 mt-2">暂无可选运输方式</view>
				<view v-if="transportType.length==0&&name==''" class="color9 mt-2">请先选择国家</view>
			</view>
			<!-- 货物类型 -->
			<view class="font-30 color2 pt-4">货物类型</view>
			<view class="select d-flex flex-wrap">
				<view class="font-28 color9 d-flex a-center label"
					v-for="(item,index) in goodsTypeData" :key="item.id"
					@click="choose(2,index)"
				>
					<image :src="submitData.class==item.id?'../../static/images/information-icon3.png':'../../static/images/information-icon4.png'"
					 mode=""></image><text>{{item.title}}</text>
				</view>
				
			</view>
			<!-- 预计重量 -->
			<view class="font-30 color3 d-flex a-center j-sb pt-5 pb-3 kg">
				<view>预计重量</view>
				<input type="digit" placeholder="请输入" v-model="submitData.keywords" class="font-26 color6 border-e1 rounded"/>
				<view class="font-28">(KG)</view>
			</view>
			
			<view class="position-absolute iconBox d-flex j-sb">
				<image src="../../static/images/information-icon5.png" mode=""></image>
				<image src="../../static/images/information-icon6.png" mode=""></image>
			</view>
		</view>
		
		<!-- 联系方式 -->
		<view class="mx-2 mt-2 px-3 rounded10 bg-white card2">
			<input type="text" placeholder="姓名"  v-model="submitData.description"/>
			<input type="text" placeholder="联系方式" v-model="submitData.phone"/>
			<button style="font-size: 15px;" class="submit" open-type="getUserInfo" @getuserinfo="Utils.stopMultiClick(submit)">提交</button>
			<view class="font-22 text-center colorM pt-3 pb-4">{{artData.description}}</view>
		</view>
		
		<!-- 下单须知 -->
		<view class="color9 font-24 pb-4 mx-3">
			<view class="pt-4 pb-3 font-28 color2">{{artData.title}}</view>
			<view class="pb-3">
				<view class="content ql-editor" style="padding:0;" v-html="artData.content">
				</view>
			</view>
		</view>
		
		
		<!-- 提示 -->
		<view class="model colorf rounded10 position-fixedXY m-a d-flex flex-column a-center font-24" v-if="is_show">
			<image src="../../static/images/yes.png" mode=""></image>
			<view>您的信息已提交</view>
			<view>稍后有工作人员联系您</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				is_show:false,
				name:'',
				transportType:[],
				goodsTypeData:[],
				submitData:{
					title:'深圳市',
					behavior:'',
					gender:'',
					class:'',
					description:'',
					phone:'',
					keywords:''
				},
				Utils:this.$Utils,
				type:'',
				//noCountry:false
				artData:{}
			}
		},
		
		onLoad(options) {
			const self = this;
			if (options.name) {
				self.name = options.name?options.name:uni.getStorageSync('name');
				self.getTransType()
			}else if(options.type){
				self.type = options.type
			};
			self.$Utils.loadAll(['getGoodsType','getArtData'], self);
		},
		
		onShow() {
			const self = this;
			if (uni.getStorageSync('name')) {
				self.name = uni.getStorageSync('name');
				self.getTransType()
			}
		},
		
		methods: {
			
			getArtData() {
				const self = this;
				const postData = {};
				postData.searchItem = {
					thirdapp_id: 2,
					type: 6
				};
				const callback = (res) => {
					if (res.info.data.length > 0) {
						self.artData = res.info.data[0];
						const regex = new RegExp('<img', 'gi');
						self.artData.content = self.artData.content.replace(regex, `<img style="max-width: 100%;"`);
					};
					console.log(self.artData)
					self.$Utils.finishFunc('getArtData');
				};
				self.$apis.articleGet(postData, callback);
			},
			
			messageAdd() {
				const self = this;
				const postData = {};
				postData.tokenFuncName = 'getProjectToken';
				if(!wx.getStorageSync('user_info')||wx.getStorageSync('user_info').headImgUrl==''||!wx.getStorageSync('user_info').headImgUrl){
				  postData.refreshToken = true;
				};
				postData.data = {};
				postData.data = self.$Utils.cloneForm(self.submitData);
				const callback = (data) => {	
					uni.hideLoading();
					if (data.solely_code == 100000) {					
						/* self.is_show = true;
						setTimeout(function(){
							self.is_show = false;
						},2000)
						clearTimeout(); */
						self.$Utils.showToast('您的信息已提交,稍后有工作人员联系您', 'none', 2000)
						setTimeout(function() {
							uni.navigateBack({
								delta:1
							})
						}, 2000);
						
					} else {
						uni.setStorageSync('canClick', true);
						self.$Utils.showToast(data.msg, 'none', 1000)
					}	
				};
				self.$apis.messageAdd(postData, callback);
			},
			
			
			
			
			submit() {
				const self = this;
				uni.showLoading();
				uni.setStorageSync('canClick', false);
				var newObject = self.$Utils.cloneForm(self.submitData);
				delete newObject.gender;
				delete newObject.class;
				delete newObject.keywords;
				const pass = self.$Utils.checkComplete(newObject);
				console.log('pass', pass);
				console.log('self.submitData',self.submitData)
				
				if (pass) {	
					if (self.submitData.phone.trim().length != 11 || !/^1[3|4|5|6|7|8|9]\d{9}$/.test(self.submitData.phone)) {
						uni.setStorageSync('canClick', true);
						self.$Utils.showToast('请输入真实有效的手机号', 'none', 1000)
						return;
					}
					const callback = (user, res) => {
						console.log(res)
						self.messageAdd();
					};
					self.$Utils.getAuthSetting(callback);
				
				} else {
					uni.setStorageSync('canClick', true);
					self.$Utils.showToast('请补全必要信息', 'none')
				};
			},
			
			choose(type,index){
				const self = this;
				if(type == 1){
					self.submitData.gender = self.transportType[index].id
				}else if(type == 2){
					self.submitData.class = self.goodsTypeData[index].id
				}
			},
			
		
			
			getTransType() {
				const self = this;
				const postData = {};
				postData.searchItem = {
					thirdapp_id: 2,
					title:self.name
				};
				postData.getAfter = {
					child: {
						tableName: 'Label',
						middleKey: 'id',
						key: 'parentid',
						searchItem: {
							status:1
						},
						condition: 'in'
					}
				};
				const callback = (res) => {
					if (res.info.data.length > 0) {
						self.aitData = res.info.data[0];
						self.submitData.behavior = self.aitData.id;
						self.transportType = self.aitData.child;
						uni.removeStorageSync('name')
					}
				};
				self.$apis.labelGet(postData, callback);
			},
			
			getGoodsType() {
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
							title: ['in', ['货物类型']],
						},
						condition: 'in'
					}
				};
				const callback = (res) => {
					if (res.info.data.length > 0) {
						self.goodsTypeData = res.info.data
					}
					self.$Utils.finishFunc('getGoodsType');
				};
				self.$apis.labelGet(postData, callback);
			},
				
		},
		
	}
</script>

<style>
page{background-color: #f5f5f5;}
.bjImg{width: 100%;height: 320rpx;}
.mask{width: 100%;height: 100%;background-color: rgba(0,0,0,0.6);position: absolute;top: 0;left: 0;}
.icon1{width: 22rpx;height: 30rpx;margin-right: 10rpx;}
.icon2{width: 28rpx;height: 28rpx;margin-right: 10rpx;}
.icon3{width: 127rpx;height: 46rpx;}
.headInfor{width: 554rpx;margin-top: 60rpx;height: 120rpx;}
.sj{width: 17rpx;height: 9rpx;margin-left: 10rpx;}

.card{margin-top: -80rpx;}
.select image{width: 30rpx;height: 30rpx;margin-right: 10rpx;}
.label{width: 25%;margin-top: 30rpx;}

.kg input{width: 400rpx;height: 70rpx;padding-left: 30rpx;box-sizing: border-box;}
.iconBox{width: 92%;bottom: -30rpx;}
.iconBox image{width: 8rpx;height: 43rpx;}

.card2 input{font-size: 26rpx;color: #999;padding: 40rpx 24rpx 20rpx;border-bottom: 1px solid #e1e1e1;position: relative;}
.card2 input::before{content: '*';color: #E80F0F;position: absolute;left: 0;}
.submit{margin-top: 80rpx;}

.model{width: 400rpx;height: 300rpx;background-color: rgba(0,0,0,0.5);}
.model image{width: 88rpx;height:62rpx;margin: 50rpx 0;}
</style>
