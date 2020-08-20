<!-- 圈子显示组件-->
<template>
	<view>
		<block v-if="data.qzs.length > 0">
			<view v-for="(item,index) in data.qzs" :key="index">
				<group-item :item="item" :job="data.jobs[index]"></group-item>
			</view>
			<image style="width: 686rpx;height: 350rpx;margin: 0 32rpx 20rpx 32rpx;" src="../../static/images/bg_circle_add.png"></image>
    </block>
    <block v-else>
      <view style="color:#ccc">快去选择喜欢的圈子吧！</view>
    </block>
	</view>
</template>

<script>
	import groupItem from '@/components/common/group-item.vue'
	export default {
		components:{groupItem},
		data() {
			return {
				data: {
					"qzs":
					[
						{
							"id":1599081,//圈子ID
							"name":"美华绘画-少儿5岁A班",//圈子名
							"head_img":"../../static/images/post/test_post_01.jpg",//头图
							"type":"a",//圈子类型
							"member_count":1,//成员数量
							"msg_count":0//发文数量
						},
						{
							"id":1599079,
							"name":"培优围棋-少儿五岁",
							"head_img":"../../static/images/post/test_post_01.jpg",
							"type":"",
							"member_count":1,
							"msg_count":0
						}
					],
					"seq_ids":[1599081,1599079],
					"jobs":[//成员职位类型见通用定义
						3,2]
				}
			}
		},
		onLoad() {
			//获取用户加入的圈子列表 15.10 userQZs
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
