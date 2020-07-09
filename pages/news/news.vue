<template>
	<view>
		
		<view class="news mx-2">
			<view class="item position-relative d-flex borderT-e1 py-3"
				v-for="(item,index) in mainData" :key="index" :data-id="item.id"
				 @click="Router.navigateTo({route:{path:'/pages/newsDetails/newsDetails?id='+$event.currentTarget.dataset.id}})">
				<image :src="item.mainImg&&item.mainImg[0]?item.mainImg[0].url:''" mode=""></image>
				<view class="d-flex flex-column j-sb h-100 ml-2 txt">
					<view class="font-28 color2 avoidOverflow2">{{item.title}}</view>
					<view class="font-24 color6">{{item.description}} | {{item.create_time}}</view>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		
		data() {
			return {
				Router:this.$Router,
				mainData:[]
			}
		},
		
		onLoad() {
			const self = this;
			self.paginate = self.$Utils.cloneForm(self.$AssetsConfig.paginate);
			self.$Utils.loadAll(['getMainData'], self);
		},
		
		onReachBottom() {
			console.log('onReachBottom')
			const self = this;
			if (!self.isLoadAll && uni.getStorageSync('loadAllArray')) {
				self.paginate.currentPage++;
				self.getMainData()
			};
		},
		
		methods: {
			
			getMainData(isNew) {
				const self = this;
				if (isNew) {
					self.mainData = [];
					self.paginate = {
						count: 0,
						currentPage: 1,
						is_page: true,
						pagesize: 10
					}
				};
				const postData = {};
				postData.paginate = self.$Utils.cloneForm(self.paginate);
				postData.searchItem = {
					thirdapp_id: 2,
					type:2
				};
				const callback = (res) => {
					if (res.info.data.length > 0) {
						self.mainData.push.apply(self.mainData, res.info.data)
					};
					self.$Utils.finishFunc('getMainData');
				};
				self.$apis.articleGet(postData, callback);
			},
			
		}
	}
</script>

<style>
.news .item{height: 140rpx;box-sizing: content-box;}
.news .item:nth-child(1){border: none;}
.news image{width: 200rpx;height: 140rpx;border-radius: 8rpx;}
.news .item .txt{width: 450rpx;}
</style>
