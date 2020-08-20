<!-- 星球发布内容页-->
<template>
	<view>
		<view class="content-group"  @click.stop="openDetailPage">
			<view class="content-head">
				<image class="userinfo-avatar" :src="content.author_headicon.uri" lazy-load></image>
				<view class="userinfo-title">
					<text class="userinfo-name">{{content.author_nickname}}</text>
					<text class="userinfo-time">{{content.publish_date}}</text>
				</view>
			</view>
			<view class="content-img">
				<view v-for="image in images" :key="image">
					<view class="content-img-item" :style="{'backgroundImage':'url(' + image.uri + ')'}"></view>
				</view>
			</view>
			<view class="content-text">
				<view class="info">
					<view :class="{hide:!iSinfo}">{{txt}}</view>
					<text @click="showinfo" v-if="!iSinfo">展开</text>
				</view>
				<text @click="showinfo" v-if="iSinfo" class="hidebtn">收起</text>
			</view>
			<view class="content-audio">
				<audio style="text-align: left" :author="sound.author" :src="sound.src" :name="sound.name" controls></audio>
			</view>
			<view class="content-class">
				<image src="../../static/icons/sign_circle.png"></image>
				<text>来自班级：小小地球2019美术班</text>
			</view>
			<view class="content-tag">
				<view v-for="(item,index) in content.tags" :key="index">
					<text>{{item}}</text>
				</view>
			</view>
		</view>
		<planet-comment :content="content"></planet-comment>
	</view>
</template>

<script>
	import planetComment from './planet-comment.vue'
	export default {
		components:{planetComment},
		props:{
			content : Object
		},
		data() {
			return {
				images:[],
				iSinfo: false,
				txt: '此处为文字内容局域，当文字内容超过5行以上时，@小火箭 @小怪豆 下面将会出现下拉全显示剪头，点击可以直接进入此信息的主界面。当图片很多时，一排显示三个，最多显示9个方框这种，左对齐当图片很多多多多多时，一排显示三个，最多显示9个方框这种，左对齐。',
				sound: {
					post: '',
					name:  '致爱丽丝',
					author: '绒猫大侠',
					src: ''
				}
			}
		},
		watch:{
			content(val) {
				console,log(val)
				// 有变化就会监听
			}
		},
		computed: {
			setImage() {
				let images = [],num = 0
				let units= this.content.units
				units.forEach(item => {
					if(item.type == 1) {
						images.push(item)
						num++
					}
				})
				if(num % 3 == 2) {
					images.push({
						type: 1,
						uri: ''
						})
				}
				this.images = images
			},
			readFile() {
				// 将txt文件转换为文本
			},
			selectAudio() {
				let units= this.content.units
				units.forEach(item => {
					if(item.type == 3) {
						this.sound.src = item.uri
					}
				})
			}
		},
		methods: {
			openDetailPage() {
				// console.log('详情页')
				// uni.navigateTo({
				// 	url: '../../pages/planet/detail'
				// })
			},
			showinfo() {
				this.iSinfo = !this.iSinfo
			}
		}
	}
</script>

<style lang="scss">
.content {
	&-group {
		background-color: #FFFFFF;
		margin-left: 32rpx;
		margin-right: 32rpx;
	},
	&-head {
		display: flex;
		align-items: center;
	},
	&-img {
		margin-top: 20rpx;
		display: flex;
		justify-content: space-between;
		flex-wrap: wrap;
		&-item {
			width: 220rpx;
			height: 220rpx;
			border-radius: 24rpx;
			margin-bottom: 10rpx;
			background-size: cover;
			background-position: center center;
		}
	},
	&-text {
		margin-top: 20rpx;
		display: flex;
		flex-direction: column;
		background-color: #fff;
		// padding: 30rpx;
		position: relative;
	},
	&-audio{
		margin-bottom: 20rpx;
		height: 134rpx;
	},
	&-class {
		border: 1px solid #ccc;
		border-radius: 20rpx;
		height: 40rpx;
		display: flex;
		align-items: center;
		width: 405rpx;
		image{
			width: 32rpx;
			height: 32rpx;
			margin-right: 10rpx;
			margin-left: 10rpx;
		}
		text{
			font-size: 24rpx;
			line-height: 40rpx;
			font-weight: bold;
		}
	},
	&-tag {
		display: flex;
		text{
			border-radius: 30rpx;
			border: 1px solid #F5F5F5;
			padding: 4rpx 10rpx;
			margin-right: 10rpx;
			color: #494949;
			font-size: 20rpx;
		}
	}
}
.userinfo {
	&-avatar {
		width: 100rpx;
		height: 100rpx;
		background-size: cover;
		border-radius: 100%;
		margin-top: 12rpx;
	},
	&-title {
		display: flex;
		flex-direction: column;
		margin-left: 20rpx;
	},
	&-name {
		margin-top: 20rpx;
		font-weight: bold;
		height: 50rpx;
	},
	&-time {
		color: #C1C1C1;
	}
}
.info {
	display: flex;
	flex-direction: column;
	view {
		font-size: 14px;
		color: rgba(102, 102, 102, 1);
		word-break: break-word; //换行模式
		background-color: #fff;
	}
	text {
		width: 686rpx;
		background-color: #FFFFFF;
		font-size: 14px;
		display: flex;
		justify-content: flex-start;
		align-items: center;
		color: #ccc;
		position: absolute;
		bottom: 0rpx;
	}
}
.hidebtn {
	display: flex;
	flex: 1;
	justify-content: flex-start;
	color: #ccc;
	font-size: 14px;
}
.hide {
	word-break: break-word; //换行模式
	overflow: hidden;
	text-overflow: ellipsis; //修剪文字
	display: -webkit-box;
	-webkit-line-clamp: 5; //此处为上限行数
	-webkit-box-orient: vertical;
}
</style>
