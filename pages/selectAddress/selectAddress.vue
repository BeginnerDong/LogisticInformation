<template>
	<view>
		<view class="search color6 mx-3 d-flex a-center j-sb mt-2">
			<view class="ss font-28 position-relative">
				<input type="text" v-model="title"/>
				<image src="../../static/images/information-icon8.png" mode=""></image>
			</view>
			<view class="colorB font-30" @click="search">搜索</view>
		</view>
		
		<view class="font-24 color9 mx-2 pt-4 pb-3">热门站点</view>
		<view class="d-flex flex-wrap j-sb hot mx-2 text-center">
			<view class="item border-e1 font-28 color2 mb-3" 
				:style="chooseIndex==index?'border:1px solid #3395FD;color:#3395FD':''" 
				v-for="(item,index) of addressData" :key="item.id"
				@click="choose(index)"
			>
				{{item.title}}
			</view>
<!-- 			<view class="item border-e1 font-28 color2 mb-3">日本</view>
			<view class="item border-e1 font-28 color2 mb-3">日本</view>
			<view class="item border-e1 font-28 color2 mb-3">日本</view>
			<view class="item border-e1 font-28 color2 mb-3">日本</view>
			<view class="item border-e1 font-28 color2 mb-3">日本</view> -->
		</view>
		
		
		<view style="height: 120rpx;width: 100%;"></view>
		<view class="bg-white borderT-e1 d-flex j-sb a-center px-2 btnBox">
			<view class="submit colorf font-24 text-center my-2" @click="confirm">确定</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				searchItem:{
					thirdapp_id:2
				},
				addressData:[],
				title:'',
				chooseIndex:-1
			}
		},
		
		onLoad(options) {
			const self = this;
			self.type = options.type;
			if(self.type=='欧洲'){
				self.beforeName = ['欧洲']
			}else if(self.type=='其他'){
				self.beforeName = ['欧洲','其他']
			};
			//self.$Utils.loadAll(['getAddressData'], self);
		},
		
		methods: {
			
			choose(index){
				const self = this;
				self.chooseIndex = index
			},
			
			confirm(){
				const self = this;
				if(self.chooseIndex>=0){
					uni.setStorageSync('name',self.addressData[self.chooseIndex].title);
					uni.navigateBack({
						delta:1
					})
				}else{
					self.$Utils.showToast('未选择国家','none')
				}
			},
			
			search(){
				const self = this;
				if(self.title!=''){
					self.addressData = []
					self.getAddressData()
				}
			},
			
			getAddressData() {
				const self = this;
				const postData = {};
				postData.searchItem = {
					thirdapp_id: 2,
					title:['LIKE',['%'+self.title+'%']]
				};
				postData.getBefore = {
					article: {
						tableName: 'Label',
						middleKey: 'parentid',
						key: 'id',
						searchItem: {
							title: ['in', self.beforeName],
						},
						condition: 'in'
					}
				};
				const callback = (res) => {
					if (res.info.data.length > 0) {
						self.addressData = res.info.data
					}
					self.$Utils.finishFunc('getGoodsType');
				};
				self.$apis.labelGet(postData, callback);
			},
			
		}
	}
</script>

<style>
.ss input{width: 620rpx;height: 60rpx;border-radius: 30rpx;background-color: #f5f5f5;padding-left: 76rpx;box-sizing: border-box;}
.ss image{position: absolute;width: 36rpx;height: 34rpx;left: 20rpx;top: 13rpx;}

.hot .item{width: 210rpx;height: 70rpx;line-height: 70rpx;}
.btnBox{position: fixed;bottom: 0;left: 0;right: 0;}
</style>
