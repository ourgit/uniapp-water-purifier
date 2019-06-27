<template>
	<view class="login">
		<view class="login-input flex-center">
			<input placeholder="请输入手机号" v-model="phoneNumber" type="number" placeholder-class="placeholder" />
		</view>
		<view class="login-input flex-center-between code">
			<input placeholder="请输入验证码" v-model="code" placeholder-class="placeholder" />
			<view class="code-btn">获取验证码</view>
		</view>
		<view class="login-input flex-center">
			<input placeholder="设置6-12位新密码" v-model="passwd" password=true placeholder-class="placeholder" />
		</view>
		<view class="login-input flex-center">
			<input placeholder="确认新密码" v-model="confirmPwd" password=true placeholder-class="placeholder" />
		</view>
		<view class="submit-btn">
			<button @click="doConfirm">确认</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				phoneNumber: '',
				code: '',
				passwd:'',
				confirmPwd: '',
			}
		},
		onLoad() {

		},
		methods: {
			toPage(page){
				// uni.hideKeyboard()
				uni.navigateTo({
					url: page
				});
			},
			doConfirm(){}
		}
	}
</script>

<style lang="scss">
	.login {
		box-sizing: border-box;
		height: 100%;
		padding: 50upx 50upx 0;
		background: $uni-bg-color;
		.login-input{
			height: 90upx;
			border-bottom: 1px solid $uni-border-color;
			margin-top: 30upx;
		}
		.code{
			.code-btn{
				height: 54upx;
				line-height: 54upx;
				padding: 0 20upx;
				color: $uni-text-color-inverse;
				background-color: $uni-text-color-theme;
				border-radius: $uni-border-radius-base;
			}
		}
		.placeholder{
			color: $uni-text-color-placeholder;
		}
	}
</style>
