<template>
	<view>
			<view class="">	
				<u-navbar :is-back="false"
							:background="background" 
							title-color="#ffffff">
							<view class="slot-wrap">
							<u-icon class="information" name="../../static/Icon/information.png" :size="40" @click="showCarside"></u-icon>
							<u-search placeholder="输入地点与坐标" :show-action="false"></u-search>
							<u-icon class="user" name="../../static/Icon/user.png" :size="40"></u-icon>
							</view>
				</u-navbar>
			</view>
	</view>
</template>

<script>
	export default {
		name:"show-navigation-bar",
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
			
		}
	}
</script>

<style lang="scss">
.slot-wrap{
		display:flex;
		align-items:center;
		flex: 1;
		padding: 0 30rpx;
		.user{
			display:flex;
			align-items:center;
			padding-left: 5px;
		}
		.information{
			display:flex;
			align-items:center;
			padding-right: 5px;
		}
	}
</style>
