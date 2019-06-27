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
			<input placeholder="设置6-12位密码" v-model="passwd" password=true placeholder-class="placeholder" />
		</view>
		<view class="login-input flex-center">
			<input placeholder="确认新密码" v-model="confirmPwd" password=true placeholder-class="placeholder" />
		</view>
		<view class="login-input flex-center">
			<input placeholder="请输入渠道码（选填）" v-model="channelCode" placeholder-class="placeholder" />
		</view>
		<view class="submit-btn" >
			<button @click="doRegister">注册</button>
		</view>
		<view class="nav">
			已有密码？
			<text class="nav-login" @click="toPage('login')">点击登录</text>
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
				channelCode: '',
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
			doRegister(){}
		}
	}
</script>

<style lang="scss">
	.login {
		box-sizing: border-box;
		height: 100%;
		padding: 50upx 50upx 0;
		background: $uni-bg-color;
		&-input{
			height: 90upx;
			border-bottom: 1px solid $uni-border-color;
			margin-top: 30upx;
		}
		.code{
			&-btn{
				height: 54upx;
				line-height: 54upx;
				padding: 0 20upx;
				color: $uni-text-color-inverse;
				background: $uni-text-color-theme;
				border-radius: $uni-border-radius-base;
			}
		}
		.placeholder{
			color: $uni-text-color-placeholder;
		}
		.nav {
			text-align: center;
			color: $uni-text-color-grey;
			font-size: $uni-font-size-sm2;
			&-login{
				color: $uni-text-color-theme;
			}
		}
	}
</style>
