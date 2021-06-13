<template>
	<view>
		<show-navigation-bar><!-- 导航栏 --></show-navigation-bar>
		<map-show><!-- 地图 --></map-show>
		
		<!-- 九宫格图表 -->
		<u-grid :col="2" :border="true">
				<u-grid-item bg-color="#2cb5e8">
					<u-icon name="../../static/Icon/chezhe.png" :size="50"></u-icon>
					<view class="grid-text">车辙</view>
				</u-grid-item>
				<u-grid-item bg-color="#2cb5e8">
					<u-icon name="../../static/Icon/mochaxishu.png" :size="50"></u-icon>
					<view class="grid-text">摩擦系数</view>
				</u-grid-item>
				<u-grid-item bg-color="#2cb5e8">
					<u-icon name="../../static/Icon/pingzhengdu.png" :size="50"  @click="gotoPlaneness()"></u-icon>
					<view class="grid-text">平整度</view>
				</u-grid-item>
				<u-grid-item bg-color="#2cb5e8">
					<u-icon name="../../static/Icon/sunhuai.png" :size="50"></u-icon>
					<view class="grid-text">损坏</view>
				</u-grid-item>
			</u-grid>
	</view>
</template>

<script>
	import mapShow from "../../components/map-show/map-show.vue"
	import showNavigationBar from"../../components/public-common/show-navigation-bar-index.vue"
	export default {
		components:{
			showNavigationBar,
		},
		data() {
			return {
				
			};
		},
		methods:{
			//跳转到平整度界面
			gotoPlaneness(){
					uni.navigateTo({
						url:"../../components/planeness/planeness",
					fail(err) {
						console.log(err);
					}})
			}
		},
	}
</script>
<style lang="scss">
	.grid-text {
			font-size: 28rpx;
			margin-top: 4rpx;
			color:#FFFFFF;
	},
	body {
		 font-family:"微软雅黑";font-weight:bold;
	}
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
	.mapStyle{
		z-index:-1;
	}
	.seizeSeat{
		width:100%;
		height:600px;
	}
</style>
