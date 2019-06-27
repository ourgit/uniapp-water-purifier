<template>
	<view class="goods">
		<swiper class="goods-swiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
			<swiper-item v-for="(item, index) in goodsImgsList" :key="index">
				<image class="goods-swiper-img" :src="item.url" mode="aspectFill"></image>
			</swiper-item>
		</swiper>
		<view class="goods-info">
			<view class="goods-info-name uni-h5 text-overflow-two">
				立升净水器家用全屋中央大流量超滤膜直饮机自来水过滤管道净化器滤膜直饮机自来水过滤管道净化器滤膜直饮机自来水过滤管道净化器
			</view>
			<view class="flex-center-between">
				<text class="good-price color-important">
					<text>¥</text>
					<text class="uni-h3">3180</text>
					<text>/年</text>
				</text>
				<view class="year-limit">一年起租</view>
			</view>
		</view>
		<view class="goods-select flex-center-between" @click="toggleSelectOption(true)">
			<view>
				<text>选择</text>
				<text class="text-color-grey">租期 数量 套餐</text>
			</view>
			<uni-icon type="more" size="30"></uni-icon>
		</view>
		<view class="goods-param">
			<view class="goods-param-tit flex-center-around">
				<text :class="actived ? 'tit' : 'tit tit-actived'" @click="toggleParam(0)">
					租赁流程
				</text>
				<text :class="actived ? 'tit tit-actived' : 'tit'" @click="toggleParam(1)">
					属性参数
				</text>
			</view>
			<view v-show="!actived" class="goods-param-process">
				<view v-for="(item,index) in processList" :key="index">
					<view class="flex-center">
						<image class="goods-param-process-img" :src="item.icon" mode="aspectFill"></image>
						<text>{{item.text}}</text>
					</view>
					<uni-icon v-if="index !== processList.length-1" class="arrowthindown" type="arrowthindown" color="#999" size="16"></uni-icon>
				</view>
			</view>
			<view v-show="actived" class="goods-param-prop">
				<view class="goods-param-prop-item flex-center">
					<text class="goods-param-prop-item-name">品牌</text>
					<text class="goods-param-prop-item-value">立升</text>
				</view>
				<view class="goods-param-prop-item flex-center">
					<text class="goods-param-prop-item-name">型号</text>
					<text class="goods-param-prop-item-value">LU3A-3C套餐1</text>
				</view>
				<view class="goods-param-prop-item flex-center">
					<text class="goods-param-prop-item-name">机器类型</text>
					<text class="goods-param-prop-item-value">超滤机 终端净水器 净水设备</text>
				</view>
				<view class="goods-param-prop-item flex-center">
					<text class="goods-param-prop-item-name">饮用人数</text>
					<text class="goods-param-prop-item-value">6人</text>
				</view>
				<view class="goods-param-prop-item flex-center">
					<text class="goods-param-prop-item-name">水质</text>
					<text class="goods-param-prop-item-value">纯净水</text>
				</view>
				<view class="goods-param-prop-item flex-center">
					<text class="goods-param-prop-item-name">功率</text>
					<text class="goods-param-prop-item-value">25W</text>
				</view>
				<view class="goods-param-prop-item flex-center">
					<text class="goods-param-prop-item-name">出水量</text>
					<text class="goods-param-prop-item-value">80L/h</text>
				</view>
				<view class="goods-param-prop-item flex-center">
					<text class="goods-param-prop-item-name">机身尺寸</text>
					<text class="goods-param-prop-item-value">472x150x140 mm</text>
				</view>
				<view class="goods-param-prop-item flex-center">
					<text class="goods-param-prop-item-name">机器重量</text>
					<text class="goods-param-prop-item-value">4.1kg</text>
				</view>
			</view>
		</view>
		<view class="goods-detail">
			<view class="goods-detail-tit uni-h4">产品详情</view>
			<view class="goods-detail-con">
				<image src="../../static/images/img01.png" mode=""></image>
				<image src="../../static/images/img01.png" mode=""></image>
			</view>
		</view>
		<view class="goods-bottom flex-center">
			<view class="goods-bottom-price">
				<text>租金</text>
				<text class="color-important">
					<text>￥</text>
					<text class="uni-h3">3180</text>
				</text>
			</view>
			<view class="goods-bottom-try">试租30天</view>
			<view class="goods-bottom-confirm" @click="pageToOrder">立即租赁</view>
		</view>
		<view class="goods-mask" v-show="showPopupBottom" @touchmove.stop @click="toggleSelectOption(false)"></view>
		<view class="goods-popup" v-show="showPopupBottom" @touchmove.stop @click.stop>
			<view class="flex-center">
				<image class="select-img" src="../../static/images/img01.png" mode=""></image>
				<view class="select-info">
					<view class="select-info-name text-overflow-two">
						立升净水器家用全屋中央大流量超滤膜直饮机中央大流量超滤膜直饮机中央大流量超滤膜直饮机
					</view>
					<view class="select-info-type">
						型号：LA2-1V02-PCRCU
					</view>
					<view class="select-info-price">
						维护费：￥740
					</view>
				</view>
			</view>
			<view class="select-type">
				<view class="select-type-tit">套餐</view>
				<text
					v-for="(item, index) in typeList" :key="index"
					:class="index === typeActived ? 'select-type-item type-actived': 'select-type-item'"
					@click="selectType(index)">{{item}}
				</text>
			</view>
			<view class="select-number">
				<view class="select-number-tit">数量</view>
				<view class="select-number-con">
					<uni-number-box :value="selectNumber" :min="1" :max="reserveNumber"></uni-number-box>
					<text class="reserve">库存：{{reserveNumber}}</text>
				</view>
			</view>
			<view class="select-daterange">
				<view class="select-daterange-tit">租期</view>
				<view class="select-daterange-con">
					<view class="select-daterange-con-item flex-center-between">
						<text class="name">起始租期</text>	
						<picker mode="date" :value="dateStart" @change="bindStartDateChange">
							<text class="value">{{dateStart}}</text>
							<text class="iconfont iconbuoumaotubiao52"></text>
						</picker>
					</view>
					<view class="select-daterange-con-item flex-center-between">
						<text class="name">结束租期</text>	
						<picker mode="date" :value="dateEnd" @change="bindEndDateChange">
							<text class="value">{{dateEnd}}</text>
							<text class="iconfont iconbuoumaotubiao52"></text>
						</picker>
					</view>
				</view>
			</view>
			
		</view>
	</view>
</template>

<script>
	import uniIcon from "@/components/uni-icon.vue"
	import uniNumberBox from "../../components/uni-number-box.vue"
	export default {
		components: {
			uniNumberBox,
			uniIcon,
		},
		data() {
			const currentDate = this.getDate({
				format: true
			})
			return {
				actived: 0, // 0:租赁流程;1属性参数:
				goodsImgsList: [
					{
						url: '../../static/images/img01.png'
					},
					{
						url: '../../static/images/img01.png'
					}
				],
				processList: [
					{
						icon: '../../static/images/tab-user.png',
						text: '选择设备和租期'
					},
					{
						icon: '../../static/images/tab-user.png',
						text: '在线预付租金（货按月代扣租金）'
					},
					{
						icon: '../../static/images/tab-user.png',
						text: '提交订单，系统审核，工作人员电话联系'
					},
					{
						icon: '../../static/images/tab-user.png',
						text: '发货安装，上门调试'
					}
				],
				showPopupBottom: false,
				typeList: ['￥3180/首年', '￥6260/2年', '￥9240/3年'],
				dateStart: currentDate,
				dateEnd: currentDate,
				typeActived: 0,
				selectNumber: 1,
				reserveNumber: 10,
			}
		},
		onLoad() {

		},
		methods: {
			toggleParam(index) {
				this.actived = index
			},
			selectType(index){
				this.typeActived = index
			},
			toggleSelectOption(status) {
				this.showPopupBottom = status
			},
			getDate() {
				const date = new Date();
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();
				month = month > 9 ? month : '0' + month;;
				day = day > 9 ? day : '0' + day;
				return `${year}-${month}-${day}`;
			},
			bindStartDateChange(e) {
				this.dateStart = e.target.value
			},
			bindEndDateChange(e) {
				this.dateEnd = e.target.value
			},
			pageToOrder() {
				uni.navigateTo({ url: 'order' });
			}
		}
	}
</script>

<style lang="scss">
	.goods{
		padding-bottom: 106upx;
		.goods-swiper{
			height: 750upx;
			.goods-swiper-img{
				width: 100%;
				height: 100%;
			}
		}
		
		.goods-info{
			padding: 20upx 30upx 50upx;
			background: $uni-bg-color;
			.goods-info-name{
				line-height: 52upx;
				width: 690upx;
				margin: 0 auto 30upx;
			}
			.year-limit{
				width: 119upx;
				height: 40upx;
				line-height: 40upx;
				border-radius: 20upx;
				text-align: center;
				font-size: $uni-font-size-sm2;
				color: $uni-text-color-inverse;
				background-image: linear-gradient(-45deg, #f6660c 0%, #ffa065 100%), linear-gradient(#ffa065, #ffa065);
				box-shadow: 0px 3px 7px 0px rgba(255, 134, 59, 0.35);
			}
		}
		
		.goods-select{
			padding: 0 30upx;
			height: 100upx;
			border-top: 1px solid $uni-border-color;
			background: $uni-bg-color;
			.text-color-grey{
				margin-left: 50upx;
				color: $uni-text-color-grey;
			}
		}
		
		.goods-param{
			margin-top: 20upx;
			background: $uni-bg-color;
			.goods-param-tit{
				padding-top: 20upx;
				border-bottom: 1px solid $uni-border-color;
				.tit{
					line-height: 70upx;
				}
				.tit-actived{
					color: $uni-text-color-theme;
					border-bottom: 2px solid $uni-text-color-theme;
				}
			}
			.goods-param-process{
				padding: 50upx;
				&-img{
					height: 36upx;
					width: 36upx;
					padding: 22upx;
					margin-right: 16upx;
					border: 1px dotted $uni-border-color;
					border-radius: 50%;
				}
				.arrowthindown{
					padding: 0 28upx;
				}
			}
			.goods-param-prop{
				padding: 0 30upx;
				&-item{
					height: 108upx;
					border-bottom: 1px solid $uni-border-color;
					&:last-child{
						border-bottom: none;
					}
					&-name{
						width: 120upx;
						color: $uni-text-color-grey2;
					}
					&-value{
						margin-left: 50upx;
					}
				}
			}
		}
		
		.goods-detail{
			margin-top: 20upx;
			padding: 30upx 20upx;
			background: $uni-bg-color;
			.goods-detail-tit{
				line-height: 64upx;
				text-align: center;
			}
		}
		
		.goods-bottom{
			position: fixed;
			bottom: 0;
			left: 0;
			right: 0;
			z-index: 1000;
			height: 106upx;
			padding-left: 30upx;
			border-top: 1px solid $uni-border-color;
			background: $uni-bg-color;
			&-price{
				flex-grow: 1;
				font-size: $uni-font-size-sm2;
			}
			&-try,
			&-confirm{
				width: 238upx;   
				line-height: 106upx;
				text-align: center;
				color: $uni-text-color-inverse;
			}
			&-try{
				background: #4f4d55;
			}
			&-confirm{
				background: $uni-text-color-theme;
			}
		}
		
		.goods-mask{
			position: fixed;
			background: $uni-bg-color-mask;
			width: 100%;
			top: 0;
			bottom: 106upx;
			left: 0;
			right: 0;
			z-index: 998;
			overflow: hidden;
			animation: showMask 0.2s ease;
		}
		
		.goods-popup{
			position: fixed;
			overflow: hidden;
			width: 100%;
			left: 0;
			bottom: 107upx;
			z-index: 999;
			box-sizing: border-box;
			padding: 40upx 30upx 0;
			background: $uni-bg-color;
			animation: showPopop 0.2s ease;
			.select-img{
				width: 200upx;
				height: 200upx;
			}
			.select-info{
				width: 470upx;
				margin-left: 20upx;
				.select-info-name{
					line-height: 40upx;
					margin-bottom: 40upx;
				}
				.select-info-type{
					line-height: 40upx;
					font-size: $uni-font-size-sm2;
					color: $uni-text-color-grey;
				}
				.select-info-price{
					line-height: 40upx;
					font-size: $uni-font-size-sm2;
					color: $uni-text-color-grey;
				}
			}
			.select-type{
				margin-top: 30upx;
				.select-type-tit{
					line-height: 40upx;
					margin-bottom: 20upx;
				}
				.select-type-item{
					display: inline-block;
					height: 76upx;
					line-height: 76upx;
					background: $uni-bg-color-grey;
					padding: 0 30upx;
					margin-right: 30upx;
					font-size: $uni-font-size-sm2;
					border-radius: $uni-border-radius-base;
				}
				.type-actived{
					background: $uni-text-color-theme;
					color: $uni-text-color-inverse;
				}
			}
			.select-number{
				margin-top: 30upx;
				.select-number-tit{
					line-height: 40upx;
				}
				.select-number-con{
					margin: 30upx 0;
					display: flex;
					align-items: flex-end;
					.reserve{
						font-size: $uni-font-size-sm2;
						color: $uni-text-color-grey;
						margin-left: 20upx;
					}

				}
			}
			.select-daterange{
				.select-daterange-tit{
					line-height: 40upx;
				}
				.select-daterange-con{
					padding: 0 20upx;
					&-item{
						line-height: 90upx;
						border-bottom: 1px solid $uni-border-color;
						&:last-child{
							border-bottom: none;
						}
						.name,
						.value,
						.iconfont{
							color: $uni-text-color-grey;
							font-size: $uni-font-size-sm2;
						}
					}
					
				}
			}
		}
		
		@keyframes showMask {
			0% {
				opacity: 0;
			}
			100% {
				opacity: 1;
			}
		}
		@keyframes showPopop {
			0% {
				transform: translateY(100%);
			}
			100% {
				transform: translateY(0%);
			}
		}
	}
</style>
