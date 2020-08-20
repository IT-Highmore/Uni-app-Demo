<template>
	<view class="find">
		<view class="find-head">
			<text>找兴趣</text>
			<text style="font-size: 20rpx;color: #ccc;">查看全部 ></text>
		</view>
		<view class="find-interest">
			<view style="display: flex;flex-direction: column;" v-for="(item,index) in interest" :key="index">
				<image style="width: 90rpx;height: 90rpx;" :src="item.img"></image>
				<text style="text-align: center;color: #ccc;font-size: 20rpx;">{{item.name}}</text>
			</view>
		</view>
		<view class="find-title">
			<view v-for="item in title" :key="item" class='head-classify' :class="{'head-selectTitle': showtitle == item}">
				<span @click="selectTitle(item)">{{item}}</span>
				<span class='head-setline' :class="{'head-setlinehover': showtitle == item}"></span>
			</view>
		</view>
		<view class="find-item">
			<block v-for="(item,index) in about" :key="index">
				<find-item :about="item"></find-item>
			</block>
		</view>
	</view>
</template>

<script>
	import findItem from "@/components/common/find-item.vue"
	export default {
		components:{findItem},
		data() {
			return {
				interest:[
					{
						name: '英语',
						img: '../../static/images/user.png'
					},{
						name: '阅读',
						img: '../../static/images/user.png'
					},{
						name: '亲自',
						img: '../../static/images/user.png'
					},{
						name: '绘画',
						img: '../../static/images/user.png'
					},{
						name: '手办',
						img: '../../static/images/user.png'
					},{
						name: '手工',
						img: '../../static/images/user.png'
					}
				],
				title:['附近','明星圈榜','明星宝贝榜'],
				showtitle: '附近',
				about:[
					{
						name: '布偶娃娃手工制作',
						status:'明星榜排名第一',
						people: 5,
						content: 20,
						img1: '../../static/images/post/test_post_02.jpg',
						img2: '../../static/images/post/test_post_01.jpg',
						img3: '../../static/images/post/test_post_02.jpg'
					},{
						name: '二次元精美手绘',
						status:'明星榜排名第二',
						people: 25,
						content: 135,
						img1: '../../static/images/post/test_post_02.jpg',
						img2: '../../static/images/post/test_post_01.jpg',
						img3: '../../static/images/post/test_post_02.jpg'
					},{
						name: '卡哇伊少女风涂鸦',
						status:'',
						people: 28,
						content: 98,
						img1: '../../static/images/post/test_post_02.jpg',
						img2: '../../static/images/post/test_post_01.jpg',
						img3: '../../static/images/post/test_post_02.jpg'
					},
				]
			}
		},
		methods: {
			selectTitle (item) {
				this.showtitle = item
			},
		}
	}
</script>

<style lang="scss">
.find{
	margin: 0 32rpx;
	&-head {
		margin: 20rpx 0;
		display: flex;
		justify-content: space-between;
		text:first-child {
			font-weight: bold;
		}
	}
}
.find-interest {
	display: flex;
	justify-content: space-between;
}
.find-title {
	margin-top: 30rpx;
	display: flex;
	justify-content: flex-start;
}
.find-item {
	margin-top: 50rpx;
}
.head {
	&-classify{
		font-size: 36rpx;
		margin-right: 30rpx;
		color: #ccc;
		position: relative;
	},
	&-selectTitle{
		color: #000;
	},
	&-setline{
		height: 6rpx;
		width: 30rpx;
		position: absolute;
		bottom: -14rpx;
		left: 25rpx;
	},
	&-setlinehover{
		border: 1rpx #000 solid;
		border-radius: 14rpx;
		background-color: #000;
	}
}
</style>
