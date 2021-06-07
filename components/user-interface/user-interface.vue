<template>
	<view>
		<!-- 弹出框 -->
		<u-popup v-model="show" 
				mode="right" 
				border-radius="20" 
				:closeable="true" 
				width="500rpx" 
				height="350px" 
				close-icon-pos="bottom-right"
				duration="170"
				@close="sendrequest"
				>
				<u-card>
						<view class="" slot="body">
							<u-avatar :src="src" mode="square"></u-avatar>
							<u-line color="grey" />
							<view class="u-body-item u-flex u-border-bottom u-col-between u-p-t-0">
								<view class="u-body-item-title u-line-2">工作地点</view>
							</view>
								<u-line color="grey" />
							<view class="u-body-item u-flex u-row-between u-p-b-0">
								<view class="u-body-item-title u-line-2">手机号码</view>
							</view>
								<u-line color="grey" />
							<view class="u-body-item u-flex u-row-between u-p-b-0">
								<view class="u-body-item-title u-line-2">邮箱</view>
							</view>
							<u-line color="grey" />
							<view class="u-body-item u-flex u-row-between u-p-b-0">
								<view class="u-body-item-title u-line-2">账户绑定</view>
							</view>
							<u-line color="grey" />
							<view class="u-body-item u-flex u-row-between u-p-b-0">
								<view class="u-body-item-title u-line-2">切换公司</view>
							</view>
							<u-line color="grey" />
							<view class="u-body-item u-flex u-row-between u-p-b-0">
								<view class="u-body-item-title u-line-2">帮助中心</view>
							</view>
							<u-line color="grey" />
							<view class="u-body-item u-flex u-row-between u-p-b-0">
								<view class="u-body-item-title u-line-2">设置</view>
							</view>
							
						</view>
						<view class="" slot="foot"><u-button class="custom-style">退出</u-button></u-icon></view>
					</u-card>
		</u-popup>
	</view>
</template>

<script>
	export default {
		name:"data-display-module",
		props:{
		    show:Boolean,
		},
		data() {
			return {
				title: '素胚勾勒出青花，笔锋浓转淡',
				subTitle: '2020-05-15',
				thumb: 'http://pic2.sc.chinaz.com/Files/pic/pic9/202002/hpic2119_s.jpg',
				src: '../../static/Icon/userphto.png'
			};
		},
		methods:{
			//关闭事件
		    sendrequest() {
				this.$emit("closewindo");//自定义事件  传递值“子向父组件传值”
		    }
		  }
	}
</script>

<style>
.u-card-wrap { 
		background-color: $u-bg-color;
		padding: 1px;
	}
	
	.u-body-item {
		font-size: 32rpx;
		color: #333;
		padding: 30rpx 10rpx;
		border-radius: 8rpx;
	}
	.custom-style {
			color: #606266;
			width: 400rpx;
		}
</style>
