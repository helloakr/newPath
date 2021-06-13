<template>
	<view>
		<show-navigation-bar titile="平整度"></show-navigation-bar>
		<view class="">
				<u-table>
					<u-tr class="u-tr">
						<u-th class="u-th">桩号</u-th>
						<u-th class="u-th"></u-th>
						<u-th class="u-th"></u-th>
						<u-th class="u-th"></u-th>
						<u-th class="u-th"></u-th>
						<u-th class="u-th"></u-th>
						<u-th class="u-th"></u-th>
						<u-th class="u-th">最大值</u-th>
					</u-tr>
					<u-tr class="u-tr">
						<u-td class="u-td">k154+200</u-td>
						<u-td class="u-td">1</u-td>
						<u-td class="u-td">2</u-td>
						<u-td class="u-td">1</u-td>
						<u-td class="u-td">2</u-td>
						<u-td class="u-td">1</u-td>
						<u-td class="u-td">2</u-td>
						<u-td class="u-td">2</u-td>
					</u-tr>
				</u-table>
		</view>
		<view class="charts-box">
		  <qiun-data-charts
		    type="line"
		    :chartData="chartData"
		    background="none"
		    :animation="false"
		  />
		</view>
		
	</view>
</template>

<script>
	import showNavigationBar from"../public-common/show-navigation-bar.vue"
	import uCharts from '../../components/u-charts/u-charts-v2.0.0.js'; 
	export default {
		components:{
			showNavigationBar,
		},
		data() {
			return {
				chartData:{
				    "categories": [
				        "1",
				        "2",
				        "3",
				        "4",
				        "5",
				        "6",
				        "7",
				        "8",
				        "9",
				        "10"
				    ],
				    "series": [
				        {
				            "name": "桩号：k154+200",
				            "data": [
				                1,
				                2,
				                1,
				                2,
				                1,
				                2,
				                3,
				                1,
				                2,
				                1
				            ]
				        },
				        {
				            "name": "桩号：k154+300",
				            "data": [
				                1,
				                1,
				                1,
				                2,
				                1,
				                1,
				                1,
				                2,
				                1,
				                1
				            ]
				        }
				    ]
				}
			}
		},
		methods: {
			
		}
	}
</script>

<style>
.charts-box{
	  width: 100%;
	  height:300px;
	}
</style>
