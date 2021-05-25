<template>
	<view class="trip">
		<view class="box" hover-class="box-active" hover-stop-propagation :hover-start-time="100" :hover-stay-time="1000">
			<text selectable>this is detail page</text>
		</view>
		<view >
			<text selectable="true" space="emsp">可被  选中</text>
		</view>
		<button type="default" size="mini" plain>click</button>
		<button type="primary" size="default" >click</button>
		<button type="warn" size="default"  loading>click</button>
		<button type="warn" size="default"  disabled>click</button>
		<image src="../../static/mixkit-i-love-you-hand-gesture-419-original.png" ></image>
		<image src="../../static/mixkit-i-love-you-hand-gesture-419-original.png" mode="aspectFit"></image>
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

<style>
	.box {
		width: 100px;
		height: 100px;
		background-color: green;
	}
	.box-active {
		width: 100%;
		height: 100px;
		background-color: skyblue;
	}
</style>
