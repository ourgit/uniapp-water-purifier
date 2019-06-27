<template>
	<view class="order-confirm">
		<view class="select-address flex-center-between">
			<image class="select-address-img" src="../../static/images/order-location.png" mode="aspectFill"></image>
			<view class="select-address-info">
				<view>
					<text class="select-address-info-name">张女士</text>
					<text class="select-address-info-mobile">13787889209</text>
				</view>
				<view class="select-address-info-address text-overflow-two">
					广东省深圳市南山区塘朗地铁站南山智园A3
				</view>
			</view>
			<uni-icon type="arrowright" color="#999" size="20"></uni-icon>
		</view>
		
		<view class="select-goods">
			<view class="flex-center">
				<image class="select-goods-img" src="../../static/images/img01.png" mode=""></image>
				<view class="select-goods-info">
					<view class="select-goods-info-name text-overflow-two">
						立升净水器家用全屋中央大流量超滤膜直饮机大流量
					</view>
					<view class="select-goods-info-type text-overflow-one">
						型号：LA2-1V02-PCRCUC
					</view>
					<view class="select-goods-info-daterange">
						使用时长：2019.05.24-2020.05.24
					</view>
				</view>
			</view>
			<view class="select-goods-number flex-center-between">
				<text>购买数量</text>
				<uni-number-box min="1" max="10" :value="1"></uni-number-box>
			</view>
			<view class="select-goods-price flex-center-between">
				<view class="price">
					<view>
						<text>维护费：</text>
						<text class="color-important">¥740</text>
					</view>
					<view>
						<text>租赁费：</text>
						<text class="color-important">¥3180</text>
					</view>
				</view>
				<text>
					<text>小计：</text>
					<text class="color-important">¥3920</text>
				</text>
			</view>
		</view>
		
		<view class="ticket-code">
			<view class="ticket-code-item flex-center-between">
				<text>优惠券</text>
				<view>
					<text class="ticket">-¥100</text>
					<uni-icon type="arrowright" color="#999" size="20"></uni-icon>
				</view>
			</view>
			<view class="ticket-code-item flex-center-between">
				<text class="code">推荐码</text>
				<text>45654545</text>
			</view>
		</view>
		
		<view class="select-pay">
			<view class="select-pay-tit">
				支付方式
			</view>
			<view class="select-pay-list">
				<radio-group @change="payTypeChange">
					<label class="select-pay-list-item flex-center-between" v-for="(item, index) in payTypeList" :key="index">
						<view class="flex-center">
							<image class="select-pay-list-item-img" :src="item.img" mode="aspectFill"></image>
							<text>{{item.name}}</text>
						</view>
						<radio :value="item.name" :checked="index === curPayType" />
					</label>
				</radio-group>
			</view>
		</view>
		
		<view class="agreement">
			<label>
				<checkbox :checked="agree" />我已阅读并同意《服务协议》
			</label>
		</view>
		
		<view class="order-submit flex-center-between">
			<view class="order-submit-price">
				<text>合计</text> 
				<text class="text-color-important">
					<text>￥</text>
					<text class="font-size-lg">3180</text>
				</text>
			</view>
			<view class="order-submit-confirm" @click="pageTo('pay')">提交订单</view>
		</view>
	</view>
</template>

<script>
	import uniNumberBox from "@/components/uni-number-box.vue"
	import uniIcon from "@/components/uni-icon.vue"
	export default {
		components: {
			uniNumberBox,
			uniIcon,
		},
		data() {
			return {
				curPayType: 0,
				payTypeList: [
					{
						name: '微信支付',
						img: '../../static/images/order-pay-wechat.png'
					},
					{
						name: '支付宝支付',
						img: '../../static/images/order-pay-ali.png'
					},
					{
						name: '对公转账',
						img: '../../static/images/order-pay-company.png'
					},
					{
						name: '他人代付',
						img: '../../static/images/order-pay-others.png'
					}
				],
				agree: false
			}
		},
		onLoad() {

		},
		methods: {
			payTypeChange() {
				
			},
			pageTo(page) {
				uni.navigateTo({
					url: page
				});
			},
			
		}
	}
</script>

<style lang="scss">
	.order-confirm{
		margin-bottom: 30upx;
		.select-address{
			box-sizing: border-box;
			width: 690upx;
			height: 185upx;
			margin: 30upx;
			padding: 0 20upx;
			background: $uni-bg-color;
			border-radius: $uni-border-radius-base;
			&-info{
				margin: 0 30upx;
				&-mobile{
					margin-left: 20upx;
					color: $uni-text-color-grey;
					font-size: $uni-font-size-sm2;
				}
				&-address{
					width: 450upx;
					font-size: $uni-font-size-sm2;
				}
			}
			&-img{
				height: 68upx;
				width: 68upx;
				border-radius: 50%;
			}
		}
		
		.select-goods{
			box-sizing: border-box;
			width: 690upx;
			margin: 30upx;
			padding: 30upx 20upx;
			background: $uni-bg-color;
			border-radius: $uni-border-radius-base;
			&-img{
				width: 200upx;
				height: 200upx;
			}
			&-info{
				margin-left: 20upx;
				width: 470upx;
				&-name{
					margin-bottom: 20upx;
				}
				&-type{
					color: $uni-text-color-grey;
					font-size: $uni-font-size-sm2;
				}
				&-daterange{
					color: $uni-text-color-grey;
					font-size: $uni-font-size-sm2;
				}
			}
		
			.select-goods-number{
				margin: 20upx 0;
			}
			
			.select-goods-price{
				padding-top: 20upx;
				border-top: 1px solid $uni-border-color;
				.price{
					font-size: $uni-font-size-sm2;
				}
			}
		}
		
		.ticket-code{
			margin: 20upx 30upx;
			padding: 0 30upx;
			background: $uni-bg-color;
			border-radius: $uni-border-radius-base;
			.ticket-code-item{
				height: 110upx;
				border-bottom: 1px solid $uni-border-color;
				&:last-child{
					border-bottom: none;
				}
			}
		}
		
		.select-pay{
			&-tit{
				padding-left: 30upx;
				color: $uni-text-color-grey2;
			}
			&-list{
				margin: 0 30upx;
				padding: 0 30upx;
				background: $uni-bg-color;
				border-radius: $uni-border-radius-base;
				&-item{
					height: 110upx;
					border-bottom: 1px solid $uni-border-color;
					&-img{
						height: 40upx;
						width: 40upx;
						margin-right: 10upx;
					}
				}
				&:last-child{
					border-bottom: none;
				}
			}
		}
		
		.agreement{
			text-align: right;
			line-height: 100upx;
			margin-right: 30upx;
			color: $uni-text-color-grey;
			font-size: $uni-font-size-sm;
		}
		
		.order-submit{
			position: fixed;
			bottom: 0;
			left: 0;
			right: 0;
			height: 106upx;
			border-top: 1px solid $uni-border-color;
			background: $uni-bg-color;
			.order-submit-price{
				flex-grow: 1;
				text-align: right;
				margin-right: 50upx;
			}
			.order-submit-confirm{
				width: 238upx;
				height: 106upx;
				line-height: 106upx;
				text-align: center;
				color: $uni-text-color-inverse;
				background: $uni-text-color-theme;
			}
		}
	}
</style>
        