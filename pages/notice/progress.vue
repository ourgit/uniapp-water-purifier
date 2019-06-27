<template>
	<view class="progress">
		<view class="progress-list" v-for="(item, index) in progressList" :key="index">
			<view class="progress-list-datetime">{{item.datetime}}</view>
			<view class="progress-list-item" @click="pageTo">
				<view class="progress-list-item-tit">
					{{item.tit}}
				</view>
				<view class="progress-list-item-con">
					{{item.con}}
				</view>
				<view class="progress-list-item-detail flex-center-between">
					<text>查看详情</text>
					<uni-icon type="arrowright" color="#ccc" size="20"></uni-icon>
				</view>
			</view>
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
				progressList: [
					{
						datetime: '2018年4月16日 08:32',
						tit: '安装服务通知',
						con: '您好，您的安装申请服务已经完成。',
					},
					{
						datetime: '2018年4月17日 12:03',
						tit: '维修服务通知',
						con: '您好，您的维修申请服务已经完成。',
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			pageTo() {
				uni.navigateTo({
					url: 'progressDetail'
				});
			},
		}
	}
</script>

<style lang="scss">
	.progress{
		&-list{
			&-datetime{
				width: 250upx;
				margin: 45upx auto 30upx;
				text-align: center;
				border-radius: $uni-border-radius-sm1;
				font-size: $uni-font-size-sm1;
				background: $uni-bg-color-grey2;
				color: $uni-text-color-inverse;
			}
			&-item{
				background: $uni-bg-color;
				border-radius: $uni-border-radius-base;
				margin: 0 30upx;
				padding: 20upx 30upx 0;
				&-tit{}
				&-con{
					font-size: $uni-font-size-sm2;
					line-height: 50upx;
				}
				&-detail{
					height: 90upx;
					font-size: $uni-font-size-sm2;
					color: $uni-text-color-theme;
					border-top: 1px solid $uni-border-color;
				}
			}
		}
	}
</style>
