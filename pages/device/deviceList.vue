<template>
	<view class="device-list">
		<view class="device-list-item flex-center" v-for="(item, index) in deviceList" :key="index">
			<image class="device-list-item-img" :src="item.img" mode=""></image>
			<view class="device-list-item-right">
				<view class="device-list-item-right-item">
					<view class="device-list-item-right-item-tit uni-h5 text-overflow-one">
						{{item.tit}}
					</view>
				</view>
				<view class="device-list-item-right-item">
					<text class="device-list-item-right-item-info">型号:{{item.type}}</text>
				</view>
				<view class="device-list-item-right-item">
					<text class="device-list-item-right-item-info">租赁费：</text>
					<text class="color-important">¥{{item.price}}</text>
				</view>
				<view class="device-list-item-right-item flex-center">
					<image class="device-list-item-right-item-img" src="../../static/images/device-time.png" mode="aspectFill"></image>
					<text class="device-list-item-right-item-info">{{item.daterange}}</text>
				</view>
				<view class="device-list-item-right-item flex-center">
					<image class="device-list-item-right-item-img" src="../../static/images/device-location.png" mode="aspectFill"></image>
					<text class="device-list-item-right-item-info">{{item.address}}</text>
				</view>
				<button class="operate-device-btn">操作设备</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				deviceList: [
					{
						img: '../../static/images/img01.png',
						tit: '立升家用直饮净水机净水机净水机',
						type: '1320026',
						price: '3280',
						daterange: '2018.01.11-2019.10.10',
						address: '深圳市福田区车公庙苍松大厦1101'
					},
					{
						img: '../../static/images/img01.png',
						tit: '立升家用直饮净水机',
						type: '1320026',
						price: '3280',
						daterange: '2018.01.11-2019.10.10',
						address: '深圳市福田区车公庙苍松大厦1101'
					},
					{
						img: '../../static/images/img01.png',
						tit: '立升家用直饮净水机',
						type: '1320026',
						price: '3280',
						daterange: '2018.01.11-2019.10.10',
						address: '深圳市福田区车公庙苍松大厦1101'
					}
				]
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="scss">
	.device-list{
		&-item{
			box-sizing: border-box;
			padding: 30upx 30upx 30upx 40upx;
			background: $uni-bg-color;
			border-top: 20upx solid $uni-bg-color-grey;
			&-img{      
				width: 180upx;
				height: 190upx;
				background: $uni-bg-color-grey;
			}
			&-right{
				margin-left: 20upx;
				height: 190upx;
				width: 480upx;
				position: relative;
				&-item{
					line-height: 40upx;
					&-tit{
						width: 300upx;
					}
					&-info{
						color: $uni-text-color-grey;
						font-size: $uni-font-size-sm1;
					}
					&-img{
						height: 22upx;
						width: 22upx;
						margin-right: 10upx;
					}
				}
				.operate-device-btn{
					position: absolute;
					top: 0;
					right: 0;
					height: 52upx;
					line-height: 52upx;
					font-size: $uni-font-size-sm2;
					color: $uni-text-color-inverse;
					background: $uni-text-color-theme;
				}
			}
		}
	}
</style>
