<template>
	<view class="queue-information">
		<view class="queue-information-top">
			<view class="queue-information-top-touxiang">
				<view class="doctor-information-touxiang">
					<view class="doctor-information-touxiang-image">
						<!-- <span class="iconfont icon-yisheng" style="font-size: 25px; align-self: center;"></span> -->
						<image src='../../../../../static/img/icon/touxiang.jpeg' style="font-size: 25px; align-self: center;height: 100px;width: 100px;"
						 mode=""></image>
					</view>
				</view>
			</view>
			<view class="queue-information-top-text">
				<view class="">
					骨科
				</view>
				<view style="margin-left: 15px;">
					张三
				</view>
				 
			</view>
		</view>
		<view class="queue-information-now">
			<view class="queue-information-now-title">
				当前呼叫（1）
			</view>
			<view class="queue-information-now-text">
				<view style="display: flex;justify-content: space-between;width: 120rpx;">
					<view>
						06
					</view>
					<view>
						号
					</view>
				</view>
				<view style="width: 120rpx;margin-left:52rpx">
					王*兰
				</view>
				<view style="width: 180rpx;">
					1号诊室
				</view>
			</view>
			
		</view>
		<view class="queue-information-next">
			<view class="queue-information-next-title">
				<view class="queue-information-now-title">
					等待呼叫（20）
				</view>
			</view>
			<view class="queue-information-next-strip" v-for="item in 2" :style="{'color':item==1?'red':'','border-bottom':item==1?'none':''}">
				<view style="display: flex;justify-content: space-between;width: 120rpx;">
					<view>
						06
					</view>
					<view>
						号
					</view>
				</view>
				<view style="width: 120rpx;margin-left:52rpx">
					王*兰
				</view>
				<view style="width: 180rpx;">
					9:00
				</view>
			</view>
		</view>
	</view>
</template>

<script>
</script>

<style>
.doctor-information-touxiang {
	height: 200rpx;
	width: 200rpx;
	display: flex;
	justify-content: center;
}

.doctor-information-touxiang-image {
	align-self: center;
	width: 130rpx;
	height: 130rpx;
	border-radius: 65rpx;
	overflow: hidden;
	display: flex;
	justify-content: center;
}
.queue-information{
	display: flex;
	flex-direction: column;
}
.queue-information-top{
	display: flex;
	background-color: white;
}
.queue-information-top-text{
	display: flex;
/* 	flex-direction: column; */
	justify-content: center;
	align-items: center;
	font-size: 32rpx;
}
.queue-information-now{
	margin: 20rpx 0 20rpx 0;
	display: flex;
	flex-direction: column;
	background-color: white;
	padding: 20rpx 30rpx 20rpx 30rpx;
}
.queue-information-now-title{
	font-size: 32rpx;
	color: #5ab4d0;
}
.queue-information-now-text{
	display: flex;
	justify-content: space-between;
	font-size: 32rpx;
	margin-top: 20rpx;
}
.queue-information-next{
	margin: 0px 0 20rpx 0;
	display: flex;
	flex-direction: column;
	background-color: white;
	padding: 20rpx 30rpx 0px 30rpx;
}
.queue-information-next-strip{
	display: flex;
	justify-content: space-between;
	font-size: 32rpx;
	height: 120rpx;
	align-items: center;
	border-bottom: solid rgba(0,0,0,.5) .2px;
}
</style>
