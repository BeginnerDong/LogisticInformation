<template>
	<view>
		
		<view class="font-40 color2 mx-2 pt-4">{{mainData.title}}</view>
		<view class="d-flex a-end mx-2 pt-3 pb-5">
			<view class="font-28 colorB pr-2">{{mainData.description}}</view>
			<view class="font-26 color9">{{mainData.create_time}}</view>
		</view>
		
		<view class="mx-2 newsCon pb-5">
			<view class="content ql-editor" style="padding:0;" v-html="mainData.content">
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				searchItem:{
					thirdapp_id:2
				},
				mainData:{}
			}
		},
		
		onLoad(options) {
			const self = this;
			if (options.id) {
				self.searchItem.id = options.id
			};
			self.$Utils.loadAll(['getMainData'], self);
		},
		
		methods: {
			
			
			
			getMainData() {
				const self = this;
				const postData = {};
				postData.searchItem = self.$Utils.cloneForm(self.searchItem);
				const callback = (res) => {
					if (res.info.data.length > 0) {
						self.mainData = res.info.data[0];
						const regex = new RegExp('<img', 'gi');
						self.mainData.content = self.mainData.content.replace(regex, `<img style="max-width: 100%;"`);
					};
					self.$Utils.finishFunc('getMainData');
				};
				self.$apis.articleGet(postData, callback);
			},
			
		}
	}
</script>

<style>
.newsCon image{width: 710rpx;height: 400rpx;}
</style>
