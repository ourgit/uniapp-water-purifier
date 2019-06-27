<template>
	<view class="content">
		<view class="banner">
			<image class="banner-center" src="../../static/images/device-mobile.png" mode="aspectFill"></image>
			<view class="circle circle-one"></view>
			<view class="circle circle-two"></view>
		</view>
		<view class="arc"></view>
		<view class="add-device">
			<view class="uni-h4">请添加设备</view>
			<view class="add-device-desc">开启立升智能净水生活</view>
			<button class="add-device-btn" @click="onAddDevice('bindDevice')">立即添加</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
			}
		},
		onLoad() {

		},
		methods: {
			onAddDevice(page){
				uni.showActionSheet({
					itemList: ['扫一扫', '输入序列号'],
					success: function (res) {
						if(res.tapIndex === 0) {
							uni.scanCode({
								success: function (res) {
									console.log('条码类型：' + res.scanType);
									console.log('条码内容：' + res.result);
								}
							});
						} else {
							uni.navigateTo({
								url: page
							});
						}
					},
					fail: function (res) {
						alert(res.errMsg);
					}
				});
			}

		}
	}
</script>

<style lang="scss">
	.banner{
		height:450upx;
		width: 100%;
		background: #19a4af;
        position: relative;
		.banner-center{
			position: absolute;
			width: 188upx;
			height: 348upx;
			left: 50%;
			top: 168upx;
			transform: translateX(-50%);
			z-index: 2;
		}
		.circle{
			width: 200upx;
			height: 200upx;
			position: absolute;
			left: 50%;
			top: 230upx;
			margin-left: -100upx;
			border-radius: 50%;
			z-index: 1;
		}
		.circle-one{
			background-color: #4ab7c0;
			animation: click1 2s linear infinite; 
		}
		.circle-two{
			background-color: #36afb9;
			animation: click2 2s linear infinite; 
		}
		@keyframes click1 {
			0% {
				opacity: .8;
				-webkit-transform: scale(1);
				transform: scale(1);
			}
			100% {
				opacity: 0;
				-webkit-transform: scale(2);
				transform: scale(2);
			}
		}
		@keyframes click2 {
			0% {
				opacity: .8;
				-webkit-transform: scale(1);
				transform: scale(1);
			}
			100% {
				opacity: 0;
				-webkit-transform: scale(3);
				transform: scale(3);
			}
		}
	}
	.arc{
		height: 200upx;
		border-radius: 0 0 100% 100%;
		background: #19a4af;
	}
	.add-device{
		text-align: center;
		margin-top: 100upx;
		.add-device-desc{
			line-height: 60upx;
			font-size: $uni-font-size-sm2;
			color: $uni-text-color-grey;
		}
		.add-device-btn{
			margin: 90upx auto 0;
			width: 316upx;
			height: 90upx;
			border-radius: 45px;
			line-height: 90upx;
			font-size: $uni-font-size-lg;
			background: $uni-text-color-theme;
			color: $uni-text-color-inverse;
		}
	}
</style>
