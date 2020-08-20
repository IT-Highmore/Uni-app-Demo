<template>
	<view>
		<!--文本域-->
		<textarea v-model="content" placeholder="精彩内容投出来~" class="uni-textarea" style="padding: 32rpx;"/>
		<!--多图上传-->
		<upload-image @change="changeImage"></upload-image>
		<!--底部操作条-->
		<view class="fixed-bottom">
			<uni-icons class="type-icon" type="image" size="20"></uni-icons>
			<uni-icons class="type-icon" type="mic" size="20"></uni-icons>
			<uni-icons class="type-icon" type="videocam" size="20"></uni-icons>
			<view class="button-release">发布</view>
		</view>
	</view>
</template>

<script>
	import uploadImage from "@/components/common/upload-image.vue"
	export default {
		components:{uploadImage},
		data() {
			return {
				content: '',
				imageList:[]
			}
		},
		methods: {
			changeImage(e) {
				this.imageList = e
			}
		}
	}
</script>

<style lang="scss">
.fixed-bottom {
	position: fixed;
	right: 0;
	bottom: 0;
	left: 0;
	z-index: 1030;
	background-color: #FFFFFF;
	height: 85rpx;
	display: flex;
	align-items: center;
}
.type-icon {
	width: 86rpx;
	height: 86rpx;
	display: flex;
	justify-content: center;
	align-items: center;
}
.button-release {
	width: 140rpx;
	height: 60rpx;
	margin-left: auto;
	color: #FFFFFF;
	text-align: center;
	line-height: 60rpx;
	margin-right: 20rpx;
	border-radius: 8rpx;
	background-color: #FFCA34;
}
</style>
