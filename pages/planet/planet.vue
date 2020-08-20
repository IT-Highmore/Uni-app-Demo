<template>
	<view>
		<view class="status_bar"><!-- 这里是状态栏 --></view>
		<searchBar></searchBar>
		<view class="swiper">
			<swiper circular autoplay>
				<swiper-item v-for="item in swipers" :key="item.id">
					<image class="swiper-item" :src="item.img"></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="head-group">
			<view v-for="item in classify" :key="item" class='head-classify' :class="{'head-changeTab': showtitle == item}">
				<span @click="changeTab(item)">{{item}}</span>
				<span class='head-setline' :class="{'head-setlinehover': showtitle == item}"></span>
			</view>
		</view>
		
		<view class="content-group">
			<block v-for="(item,index) in showList" :key="index">
				<planet-content :content="item"></planet-content>
				<view style="height: 15rpx;background-color: #F5F5F4;"></view>
			</block>
		</view>
		
	</view>
</template>

<script>
	const recommend = {
		"errcode":0,
		"errinfo":"",
		"data":
		{
			"marks":[0,0],
			"msgs":
			[
				{
					"id":174,
					"author_id":2,
					"author_nickname":"绒猫大侠",
					"author_headicon":{
						"type":1,
						"uri":"../../static/images/user.png"
					},
					"publish_date":"2019-01-28T11:25:20+08:00",
					"view_count":0,
					"acclaim_count":1,
					"comment_count":2,
					"share_count":1,
					"loc_name":"AnyWhere",
					"loc_latitude":1,
					"loc_longitude":2,
					"tags":[
						"小小地球课后班",
						"绘画"
					],
					"units":[
						{
						"type":1,
						"uri":"../../static/images/post/test_post_01.jpg"
						},
						{
						"type":1,
						"uri":"../../static/images/post/test_post_02.jpg"
						},
						{
						"type":0,
						"uri":"test/msg/20190128/798.txt"
						},
						{
						"type":3,
						"uri":"https://img-cdn-qiniu.dcloud.net.cn/uniapp/audio/music.mp3"
						}
					]
				},
				{
					"id":160,
					"author_id":2,
					"author_nickname":"b21234",
					"author_headicon":{
						"type":1,
						"uri":"../../static/images/user.png"
					},
					"publish_date":"2019-01-28T11:24:35+08:00",
					"view_count":0,
					"acclaim_count":1,
					"comment_count":2,
					"share_count":0,
					"loc_name":"AnyWhere",
					"loc_latitude":1,
					"loc_longitude":2,
					"tags":[
						"tagA",
						"tagB"
					],
					"units":[
						{
							"type":1,
							"uri":"../../static/images/post/test_post_02.jpg"
						},
						{
							"type":1,
							"uri":"../../static/images/post/test_post_01.jpg"
						},
						{
							"type":1,
							"uri":"../../static/images/post/test_post_02.jpg"
						},
						{
							"type":1,
							"uri":"../../static/images/post/test_post_01.jpg"
						},
						{
							"type":1,
							"uri":"../../static/images/post/test_post_02.jpg"
						}
					]
				}
			],
			"seq_ids":[500000012,500000007],
			"users_focus":[0,0]
		}
	}
	import searchBar from '@/components/searchBar/searchBar.vue'
	import planetContent from '@/components/common/planet-content.vue'
	export default {
	  components: {searchBar, planetContent},
		data() {
			return {
				swipers: [
					{
						id: 1,
						img: "https://game-1259474362.cos.ap-shanghai.myqcloud.com/miniprogram/images/main_banner_02.jpg"
					},
					{
						id: 2,
						img: "https://game-1259474362.cos.ap-shanghai.myqcloud.com/miniprogram/images/main_banner_01.jpg"
					}
				],
				classify: ["推荐","关注","附近","绘画","书法","棋类"],
				showtitle: '推荐',
				showList: recommend.data.msgs
			}
		},
		onLoad() {
			console.log('首页')
		},
		methods: {
			changeTab (item) {
				if(this.showtitle == item) {
					return
				}
				this.showtitle = item
			},
			async getRecommend() {
				// const res = await this.$myRequest({
				// 	url: '/v1/recommendMsgs'
				// })
				// console.log(res)
			}
		}
	}
</script>

<style lang="scss">
.status_bar {
	height: var(--status-bar-height);
	width: 100%;
}
swiper-item{
  display: flex;
  justify-content: center;
}
.swiper {
	width: 750rpx;
	height: 230rpx;
	margin-top: 100rpx;
	&-item {
		width: 686rpx;
		height: 230rpx;
		background-size: cover;
		border-radius: 14rpx;
	}
}
.head-group{
  margin-left: 32rpx;
  margin-top: 50rpx;
  margin-bottom: 40rpx;
  display: flex;
  justify-content: flex-start;
}
.head {
	&-classify{
		font-size: 36rpx;
		margin-right: 30rpx;
		color: #ccc;
		position: relative;
	},
	&-changeTab{
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

.content-group{
	
}
</style>
