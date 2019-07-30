<template>
	<view class="swipers-wrap">
		<swiper @animationfinish="swiperChange"  :current="currentSwiper" circular="true"  class="swipers-view"
		 :autoplay="autoplay"  @change="dotChange">
			<block v-for="(item,index) in swiperList" :key="index">
				<swiper-item>
					<view class="swipers-best-hot-video">
						美景展示~
					</view>
					<view class="swipers-image-view">
						<image :src="item.imgUrl" mode="aspectFill" class="swipers-image"></image>
						<view class="swipers-title">
							{{item.title}}
						</view>
					</view>
				</swiper-item>
			</block>
		</swiper>
		
		<!--重置指示面板（小圆点）的样式  -->
		<view class="swipers-dots">
			<block v-for="(item,index) in swiperList" :key="index">
				<view class="dot" :class="{active:  currentDot == index}"></view>
			</block>
		</view>
	</view>
</template>
 
<script>
	export default {
		data() {
			return {
				currentDot: 0, //指示面板对应的索引
				currentSwiper: 0, //用来记录当前swiper对应的索引
				autoplay: true,
				swiperList:[
					{
						'imgUrl':'../../static/swiper.jpg',
						'title':'白云朵朵！'
					},
					{
						'imgUrl':'../../static/list.jpg',
						'title':'蓝天绿树！'
					},
					{
						'imgUrl':'../../static/user.jpg',
						'title':'boy！'
					}
				]
			}
		},
 
		methods: {
			dotChange: function(e) {
				this.currentDot = e.detail.current
			},
			swiperChange: function(e) {
				this.currentSwiper = e.detail.current
			},
		}
	}
</script>
 
<style>
	.swipers-wrap {
		height: auto;
		position: relative;
		background-color: blue;
		padding: 0 15upx;
		padding-bottom: 54upx;
 
	}
 
	.swipers-view {
		height: 420upx;
	}
 
	.swipers-best-hot-video {
		height: 90upx;
		line-height: 90upx;
		color: #f8f3bf;
		font-size: 36upx;
		text-align: center;
	}
 
	.swipers-image-view {
		height: 100%;
		position: relative;
		z-index: 1;
	}
 
	.swipers-image {
		width: 100%;
		height: 100%;
	}
 
 
	.swipers-image-view .swipers-title {
		position: absolute;
		z-index: 99;
		left: 25upx;
		bottom: 105upx;
		font-size: 24upx;
		font-weight: bold;
 
		color: #fff;
		font-size: 36upx;
	}
 
	/*用来包裹所有的小圆点  */
	.swipers-dots {
		width: 100%;
		height: 50upx;
		display: flex;
		flex-direction: row;
		position: absolute;
		left: 0;
		bottom: 0upx;
		/* border:1upx solid red; */
		display: flex;
		justify-content: center;
		align-items: center;
		/* border:1rpx solid green; */
	}
 
	/*未选中时的小圆点样式 */
	.dot {
		width: 6px;
		height: 2upx;
		width: 55upx;
		background-color: #999;
		margin: 0 10upx;
		/* border:1upx solid red; */
	}
 
	/*选中以后的小圆点样式  */
	.dot.active {
		height: 2upx;
		width: 80upx;
		background-color: #fff;
		margin: 0 10upx;
	}
</style>
