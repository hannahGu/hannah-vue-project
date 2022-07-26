<template>
	<view class="star">
	   评分：<view class="star-item" v-for="(itemClass, index) in itemClass" :key="index" :class="itemClass"></view>
	</view>
	
</template>

<script>
	// 星星总长度
	const LENGTH = 5;
	 
	// 星星的状态
	const CLS_ON = "on";        // 全星
	const CLS_HALF = "half";    // 半星
	const CLS_OFF = "off";      // 剩余未点亮的星星
	 
	export default {
	    name: 'star',
		props:['score'],
	    computed: {
	        itemClass() {
	            let result = [];
	            let score = Math.floor(this.score * 2) / 2;
	            let hasDecimal = score % 1 !== 0;
	            let integer = Math.floor(score);
	 
	            for(let i = 0; i < integer; i++) {
	                result.push(CLS_ON);
	            }
	 
	            // 是否有半个星星
	            if(hasDecimal) {
	                result.push(CLS_HALF);
	            }
	 
	            // 补齐
	            while(result.length < LENGTH) {
	                result.push(CLS_OFF);
	            }
	            return result
	        }
	    },
	 
	}
</script>

<style>
	.star{
		margin-left:20rpx;
	}
	.star .star-item{
	    display: inline-block;
	    width: 20rpx;
	    height: 20rpx;
	    margin-right: 6rpx;
	    background-repeat: no-repeat;
	    background-size: 20rpx 20rpx;
	}
	 
	/* 三种图片类型*/
	.star .on{
	    background-image: url(img/on.jpeg);
	}
	.star .half{
	    background-image: url(img/half.jpeg);
	}
	.star .off{
	    background-image: url(img/off.png);
	}
</style>