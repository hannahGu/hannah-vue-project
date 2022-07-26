<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
			<view>
				<Star :score="score"/>
				<ProvinceCityArea />
			</view>
		
	</view>
</template>

<script>
	import ProvinceCityArea from './component/provinceCityArea.vue'
	import Star from './component/star.vue'
	export default {
		data: function () {
		        return {
		            title: '汉娜测试题',
					score:3.7,
		        }
		    },
			components:{
			    ProvinceCityArea,
				Star,
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

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	
</style>
