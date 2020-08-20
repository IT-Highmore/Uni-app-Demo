<!-- 星球发布评论-->
<template>
	<view class="comment">
		<view class="comment-left">
			<view class="comment-left-item animate__jello" :hover-class="animate__jello">
				<image class="animate pl" src="../../static/icons/icon_comment_fav_01.png"></image>
				<text>{{content.view_count}}</text>
			</view>
			<view class="comment-left-item animate__bounce">
				<image src="../../static/icons/icon_comment_comment.png"></image>
				<text>{{content.comment_count}}</text>
			</view>
			<view class="comment-left-item">
				<image src="../../static/icons/icon_comment_thumbsup_01.png"></image>
				<text>{{content.acclaim_count}}</text>
			</view>
		</view>
		<view class="comment-right">
			<image src="../../static/icons/icon_comment_share.png"></image>
			<text>{{content.share_count}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			content: Object
		}
	}
</script>

<style lang="scss">
.comment {
		display: flex;
		align-items: center;
		margin: 20rpx 32rpx 20rpx 32rpx;
		height: 40rpx;
		&-left {
			display: flex;
			align-items: center;
			margin-right: 150rpx;
			&-item {
				width: 150rpx;
				height: 40rpx;
				display: flex;
				align-items: center;
				image {
					width: 40rpx;
					height: 40rpx;
					margin-right: 20rpx;
				}
				text {
					line-height: 40rpx;
				}
			}
		},
		&-right {
			display: flex;
			align-items: center;
			image {
				width: 40rpx;
				height: 40rpx;
				margin-right: 20rpx;
			},
			text {
				line-height: 40rpx;
			}
		}
	}
</style>
