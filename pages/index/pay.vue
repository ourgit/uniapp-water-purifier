<template>
	<view class="pay">
		<view class="pay-money">
			<text>￥</text>
			<text class="uni-h1">672.00</text>
		</view>
		<view class="pay-select">
			<view class="pay-select-item flex-center-between">
				<text>收款方</text>
				<view class="payee">立升云租赁</view>
			</view>
			<view class="pay-select-item flex-center-between">
				<text>是否开具发票</text>
				<view class="invoice">
					<text>电子发票（企业）</text>
					<uni-icon type="arrowright" color="#999" size="20"></uni-icon>
				</view>
				
			</view>
			<view class="pay-select-item flex-center-between">
				<text>是否签订合同</text>
				<view class="agreement">
					<text>是</text>
					<uni-icon type="arrowright" color="#999" size="20"></uni-icon>
				</view>
			</view>
		</view>
		<view class="submit-btn">
			<button class="btn">立即支付</button>
		</view>
	</view>
</template>

<script>
	import uniIcon from "@/components/uni-icon.vue"
	export default {
		components: {
			uniIcon,
		},
		data() {
			return {
				
			}
		},
		onLoad() {

		},
		methods: {
			
			pageTo() {
				// uni.navigateTo({
				// 	url: 'index'
				// });
			},
			
		}
	}
</script>

<style lang="scss">
	.pay{
		background: $uni-bg-color;
		.pay-money{
			height: 400upx;
			line-height: 400upx;
			text-align: center;
		}
		
		.pay-select{
			padding: 0 30upx;
			&-item{
				height: 110upx;
				border-bottom: 1px solid $uni-border-color;
				&:last-child{
					border-bottom: none;
				}
			}
		}
		
		.submit-btn{
			position: fixed;
			bottom: 0;
			left: 0;
			right: 0;
			padding: 0 30upx;
		}
	}
</style>
