<template>
	<view class="card-strip">
		<view class="card-strip-left">
			<view class="card-strip-left-image">
				<!-- <svg class="icon card-strip-left-image-icon" aria-hidden="true">
				  <use :xlink:href=iconSrc></use>
				</svg> -->
			</view>
			<view class="card-strip-left-text">
				<view class="card-strip-left-text-title">
					{{ title }}
				</view>
				<view class="card-strip-left-text-note">
					{{ note }}
				</view>
			</view>
		</view>
		<view class="card-strip-right">
			<view class="card-strip-right-image">
				<image src="../../../static/img/icon/right.png" style="width: 50rpx; height: 50rpx;" ></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			title:String,
			note:String,
			iconSrc:String
		}
	}
</script>

<style>
	.card-strip{
		display: flex;
		height: 120rpx;
	}
	
	.card-strip-left{
		justify-content: flex-start;
		display: flex;	
		width: 480rpx;
		align-items: center;
	}
	.card-strip-left-image{
		justify-content: flex-start;
	}
	.card-strip-left-text{
		justify-content: flex-end;
		margin-left: 24rpx;
	}
	.card-strip-left-text-title{
		font-size: 36rpx;
		font-weight: 600;
		margin-bottom: 10rpx;
	}
	.card-strip-left-text-note{
		color: #999999;
		font-size: 20rpx;
	}
	.card-strip-right{
		justify-content: flex-end;
		width: 140rpx;
		display: flex;
		align-items: center;
	}
	.card-strip-right-image{
		justify-content: flex-end;
	}
	.card-strip-left-image-icon{
		font-size: 84rpx;
	}
</style>
