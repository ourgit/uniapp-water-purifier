<template>
	<view class="progress-detail">
		<view
			class="progress-detail-list flex-center"
			v-for="(item, index) in progressDetailList"
			:key="index">
			<view>
				<view class="progress-detail-list-time">{{item.time}}</view>
				<view class="progress-detail-list-date">{{item.date}}</view>
			</view>
			<view class="bull">&bull;</view>
			<view class="progress-detail-list-text">
				{{item.text}}
			</view>
		</view>
		
		<view class="submit-btn">
			<button @click="pageTo">服务评价</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				progressDetailList: [
					{
						step: 1,
						text: '已完成',
						date: '2019-04-15',
						time: '11:30',
					},
					{
						step: 2,
						text: '上门安装',
						date: '2019-04-15',
						time: '11:30',
					},
					{
						step: 3,
						text: '预约时间4月16日',
						date: '2019-04-15',
						time: '11:30',
					},
					{
						step: 4,
						text: '派单成功',
						date: '2019-04-15',
						time: '11:30',
					},
					{
						step: 5,
						text: '申请安装/售后',
						date: '2019-04-15',
						tiem: '11:34',
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			pageTo() {
				uni.navigateTo({
					url: 'rate'
				});
			},
		}
	}
</script>

<style lang="scss">
	.progress-detail{
		height: 100%;
		box-sizing: border-box;
		padding: 90upx 0 0 60upx;
		background: $uni-bg-color;
		&-list{
			margin-bottom: 66upx;
			&-time{
				text-align: center
			}
			&-date{
				font-size: $uni-font-size-sm1;
				text-align: center;
				color: $uni-text-color-grey;
			}
			.bull{
				margin: 0 30upx;
				color: $uni-text-color-theme;
			}
			&-text{
				font-weight: bold;
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
