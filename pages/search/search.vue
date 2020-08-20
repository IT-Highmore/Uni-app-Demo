<template>
	<view>
		<!-- 搜索条 -->
		<view class="searchTopBox">
			<view class="searchBoxRadius">
				<input class="searchBoxIpt" type="search" v-model="ipt" @confirm="searchNow($event)" placeholder="点击输入搜索词"></input>
			</view>
		</view>
		<!-- 搜索历史 -->
		<template v-if="searchList.length === 0">
			<view class="searchBotBox">
				<view class="ov">
					<view class="fl">搜索历史</view>
					<uni-icons @tap="clearKey" style="line-height: 32rpx;"  type="trash" size="18"></uni-icons>
				</view>
				<view class="searchHistoryBox">
					<view class="searchHistoryBoxItem" v-for="(item,index) in searchKey" :key="index" @click="tapSearchHistory(item)">
						{{item}}
					</view>
				</view>
			</view>
			<view class="searchBotBox">
				<view class="ov">
					<view class="fl">大家都在看</view>
				</view>
				<view class="searchHistoryBox">
					<view class="searchHistoryBoxItem" v-for="(item,index) in recommendKey" :key="index" @click="tapSearchHistory(item)">
						{{item}}
					</view>
				</view>
			</view>
		</template>
		<!-- 搜索结果 -->
		<template v-else>
			<view style="display: flex;margin-left: 32rpx;">
				<view class="unselect" :class="{'select': searchTab == 0}" @click="tapSearchTab(0)">内容 999+</view>
				<view style="color: #ccc;margin-right: 20rpx;">|</view>
				<view class="unselect" :class="{'select': searchTab == 1}" @click="tapSearchTab(1)">用户 819</view>
				<view style="color: #ccc;margin-right: 20rpx;">|</view>
				<view class="unselect" :class="{'select': searchTab == 2}" @click="tapSearchTab(2)">圈子 7</view>
			</view>
			<block v-if="searchTab == 0">
				<block v-for="(item,index) in searchList" :key="index">
					<planet-content :content="item"></planet-content>
				</block>
			</block>
			<block v-else-if="searchTab == 1">
				<block v-for="(item,index) in searchList" :key="index">
					<search-user :content="item"></search-user>
				</block>
			</block>
			<block v-else>
				<block v-for="(item,index) in searchList" :key="index">
					<search-quanzi :content="item"></search-quanzi>
				</block>
			</block>
		</template>
	</view>
</template>
<script>
	import planetContent from '@/components/common/planet-content.vue'
	import searchQuanzi from '@/components/common/search-quanzi.vue'
	import searchUser from '@/components/common/search-user.vue'
	const demo = [
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
	]
	const demo1 = [{name: '旅行用的小皮洗脸盆',focus_count:0,img:'../../static/images/user.png'},{name: '旅行用的小皮洗脸盆',focus_count:50,img:'../../static/images/user.png'},{name: '旅行用的小皮洗脸盆',focus_count:70,img:'../../static/images/user.png'}]
	const demo2 = [{name: '小小地球2019美术班',img:'../../static/images/user.png',person_count:27,content_count:20},{name: '小小地球2019美术班',img:'../../static/images/user.png',person_count:27,content_count:20},{name: '小小地球2019美术班',img:'../../static/images/user.png',person_count:27,content_count:20}]
	export default {
		components:{planetContent,searchQuanzi,searchUser},
		data() {
			return {
				searchKey:[],
				recommendKey:['油画','音乐','舞蹈','诗词','英语','优惠活动折扣','培训机构名单','数学','语文','手工活动'],
				ipt: '',
				searchClose: true,
				searchList:[],
				searchTab: 0
			}
		},
		onShow() {
			var vv = uni.getStorageSync('searchLocal');
			var arr = vv.split("-");
			this.searchKey = arr;
		},
		methods: {
			// 点击搜索标签
			tapSearchTab(index){
				this.searchTab = index
				if(index == 0) {
					this.searchList = demo
				} else if(index == 1) {
					this.searchList = demo1
				}else{
					this.searchList = demo2
				}
			},
			// 点击搜索历史
			tapSearchHistory(text) {
				this.ipt = text
				this.searchNow()
			},
			// 清除搜索历史
			clearKey() {
				var that = this;
				uni.showModal({
					title: '提示',
					content: '点击确定将删除所有历史信息，确定删除吗？',
					success: function(res) {
						if (res.confirm) {
							that.searchKey = [];
							uni.setStorage({
								key: 'searchLocal',
								data: that.searchKey
							});
						} else if (res.cancel) {
						}
					}
				});

			},
			searchNow() {
				if (this.ipt == '') {
					uni.showToast({
						title: '未输入搜索关键字',
						icon: 'none',
						duration: 1000
					});
					return false;
				}
				// 显示loading状态
				uni.showLoading({
					title: '加载中...',
					mask: false
				});
				
				let newData = true;
				console.log(this.searchKey)
				for(let i = 0; i < this.searchKey.length;i++) {
					let item = this.searchKey[i]
					if(item === this.ipt) {
						newData = false;
						break
					}
				}
				
				if(newData) {
					// 加入历史记录
					var newArr = this.searchKey;
					newArr.push(this.ipt);
					this.searchKey = newArr;
					// 存储到本地缓存
					var newStr = newArr.join('-');
					console.log(newStr)
					uni.setStorage({
						key: 'searchLocal',
						data: newStr
					});
				}
				
				// 请求搜索
				setTimeout(()=> {
					this.searchList = demo
					uni.hideLoading()
				},2000)
			
			}
		}
	}
</script>
<style>
	page {
		background: #FFF;
	}
	.unselect {
		color: #ccc;
		margin-right: 20rpx;
	}
	.select{
		color: #000000;
	}
	.ov {
		overflow: hidden;
		display: flex;
		width: 686rpx;
		justify-content: space-between;
	}

	.fl {
		line-height: 32rpx;
		float: left;
		font-weight: bold;
	}

	.fr {
		float: right;
	}

	.searchTopBox {
		margin: 30rpx 32rpx;
		width:686rpx;
		height: 70rpx;
		box-sizing: border-box;
	}

	.searchBoxRadius {
		width: 100%;
		height:70rpx;
		border-bottom: 3px solid #000000;
		overflow: hidden;
	}

	.searchBoxIpt {
		height: 70rpx;
		line-height: 70rpx;
		float: left;
	}

	.searchBotBox {
		width: 100%;
		margin: 30rpx 32rpx;
		box-sizing: border-box;
	}

	.searchHistoryBox {
		width: 686rpx;
		box-sizing: border-box;
		overflow: hidden;
		margin-top: 30rpx;
	}

	.searchHistoryBoxItem {
		float: left;
		font-size: 26rpx;
		color: #666;
		line-height: 46rpx;
		height: 46rpx;
		padding: 0 20rpx;
		border-radius: 10rpx;
		margin-right: 15rpx;
		margin-bottom: 20rpx;
		border: 1px solid #ccc;
	}
</style>
