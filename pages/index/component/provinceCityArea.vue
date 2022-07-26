<template>
	<view class="content">
		        <view class="uni-padding-wrap">
		            <view class="uni-title">地址：{{province}} {{city}} {{area}}</view>
		        </view>
		        <picker-view v-if="visible" :indicator-style="indicatorStyle" :value="value" @change="bindChange" class="picker-view">
		            <picker-view-column>
		                <view class="item" v-for="(item,index) in provinces" :key="index">{{item.name}}</view>
		            </picker-view-column>
		            <picker-view-column>
		                <view class="item" v-for="(item,index) in cities" :key="index">{{item.name}}</view>
		            </picker-view-column>
		            <picker-view-column>
		                <view class="item" v-for="(item,index) in areas" :key="index">{{item}}</view>
		            </picker-view-column>
		        </picker-view>

	</view>
</template>

<script>
	import provinces from './province.js'
	export default {
		data: function () {
				const cities = []
				const areas = []
		        const province = ''
		        const city = ''
		        const area = ''
		
		        return {
		            title: 'picker-view',
					areas,
					cities,
		            provinces,
		            province,
		            city,
		            area,
		            value: [0, 0, 0],
		            visible: true,
		            indicatorStyle: `height: 50px;`
		        }
		    },
		    methods: {
		        bindChange: function (e) {
					
		            const val = e.detail.value
		            this.province = this.provinces[val[0]]['name']
					this.cities = this.provinces.filter(i=>i.name === this.province)[0]['city']
		            this.city = this.cities[val[1]>=this.cities.length? 0: val[1]]['name']
		            this.areas = this.cities.filter(i=>i.name === this.city)[0]['area']
					this.area = this.areas[val[2]>this.areas.length? 0: val[2]]
		        }
		    }
		}


</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}
	.uni-padding-wrap{
		margin-left:40rpx;
		width:100%;
		
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	.picker-view {
			width: 750rpx;
			height: 600rpx;
			margin-top: 20rpx;
		}
		.item {
			height: 50px;
			align-items: center;
			justify-content: center;
			text-align: center;
		}
</style>
