<template>
	<view class="order">
		<view class="order-form">
			<view class="order-form-cell flex-center-between">
				<text class="order-form-cell-name">单位名称</text>
				<input class="order-form-cell-value" type="text" value="立升净水企业" />
			</view>
			<view class="order-form-cell flex-center-between">
				<text class="order-form-cell-name">电话</text>
				<input class="order-form-cell-value" type="text" value="0332-234241" />
			</view>
			<view class="order-form-cell flex-center-between">
				<text class="order-form-cell-name">
					<text class="required color-important">*</text><text>联系人</text>
				</text>
				<input class="order-form-cell-value" type="text" value="" />
			</view>
			<view class="order-form-cell flex-center-between">
				<text class="order-form-cell-name">性别</text>
				<radio-group @change="sexChange">
					<label class="radio"><radio value="male" :checked="curSex === 'male'" />先生</label>
					<label class="radio"><radio value="female" :checked="curSex === 'female'" />女士</label>
				</radio-group>
			</view>
			<view class="order-form-cell flex-center-between">
				<text class="order-form-cell-name">
					<text class="required color-important">*</text><text>手机号</text>
				</text>
				<input class="order-form-cell-value" type="text" value="13532339459" />
			</view>
			<view class="order-form-cell flex-center-between">
				<text class="order-form-cell-name">微信号</text>
				<input class="order-form-cell-value" type="text" value="wx232324" />
			</view>
			<view class="order-form-cell flex-center-between">
				<text class="order-form-cell-name">
					<text class="required color-important">*</text><text>用水人数</text>
				</text>
				<input class="order-form-cell-value" type="text" value="23" />
			</view>
			<view class="order-form-cell flex-center-between">
				<text class="order-form-cell-name">使用性质</text>
				<picker class="flex-center" @change="bindPickerChange" :value="index" :range="array">
					<text>{{array[index]}}</text>
					<text class="iconfont iconbuoumaotubiao52"></text>
				</picker>
			</view>
			<view class="order-form-cell flex-center-between">
				<text class="order-form-cell-name">水质分类</text>
				<radio-group @change="waterTypeChange">
					<label class="radio"><radio value="1" :checked="curWaterType === '1'" />市政水</label>
					<label class="radio"><radio value="0" :checked="curWaterType === '0'" />非市政水</label>
				</radio-group>
			</view>
			<view class="order-form-cell flex-center-between">
				<text class="order-form-cell-name">安装地址</text>
				<mpvue-city-picker ref="mpvueCityPicker" :pickerValueDefault="pickerValueDefault" @onChange="onChange" @onCancel="onCancel" @onConfirm="onConfirm"></mpvue-city-picker>
			</view>
			<view>
				<text class="address-name">详细地址</text>
				<textarea class="address-area" value="广东省深圳市南山区塘朗地铁站南山智园A3栋70" />
			</view>
			
		</view>
		
<!-- 		<uni-list>
			<uni-list-item title="单位名称" show-arrow="false">
				<input class="order-form-cell-value" type="text" value="立升净水企业" />
			</uni-list-item>
			<uni-list-item title="电话" show-arrow="false"></uni-list-item>
			<uni-list-item title="*联系人" show-arrow="false">
			</uni-list-item>
			<uni-list-item title="性别" show-arrow="false"></uni-list-item>
			<uni-list-item title="*手机号" show-arrow="false"></uni-list-item>
			<uni-list-item title="微信号" show-arrow="false"></uni-list-item>
			<uni-list-item title="*用水人数" show-arrow="false"></uni-list-item>
			<uni-list-item title="使用性质"></uni-list-item>
			<uni-list-item title="水质分类" show-arrow="false"></uni-list-item>
			<uni-list-item title="安装地址"></uni-list-item>
			<uni-list-item title="详细地址"></uni-list-item>
		</uni-list> -->
		
		<view class="submit-btn">
			<button @click="pageTo">确定</button>
		</view>
	</view>
</template>

<script>
	import mpvueCityPicker from "@/components/mpvue-city-picker.vue"
	// import uniList from '@/components/uni-list.vue'
	// import uniListItem from '@/components/uni-list-item.vue'
	export default {
		components: {
			mpvueCityPicker,
			// uniList,
			// uniListItem,
		},
		data() {
			return {
				curSex: 'male',
				curWaterType: '1',
				array: ['办公', '家用'],
				index: 0,
				pickerValueDefault: [0, 0, 1]
			}
		},
		onLoad() {

		},
		methods: {
			sexChange(e) {
				this.curSex = e.target.value
			},
			waterTypeChange(e) {
				this.curWaterType = e.target.value
			},
			bindPickerChange: function(e) {
				this.index = e.target.value
			},
			pageTo() {
				uni.navigateTo({
					url: 'orderConfirm'
				});
			},
			showCityPicker() {
				this.$refs.mpvueCityPicker.show();
			},
			onChange(e) {
				console.log(e);
			},
			onCancel(e) {
				console.log(e);
			},
			onConfirm(e) {
				console.log(e);
			}
		}
	}
</script>

<style lang="scss">
	.order{
		padding-top: 20upx;
		font-size: $uni-font-size-lg1;
		&-form{
			padding: 0 30upx;
			background: $uni-bg-color;
			&-cell{
				height: 110upx;
				border-bottom: 1px solid $uni-border-color;
				&-name{
					color: $uni-text-color-grey2;
					padding-left: 20upx;
					.required{
						position: absolute;
						left: 30upx;
					}
				}
				&-value{
					text-align: right;
				}
				.radio{
					margin-left: 20upx;
				}
			}
			.address-name{
				color: $uni-text-color-grey2;
				padding-left: 20upx;
				line-height: 60upx;
			}
			.address-area{
				width: 650upx;
				height: 100upx;
				margin: 20upx auto;
				font-size: $uni-font-size-sm2;
			}
		}
		.submit-btn{
			padding: 0 30upx;
		}
	}
</style>
