<template>
	<view class="address-edit">
		<view class="address-edit-list">
			<view class="address-edit-list-item flex-center">
				<view class="address-edit-list-item-name">收货人</view>
				<input type="text" value="张女士" />
			</view>
			<view class="address-edit-list-item flex-center">
				<view class="address-edit-list-item-name">手机号码</view>
				<input type="text" value="13508665666" />
			</view>
			<view class="address-edit-list-item flex-center">
				<view class="address-edit-list-item-name">所在地区</view>
				<input type="text" value="广东省深圳市宝安区" />
			</view>
			<view class="address-edit-list-area">
				<view class="address-edit-list-area-name">详细地址</view>
				<textarea class="address-edit-list-area-value" value="广东省深圳市南山区塘朗地铁站南山智园A3栋70" />
			</view>
		</view>
		<view class="set-defect flex-center">
			<label>
				<checkbox :checked="defaultStatus" />设为默认地址
			</label>
		</view>
		
		<view class="submit-btn">
			<button @click="pageTo">保存</button>
		</view>
	</view>
	
</template>

<script>
	export default {
		components: {
			
		},
		data() {
			return {
				defaultStatus: false
			}
		},
		onLoad() {

		},
		methods: {
			
			pageTo() {
				uni.navigateTo({
					url: 'address'
				});
			},
			
		}
	}
</script>

<style lang="scss">
	.address-edit{
		background: $uni-bg-color;
		&-list{
			padding: 0 30upx;
			&-item{
				height: 110upx;
				border-bottom: 1px solid $uni-border-color;
				&-name{
					width: 125upx;
					color: $uni-text-color-grey2;
					margin-right: 60upx;
				}
			}
			&-area{
				&-name{
					margin-right: 60upx;
					color: $uni-text-color-grey2;
				}
				&-value{
					width: 100%;
					font-size: $uni-font-size-sm2;
				}
			}
		}
		.set-defect{
			height: 110upx;
			padding-left: 30upx;
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
