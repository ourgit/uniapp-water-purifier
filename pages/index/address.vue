<template>
	<view class="address-management">
		<view class="address-management-top"></view>
		<view v-if="addressList.length > 0" class="address-management-list">
			<view
				class="address-management-list-item flex-center-between"
				v-for="(item, index) in addressList"
				:key="index">
				<view>
					<view>
						<text>{{item.name}}</text>
						<text>{{item.mobile}}</text>
						<text class="default">{{item.isDefault ? '默认' : ''}}</text>
					</view>
					<view class="address">{{item.address}}</view>
				</view>
				<uni-icon type="compose" size="26" @click="pageTo"></uni-icon>
			</view>
		</view>
		
		<view v-else class="no-data">暂无收货地址哦~</view>
		
		<view class="address-add">
			<button class="address-add-btn" @click="pageTo">
				<uni-icon type="plusempty" color="#fff" size="20"></uni-icon>
				<text>新建地址</text>
			</button>
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
				addressList: [
					{
						name: '张女士',
						mobile: '13787878902',
						address: '广东省深圳市南山区塘朗地铁站南山智园A3栋705',
						isDefault: true
					},
					{
						name: 'zox',
						mobile: '13787878902',
						address: '广东省深圳市南山区塘朗地铁站南山智园A3栋705',
						isDefault: false
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			
			pageTo() {
				uni.navigateTo({
					url: 'addressEdit'
				});
			},
			
		}
	}
</script>

<style lang="scss">
	.address-management{
		&-top{
			height: 10upx;
			width: 100%;
			background: url(../../static/images/address-top-border.png) no-repeat 100%/100%;
		}
		&-list{
			padding: 0 30upx;
			border-bottom: 1px solid $uni-border-color;
			&-item{
				height: 168upx;
				border-bottom: 1px solid $uni-border-color;
				&:last-child{
					border-bottom:none;
				}
				.default{
					display: inline-block;
					padding: 0 10upx;
					margin: 0 20upx;
					font-size: $uni-font-size-sm2;
					color: $uni-text-color-inverse;
					border-radius: $uni-border-radius-base;
					background-image: linear-gradient(-45deg, #00b5c4 0%, #52c7d1 100%), linear-gradient(#52c7d1, #52c7d1);
				}
				.address{
					font-size: $uni-font-size-sm2;
				}
			}
		}
		.address-add{
			position: fixed;
			bottom: 0;
			left: 0;
			right: 0;
			&-btn{
				margin: 38upx auto;
				width: 559upx;
				height: 88upx;
				line-height: 88upx;
				font-size: $uni-font-size-base;
				color: $uni-text-color-inverse;
				background-color: #504e56;
				border-radius: 44px;
			}
		}
	}
</style>
