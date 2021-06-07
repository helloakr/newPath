<!-- The file is map show -->
<template>
	<view>
		<view class="mapStyle">
			<map 
				:style="{height: nowMapIndex ? nintyPercentScreenHeight : seventyPercentScreenHeight,width:'750rpx'}"
				:scale="scale"
				:latitude="latitude" 
				:longitude="longitude" 
				:markers="covers"
				:polyline="polyline"
				>
			</map>
			</view>
		</view>
	</view>
</template>

<script>
	var test ={
			points:[{latitude: 26.028955623309585,longitude: 119.31339730236814},],  
					color:"#C0C0C0", 
					width:3,  
					arrowLine: true,
				};
	export default {
		name:"map-show",
		data() {
			return {
				//地图数据
				title: 'map',
				nowMapIndex:true,
				phoneHeight:'',//屏幕高
				phoneWidth:'',//屏幕宽
				latitude: 26.02745167447258,
				longitude: 119.3118952653198, 
				tete:1,
				//地图标记
				covers: [{
					latitude: 26.02745167447258,
					longitude: 119.3118952653198,
					title: '北斗设备1',
					label: {
						content: '检查',
						color: '#F76350',
						anchorX: 0,
						anchorY: -80, 
						bgColor: '#fff', 
						padding: 5, 
						borderWidth: 1,
						borderColor: '#D84C29',						
						textAlign: 'right'
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
			};
		},
		onReady(){
				// 计算屏幕高度 ，宽度
				let _this = this;
				uni.getSystemInfo({
					success(res) {
					_this.phoneHeight = res.windowHeight;
					_this.phoneWidth = res.windowWidth
					console.log(_this.phoneHeight+"当前手机高度")
					console.log(_this.phoneWidth+"当前手机宽度")
				}
			});
		},
		computed:{//计算
					nintyPercentScreenHeight(){//百分之九十的屏幕高
						if(this.phoneHeight!=='' && this.phoneWidth!==''){
							return 750/(this.phoneWidth)*(this.phoneHeight)*0.9+'rpx'
						}else{
							return '1250rpx'
						}
						
					},
				seventyPercentScreenHeight(){//百分之七十的屏幕高
					if(this.phoneHeight!=='' && this.phoneWidth!==''){
						return 750/(this.phoneWidth)*(this.phoneHeight)*0.7+'rpx'
					}else{
							return '1000rpx'
				}
					
				},
			}
	}
</script>

<style>

</style>
