<template>
	<view class="login">
		<view class="login-input flex-center">
			<input placeholder="请输入手机号" v-model="phoneNumber" type="number" placeholder-class="placeholder" />
		</view>
		<view class="login-input flex-center">
			<input placeholder="请输入密码" v-model="passwd" password=true placeholder-class="placeholder" />
		</view>
		<view class="submit-btn">
			<button @click="doLogin">登录</button>
		</view>
		<view class="nav flex-center-between">
			<view @click="toPage('resetpasswd')">忘记密码</view>
			<view @click="toPage('register')">我要注册</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				phoneNumber: '',
				passwd:'',
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
			doLogin(){}
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
		.placeholder{
			color: $uni-text-color-placeholder;
		}
		.nav {
			color: $uni-text-color-theme;
			font-size: $uni-font-size-sm2;
		}
	}
</style>
