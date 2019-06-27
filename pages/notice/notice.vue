<template>
	<view class="notice">
		<view
			class="notice-item flex-center"
			v-for="(item,index) in noticeList"
			:key="index"
			@click="pageTo(item.page)">
			<image class="notice-item-img" :src="item.icon" mode="aspectFill"></image>
			<view class="notice-item-right">
				<view class="flex-center-between">
					<text class="notice-item-right-name">
						{{item.name}}
					</text>
					<text class="notice-item-right-datetime">
						{{item.list.length > 0 ? item.list[item.list.length-1].datetime : ''}}
					</text>
				</view>
				<view class="notice-item-right-con">
					{{item.list.length > 0 ? item.list[item.list.length-1].con : '暂无'+item.name+'提醒'}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				noticeList: [
					{
						name: '漏水报警',
						page: 'alarm',
						icon: '../../static/images/notice-alarm.png',
						list: [
							{
								datetime: '11-30 21:23',
								con: '紧急！您的净水器漏水中，请尽快处理！'
							}
						]
					},
					{
						name: '更换滤芯',
						page: 'repair',
						icon: '../../static/images/notice-repair.png',
						list: []
					},
					{
						name: '维修保养',
						page: 'maintenance',
						icon: '../../static/images/notice-maintenance.png',
						list: []
					},
					{
						name: '平台推送',
						page: 'platform',
						icon: '../../static/images/notice-platform.png',
						list: []
					},
					{
						name: '服务进度',
						page: 'progress',
						icon: '../../static/images/notice-progress.png',
						list: []
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			pageTo(page) {
				uni.navigateTo({
					url: page
				});
			},
		}
	}
</script>

<style lang="scss">
	.notice{
		background: $uni-bg-color;
		padding: 0 40upx;
		.notice-item{
			height: 162upx;
			border-bottom: 1px solid $uni-border-color;
			&:last-child{
				border-bottom: none;
			}
			.notice-item-img{
				width: 80upx;
				height: 80upx;
				border-radius: 50%;
				background: $uni-bg-color-grey;
			}
			.notice-item-right{
				width: 560upx;
				margin-left: 30upx;
				.notice-item-right-datetime,
				.notice-item-right-con{
					font-size: $uni-font-size-sm2;
					color: $uni-text-color-grey;
				}
			}
		}
	}
</style>
