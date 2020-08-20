<template>
	<view class="searchbar">
		<navigator class="search-navigator" url="../../pages/search/search">
			<text class="search-title">小怪豆</text>
			<uni-icons style="margin: 10rpx 10rpx 0 30rpx;line-height: 64rpx;"  type="search" size="12"></uni-icons>
			<!-- <image src="../../static/icons/icon_search.png" style="margin: 0rpx 10rpx 0 50rpx;"></image> -->
			<text class="search-text">搜索宝宝作品</text>
		</navigator>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">
.searchbar {
  margin-left: 32rpx;
  position: absolute;
  width: 100%;
}
.search-navigator {
  width: 65%;
  height: 64rpx;
  background-color: #F1F1F1;
  border-radius: 24rpx;
 }
 .search-title{
	 margin-left: 20rpx;
	font-size: 32rpx;
	font-weight: 500;
	line-height: 64rpx;
 }
 
 .search-text{
	 font-size: 24rpx;
	 color: #C0C0C0;
	 line-height: 64rpx;
 }
</style>