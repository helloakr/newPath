<template>
	<view>
		<u-navbar :is-back="false"
							:background="background" 
							title-color="#ffffff"
							:title="titile"
							>
							<view class="slot-wrap">
								<u-icon class="information" name="../../static/Icon/back.png" :size="40" @ @click="goBack()"></u-icon>
							</view>
		</u-navbar>
	</view>
</template>

<script>
	export default {
		name:"show-navigation-bar",
		props:{
			titile:String,
		},
		data() {
			return {
				//导航栏设置
				background: {
					backgroundColor: '#001f3f',	
						backgroundImage: 'linear-gradient(141deg, rgb(159,184,173), rgb(31,200,219),rgb(44,181,232))',
				},
			}
		},
		methods: {
			goBack(){
				uni.navigateBack()
			}
		}
	}
</script>

<style lang="scss">
.slot-wrap{
		display:flex;
		align-items:center;
		flex: 1;
		padding: 0 30rpx;
		.information{
			display:flex;
			align-items:center;
			padding-right: 5px;
		}
	}
</style>
