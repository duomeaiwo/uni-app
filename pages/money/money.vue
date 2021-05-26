<template>
	<view>
		<view>rpx</view>
		<view class="box">
			{{msg}}
			<view class="iconfont icon-jiagezixun">
				<button type="default" @click="pulldown">refresh</button>
			</view>
		</view>
		<view v-for="item in list" class="item">
			{{item}}
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				msg: 'xxx',
				list: [
					'apple', 'orange', 'pineapple', 'watermelon', 'banana', 'lemon'
				]
			};
		},
		onPullDownRefresh() {
			this.msg = 'aaa'
			uni.stopPullDownRefresh()
		},
		onReachBottom() {
			console.log('xx')
			this.list = [...this.list,
				'apple', 'orange', 'pineapple', 'watermelon', 'banana', 'lemon'
			]
		},
		methods: {
			pulldown() {
				uni.startPullDownRefresh()
			}
		}
	}
</script>

<style lang="scss">
	.box {
		width: 375rpx;
		height: 375rpx;
		color: $uni-color-error;
		font-size: 75rpx;
		background-color: #4CD964;
	}

	.item {
		height: 100px;
		line-height: 100px;
	}
</style>
