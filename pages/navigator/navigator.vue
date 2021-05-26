<template>
	<view>
		<view class="top">
			<text selectable>导航跳转</text>
			<text selectable>why cant be selected</text>
		</view>
		<navigator url="../homepage/homepage" open-type="switchTab">homepage</navigator>
		<navigator url="../details/details" open-type="redirect">detail</navigator>
		<navigator url="../details/details">detail without redirect</navigator>
		<button type="default" @click="jumpto(0)">jumpto details</button>
		<button type="default" @click="jumpto(1)">jumpto tabbar</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		},
		methods: {
			jumpto(val) {
				if (val === 0) {
					uni.navigateTo({
						url: '../details/details'
					})
				} else {

					uni.switchTab({
						url: '../homepage/homepage'
					})
				}
			}
		}
	}
</script>

<style lang="scss">
	.top {
		margin-bottom: 20px;
	}
</style>
