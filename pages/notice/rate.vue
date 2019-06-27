<template>
	<view class="score">
		<view class="score-star">
			<com-stars innerScore="3"></com-stars>
		</view>

		<view class="score-detail">
			
		</view>
	</view>
</template>

<script>
	import comStars from "../../components/com-stars.vue"
	export default {
		components: {
			comStars
		},
		data() {
			return {
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
	.score{
	}
</style>
