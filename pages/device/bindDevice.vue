<template>
	<view class="bind-device">
		<view class="bind-device-tit">请输入序列号：</view>
		<input class="bind-device-input flex-center" type="number" :value="serialNumber" />
		<view class="submit-btn">
			<button @click="toPage('deviceList')">确定</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				serialNumber: null
			}
		},
		onLoad() {

		},
		methods: {
			toPage(page){
				uni.hideKeyboard()
				uni.navigateTo({
					url: page
				});
			},
		}
	}
</script>

<style lang="scss">
	.bind-device{
		padding: 50upx;
		.bind-device-tit{
			line-height: 120upx;
			color: $uni-text-color-grey;
		}
		.bind-device-input{
			padding: 20upx 10upx;
			font-size: $uni-font-size-lg1;
			border: 1px solid $uni-border-color;
			border-radius: $uni-border-radius-base;
			background: $uni-bg-color;
		}
	}
</style>
