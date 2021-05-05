<template>
	<view>
		<!-- 弹出框 -->
		<u-popup v-model="show" 
				mode="bottom" 
				border-radius="20" 
				:closeable="true" 
				width="500rpx" 
				height="350px" 
				close-icon-pos="bottom-right"
				duration="170"
				@close="sendrequest"
				>
				<view class="charts-box">
				  <qiun-data-charts
				    :type="type"
				    :chartData="chartData"
				    background="none"
				    :animation="false"
				  />
				</view>
		</u-popup>
	</view>
</template>

<script>
	import uCharts from '../../components/u-charts/u-charts-v2.0.0.js'; 
	export default {
		name:"data-display-module",
		props:{
			type:String,
		    show:Boolean,
			chartData:Object
		},
		data() {
			return {
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
.charts-box{
	  width: 100%;
	  height:300px;
	}
</style>
