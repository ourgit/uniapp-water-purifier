<template>
	<view class="index">
		<swiper class="banner" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
			<swiper-item v-for="(item, index) in bannerList" :key="index">
				<image class="swiper-item-img" :src="item.url" mode="aspectFill"></image>
			</swiper-item>
		</swiper>
		
		<view class="menu flex-center-around">
			<view class="menu-item" v-for="(item, index) in menuList" :key="index">
				<image class="menu-item-img" :src="item.img" mode="aspectFill"></image>
				<view class="menu-item-text">{{item.text}}</view>
			</view>
		</view>
		
		<view class="goods">
			<view class="goods-tit flex-center-between">
				<text class="uni-h4">产品中心</text>
				<view class="goods-tit-more">
					<text>更多</text>
					<uni-icon type="arrowright" color="#999" size="14"></uni-icon>
				</view>
			</view>
			<view class="goods-list flex-center">
				<view class="goods-list-item" v-for="(item,index) in goodsList" :key="index" @click="onClickGood">
					<image class="goods-list-item-img" :src="item.img" mode="aspectFill"></image>
					<view class="goods-list-item-detail text-overflow-two">{{item.detail}}</view>
					<view class="flex-center-between">
						<text class="color-important">{{item.price}}</text>
						<text class="goods-list-item-try">试租30天</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uniIcon from "@/components/uni-icon.vue"
	export default {
		components: {
			uniIcon
		},
		data() {
			return {
				bannerList: [
					{
						url: '../../static/images/img01.png'
					},
					{
						url: '../../static/images/img01.png'
					}
				],
				menuList: [
					{
						img: '../../static/images/index-pay.png',
						text: '充值缴费'
					},
					{
						img: '../../static/images/index-data.png',
						text: '机器数据'
					},
					{
						img: '../../static/images/index-control.png',
						text: '智能控制'
					},
					{
						img: '../../static/images/index-service.png',
						text: '服务召唤'
					}
				],
				goodsList: [
					{
						img: '../../static/images/img01.png',
						detail: '立升净水器家用全屋中央大流量超滤膜直饮机量超滤膜直饮机量超滤膜直饮机',
						price: '3180元/年'
					},
					{
						img: '../../static/images/img01.png',
						detail: '立升净水器家用全屋中央大流量超滤膜直饮机',
						price: '3180元/年'
					},
					{
						img: '../../static/images/img01.png',
						detail: '立升净水器家用全屋中央大流量超滤膜直饮机',
						price: '3180元/年'
					},
					{
						img: '../../static/images/img01.png',
						detail: '立升净水器家用全屋中央大流量超滤膜直饮机',
						price: '3180元/年'
					},
					{
						img: '../../static/images/img01.png',
						detail: '立升净水器家用全屋中央大流量超滤膜直饮机',
						price: '3180元/年'
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			onClickGood() {
				uni.navigateTo({
					url: 'goods'
				});
			}
		}
	}
</script>

<style lang="scss">
	.index{
		.banner{
			height: 352upx;
			.swiper-item-img{
				height: 100%;
				width: 100%;
			}
		}
		
		.menu{
			height: 224upx;
			background: $uni-bg-color;
			&-item{
				&-img{
					height: 100upx;
					width: 100upx;
				}
			}
		}
		
		.goods{
			margin-top: 20upx;
			background: $uni-bg-color;
			&-tit{
				height: 120upx;
				padding: 0 30upx;
				&-more{
					font-size: $uni-font-size-sm2;
					color: $uni-text-color-grey;
				}
			}
			&-list{
				flex-wrap: wrap;
				padding: 0 15upx;
				&-item{
					margin: 0 15upx 30upx;
					&-img{
						height: 330upx;
						width: 330upx;
						background: $uni-bg-color-grey;
					}
					&-detail{
						width: 330upx;
						line-height: 42upx;
					}
					&-try{
						height: 42upx;
						line-height: 42upx;
						padding: 0 20upx;
						background-color: #d5f8f4;
						color: #20b1a0;
						border-radius: $uni-border-radius-sm2;
						font-size: $uni-font-size-sm2;
					}
				}
			}
		}

	}
</style>
