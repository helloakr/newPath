<template>
	<view>
		<!-- 导航栏 -->
		<u-navbar :is-back="false" 
					title="北斗芯路" 
					:background="background" 
					title-color="#ffffff">
		</u-navbar>
		
		<!-- 地图显示模块 -->
		<view class="mapStyle">
			<map 
				style="width:100%;height:600px;" 
				:scale="scale"
				:latitude="latitude" 
				:longitude="longitude" 
				:markers="covers"
				:polyline="polyline">
			</map>
		</view>
		
		<!-- 封装渲染组件 -->
		<data-display-module :show="showfriction"  @closewindo="updateFriction" :chartData="chartData" :type="chartType"></data-display-module>
		<data-display-module :show="showcarside"  @closewindo="updateCarside" :chartData="chartData1" :type="chartType1"></data-display-module>
		<data-display-module :show="showplaneness"  @closewindo="updatePlaneness" :chartData="chartData2" :type="chartType2"></data-display-module>
		<data-display-module :show="showdamage"  @closewindo="updateDamage" :chartData="chartData3" :type="chartType3"></data-display-module>		
			<!-- 图表按钮 -->
		<u-grid :col="2" :border="true">
				<u-grid-item bg-color="#2cb5e8">
					<u-icon name="../../static/Icon/chezhe.png" :size="50" @click="showCarside"></u-icon>
					<view class="grid-text">车辙</view>
				</u-grid-item>
				<u-grid-item bg-color="#2cb5e8">
					<u-icon name="../../static/Icon/mochaxishu.png" :size="50" @click="showFriction"></u-icon>
					<view class="grid-text">摩擦系数</view>
				</u-grid-item>
				<u-grid-item bg-color="#2cb5e8">
					<u-icon name="../../static/Icon/pingzhengdu.png" :size="50" @click="showPlaneness"></u-icon>
					<view class="grid-text">平整度</view>
				</u-grid-item>
				<u-grid-item bg-color="#2cb5e8">
					<u-icon name="../../static/Icon/sunhuai.png" :size="50" @click="showDamage"></u-icon>
					<view class="grid-text">损坏</view>
				</u-grid-item>
			</u-grid>
	</view>
</template>

<script>
	import uCharts from '../../components/u-charts/u-charts-v2.0.0.js'; 
	import dataDisplayModule from"../../components/data-display-module/data-display-module.vue"
	
	//地图初始化数据
	var test ={
			points:[{latitude: 26.028955623309585,longitude: 119.31339730236814},],  
						color:"#C0C0C0", 
						width:3,  
						arrowLine: true,
				};
	export default {
		data() {
			return {
				//导航栏数据
				background: {
					backgroundColor: '#001f3f',	
						backgroundImage: 'linear-gradient(141deg, rgb(159,184,173), rgb(31,200,219),rgb(44,181,232))',
				},
				disply:null,
				//地图数据
				title: 'map',
				latitude: 26.02745167447258,
				longitude: 119.3118952653198, 
				tete:1,
				//地图标记
				covers: [{
					latitude: 26.02745167447258, //纬度
					longitude: 119.3118952653198, //经度			
					title: '北斗设备1', //标注点名
					label: { //为标记点旁边增加标签
						content: '检查', //文本
						color: '#F76350', //文本颜色
						anchorX: 0, //label的坐标，原点是 marker 对应的经纬度
						anchorY: -80, //label的坐标，原点是 marker 对应的经纬度 
						bgColor: '#fff', //背景色
						padding: 5, //文本边缘留白
						borderWidth: 1, //边框宽度
						borderColor: '#D84C29', //边框颜色							
						textAlign: 'right' //文本对齐方式。
					},
				}],
				//路径
				polyline:[{
					points:[  
						{latitude:0,longitude:0},
					],  
					color:"#F76350", 
					width:5,  
					arrowLine: true,
				}],
				scale: 15,
				//弹窗
				
				showfriction:false,
				showcarside:false,
				showplaneness:false,
				showdamage:false,
				chartType:"arcbar",
				chartData:{"series": [{"name": "正确率","data": 0.8,"color": "#2fc25b"}]},
				chartType1:"radar",
				chartData1:{"categories": ["维度1","维度2","维度3","维度4","维度5","维度6"],"series": [{"name": "","data": [90,110,165,195,187,172]},{"name": "","data": [190,210,105,35,27,2]}]},
				chartType2:"column",
				chartData2:{ "categories": ["100","200","300","400","500","600"],"series": [{"name": "目标值","data": [35,36,31,33,13,34]},{"name": "完成量","data": [18,27,21,24,6,28]}]},
				chartType3:"line",
				chartData3:{  "categories": ["100","200","300","400","500","500"],"series": [{"name": "成交量A","data": [35,8,25,37,4,20]},{"name": "成交量B","data": [70,40,65,100,44,,68]},{"name": "成交量C","data": [100,80,95,150, 112,132]
        }
    ]}
				//图表数据
			};
		},
		methods:{
			//让地图动起来
			getPolyline(){
				var that = this;
				var num=test.points.length;
				var tt=test.points[num-1].latitude+0.001;
				var ss=test.points[num-1].longitude+0.001;
				var jj = {latitude:tt,longitude:ss};
				test.points.push(jj);
				that.polyline.push(test);
			},
			updateFriction(){   //声明这个函数
			      this.showfriction=false
			 },
			 updateCarside(){   //声明这个函数
			       this.showcarside=false
			  },
			  updatePlaneness(){   //声明这个函数
			        this.showplaneness=false
			   },
			updateDamage(){   //声明这个函数
			         this.showdamage=false
			    },
			//渲染图表的函数
			showFriction(){
				this.showfriction=true;
			},
			showCarside(){
				this.showcarside=true;
			},
			showPlaneness(){
				this.showplaneness=true;
			},
			showDamage(){
				this.showdamage=true;
			}
			
		},
		mounted:function(){
			// setInterval(this.getPolyline,1000);
		},
		beforeDestroy:function(){
			clearInterval(this.getPolyline);
		}
	}
</script>
<style lang="scss">
	.grid-text {
			font-size: 28rpx;
			margin-top: 4rpx;
			color:#FFFFFF;
	},
	// 全局字体设置
	body {
		 font-family:"微软雅黑";font-weight:bold;
	}
	
</style>
