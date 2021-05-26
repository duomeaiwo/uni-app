<template>
	<view class="content">
		<button type="default" @click="getData">getData</button>
		<button type="default" @click="setStorage">setStorage</button>
		<button type="default" @click="getStorage">getStorage</button>
		<button type="default" @click="removeStorage">removeStorage</button>
		<button type="default" @click="uploadPic">上传图片</button>
		<button type="default" @click="clearPic">清空图片</button>
		<view >
			<image v-for="item in imgSrc" :src="item" @click="previewImg(item)" mode="aspectFit"></image>
		</view>
		<!-- #ifdef H5 -->
		<view class="text">仅在h5中可见</view>
		<!-- #endif -->
		<!-- #ifdef MP-WEIXIN -->
		<view class="text">仅在微信小程序中可见</view>
		<!-- #endif -->
		<navigator url="../navigator/navigator">导航页</navigator>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgSrc: []
			}
		},
		onLoad() {
		// #ifndef H5
			console.log('inndef h5 onLoad')
		// #endif
		},
		methods: {
			getData() {
				uni.request({
					url: 'https://api-hmugo-web.itheima.net/api/public/v1/home/swiperdata',
					success: (res) => {
						console.log(res)
					}
				})
			},
			setStorage() {
				uni.setStorageSync('storage_key', 'hello')
			},
			getStorage() {
				const value = uni.getStorageSync('storage_key')
				console.log(value)
			},
			removeStorage() {
				uni.removeStorageSync('storage_key')
			},
			uploadPic() {
				uni.chooseImage({
					count: 6,
					sizeType: ["original", "compressed"],
					success: (res) => {
						console.log(res)
						this.imgSrc = res.tempFilePaths
					}
				})
			},
			clearPic() {
				this.imgSrc = []
			},
			previewImg(current) {
				uni.previewImage({
					current,
					urls: this.imgSrc
				})
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	/* #ifdef H5 */
	.text {
		color: hotpink;
	}
	/* #endif */
	/* #ifndef H5 */
	.text {
		color: #2C405A;
	}
	/* #endif */
</style>
