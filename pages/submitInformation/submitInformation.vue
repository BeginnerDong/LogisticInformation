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
					<view class="font-30 pl-1 pt-5 d-flex a-center" @click="Router.redirectTo({route:{path:'/pages/selectAddress/selectAddress'}})">请选择<image src="../../static/images/information-icon7.png" class="sj"></image></view>
					<!-- <view class="font-30 pl-1 pt-5 text-center">美国</view> -->
				</view>
			</view>
		</view>
		
		<view class="card mx-2 px-3 rounded10 bg-white position-relative">
			<!-- 运输方式 -->
			<view class="font-30 color2 pt-4">运输方式</view>
			<view class="select d-flex flex-wrap">
				<view class="font-28 color9 d-flex a-center label">
					<image src="../../static/images/information-icon3.png" mode=""></image><text>快递</text>
				</view>
				<view class="font-28 color9 d-flex a-center label">
					<image src="../../static/images/information-icon4.png" mode=""></image><text>空运</text>
				</view>
				<view class="font-28 color9 d-flex a-center label">
					<image src="../../static/images/information-icon4.png" mode=""></image><text>海运</text>
				</view>
				<view class="font-28 color9 d-flex a-center label">
					<image src="../../static/images/information-icon4.png" mode=""></image><text>铁路</text>
				</view>
			</view>
			<!-- 货物类型 -->
			<view class="font-30 color2 pt-4">货物类型</view>
			<view class="select d-flex flex-wrap">
				<view class="font-28 color9 d-flex a-center label">
					<image src="../../static/images/information-icon4.png" mode=""></image><text>普货</text>
				</view>
				<view class="font-28 color9 d-flex a-center label">
					<image src="../../static/images/information-icon4.png" mode=""></image><text>带电</text>
				</view>
				<view class="font-28 color9 d-flex a-center label">
					<image src="../../static/images/information-icon4.png" mode=""></image><text>带磁</text>
				</view>
				<view class="font-28 color9 d-flex a-center label">
					<image src="../../static/images/information-icon4.png" mode=""></image><text>带磁带电</text>
				</view>
				<view class="font-28 color9 d-flex a-center label">
					<image src="../../static/images/information-icon4.png" mode=""></image><text>鞋子</text>
				</view>
				<view class="font-28 color9 d-flex a-center label">
					<image src="../../static/images/information-icon4.png" mode=""></image><text>包包</text>
				</view>
				<view class="font-28 color9 d-flex a-center label">
					<image src="../../static/images/information-icon4.png" mode=""></image><text>纺织品</text>
				</view>
				<view class="font-28 color9 d-flex a-center label">
					<image src="../../static/images/information-icon4.png" mode=""></image><text>其他</text>
				</view>
			</view>
			<!-- 预计重量 -->
			<view class="font-30 color3 d-flex a-center j-sb pt-5 pb-3 kg">
				<view>预计重量</view>
				<input type="text" placeholder="请输入" class="font-26 color6 border-e1 rounded"/>
				<view class="font-28">(KG)</view>
			</view>
			
			<view class="position-absolute iconBox d-flex j-sb">
				<image src="../../static/images/information-icon5.png" mode=""></image>
				<image src="../../static/images/information-icon6.png" mode=""></image>
			</view>
		</view>
		
		<!-- 联系方式 -->
		<view class="mx-2 mt-2 px-3 rounded10 bg-white card2">
			<input type="text" placeholder="姓名" />
			<input type="text" placeholder="联系方式" />
			<view class="submit" @click="submit()">提交</view>
			<view class="font-22 text-center colorM pt-3 pb-4">提交后我们会有专业的客服人员回复</view>
		</view>
		
		<!-- 下单须知 -->
		<view class="color9 font-24 pb-4 mx-3">
			<view class="pt-4 pb-3 font-28 color2">下单须知</view>
			<view class="pb-3">1.如货物出货后无提取信息的，无论任何原因造成，例如：海关查验扣件、丢件、等各种原因造成无提取物的，推未提取部分的运费，且按实际采购货值进行赔偿，赔偿最高不超过30RMB/KG</view>
			<view>2.不承担的物品包括：纯电池、仿牌、液体、粉末、食品、鲜货、药品、腐蚀性物品、易燃易爆军火武器等违禁品 </view>
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
				is_show:false
			}
		},
		methods: {
			submit(){
				const self = this;
				self.is_show = true;
				setTimeout(function(){
					self.is_show = false;
				},3000)
				clearTimeout();
			}
		}
	}
</script>

<style>
page{background-color: #f5f5f5;}
.bjImg{width: 100%;height: 320rpx;}
.mask{width: 100%;height: 100%;background-color: rgba(0,0,0,0.3);position: absolute;top: 0;left: 0;}
.icon1{width: 22rpx;height: 30rpx;margin-right: 10rpx;}
.icon2{width: 28rpx;height: 28rpx;margin-right: 10rpx;}
.icon3{width: 127rpx;height: 46rpx;}
.headInfor{width: 554rpx;margin-top: 60rpx;height: 120rpx;}
.sj{width: 17rpx;height: 9rpx;margin-left: 10rpx;}

.card{margin-top: -80rpx;}
.select image{width: 30rpx;height: 30rpx;margin-right: 10rpx;}
.label{width: 25%;margin-top: 30rpx;}

.kg input{width: 400rpx;height: 70rpx;text-indent: 30rpx;}
.iconBox{width: 92%;bottom: -30rpx;}
.iconBox image{width: 8rpx;height: 43rpx;}

.card2 input{font-size: 26rpx;color: #999;padding: 40rpx 0 20rpx;border-bottom: 1px solid #e1e1e1;text-indent: 24rpx;position: relative;}
.card2 input::before{content: '*';color: #E80F0F;position: absolute;left: -25rpx;}
.submit{margin-top: 80rpx;}

.model{width: 400rpx;height: 300rpx;background-color: rgba(0,0,0,0.5);}
.model image{width: 88rpx;height:62rpx;margin: 50rpx 0;}
</style>
