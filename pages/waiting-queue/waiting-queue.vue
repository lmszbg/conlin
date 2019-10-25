<template>
	<view class="waiting-queue">
		<view class="waiting-queue-top">
			
		</view>
		<view class="wating-queue-type">
			<view class="wating-queue-type-left">
				<view class="wating-queue-type-text" @click="isMyWait=true" :class="isMyWait?'wating-queue-type-text-active':''">
					<view style="align-self: center;">
						候诊排队
					</view>
				</view>
			</view>
			<view class="wating-queue-type-right">
				<view class="wating-queue-type-text" @click="isMyWait=false" :class="isMyWait==false?'wating-queue-type-text-active':''">
					<view style="align-self: center;">
						全院叫号
					</view>
				</view>
			</view>
		</view>
		<view class="the-waiting-body" :style="{'display':isMyWait?'':'none'}">
			<view class="the-waiting-card" v-for="item in 2" @click="gotoInformation">
				<view class="the-waiting-card-patient">
					<view class="the-waiting-card-patient-text">
						门诊产科 阳诚
					</view>
				</view>
				<view class="the-waiting-card-top">
					<view class="the-waiting-card-top-title">
						<view>当前叫号</view>
					</view>
					<view class="the-waiting-card-top-num">
						<view>5号</view>
					</view>
					<view class="the-waiting-card-top-wait" style="color: rgba(0,0,0,.5);">
						<view>当前等待还有2人</view>
					</view>
				</view>
				
				<view class="the-waiting-yuanjiao1 " style="margin-top: -1px;margin-bottom: -1px;height: 9px;">
					<view style="background-color:#00CC99;width: 7px;height: 7px;border-top-right-radius: 7px;"></view>
					<view style="border-bottom: dashed rgba(0,0,0,.2) 1px;width: 568rpx;height: 6px;"></view>
					<view style="background-color: #00CC99;width: 7px;height: 7px;border-top-left-radius: 7px;"></view>
				</view>
				<view class="the-waiting-yuanjiao2" style="margin-top: -1px;height: 9px;margin-bottom: -1px;">
					<view style="background-color: #00CC99;width: 7px;height: 7px;border-bottom-right-radius: 7px;"></view>
					<view style="background-color: #00CC99;width: 7px;height: 7px;border-bottom-left-radius: 7px;"></view>
				</view>
				<view class="the-waiting-card-bottom" >
					<view class="the-waiting-card-bottom-title" style="color: #3f8fca;">
						<view>等待呼叫</view>
					</view>
					<view class="the-waiting-card-bottom-wait">
						<view>我的排队序号</view>
					</view>
					<view class="the-waiting-card-bottom-num">
						<view>5号</view>
					</view>
					<view class="the-waiting-card-bottom-strip">
						<view class="the-waiting-card-bottom-strip-left">
							候诊位置：
						</view>
						<view class="the-waiting-card-bottom-strip-right">
							门诊产科
						</view>
					</view>
					<view class="the-waiting-card-bottom-strip">
						<view class="the-waiting-card-bottom-strip-left">
							候诊时段：
						</view>
						<view class="the-waiting-card-bottom-strip-right">
							下午
						</view>
					</view>
					<view class="the-waiting-card-bottom-strip">
						<view class="the-waiting-card-bottom-strip-left">
							估计等待时间：
						</view>
						<view class="the-waiting-card-bottom-strip-right">
							10分钟
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="the-all-waiting" :style="{'display':isMyWait==false?'':'none'}">
			<view class="the-all-waiting-strip" v-for="item in 2">
				<view class="the-all-waiting-strip-left">
					<view class="the-all-waiting-strip-icon">
						<view class="iconfont icon-gerenxinxi" style="font-size: 110rpx;"></view>
					</view>
					<view class="the-all-waiting-strip-text">
						<view style="font-size: 36rpx;">
							乳腺病科
						</view>
						<view style="font-size: 28rpx; color: rgba(0,0,0,.5);display: flex;">
							普通
							<!-- <view class="iconfont icon-next" style="align-self: center; font-size: 15px;"></view> -->
						</view>
					</view>
				</view>
				<view class="the-all-waiting-strip-right">
					<view class="the-all-waiting-strip-right-text">
						<view style="display: flex;	color: #E87D0D;">
							当前叫号：
							<view >
								5号
							</view>
						</view>
						<view class="iconfont icon-next" style="align-self: center;font-size: 30rpx;margin-right: 2rpx;color: rgba(0,0,0,.5);"></view>
					</view>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default{
		data(){
			return {
				isMyWait: true
			}
		},
		methods:{
			gotoInformation: function (){
				uni.navigateTo({
					url: '../../waiting-queue-information/waiting-queue-information'
				})
			}
		}
	}
	
</script>

<style>
.waiting-queue{
	display: flex;
	flex-direction: column;
}
.waiting-queue-top{
	background-color: white;
	height: 120rpx;
}
.wating-queue-type{
	display: flex;
	justify-content: center;
	background-color: #f8f8f8;
}
.wating-queue-type-left{
	margin-right: 100rpx;
}
.wating-queue-type-text{
	height: 80rpx;
	font-size: 32rpx;
	display: flex;
	justify-content: center;
}
.wating-queue-type-text-active{
	color: #00CC99;
	border-bottom: solid #00CC99 3px;
}
.the-waiting-body{
	display: flex;
	justify-content: center;
	flex-direction: column;
}
.the-waiting-card{
	align-self: center;
	background-color: #00CC99;
	width: 680rpx;
	border-radius: 8rpx;
	margin-top: 32rpx;
	display: flex;
	flex-direction: column;
	padding-bottom: 30rpx;
}
.the-waiting-card-patient{
	height: 100rpx;
	align-self: center;
	display: flex;
	justify-content: center;
}
.the-waiting-card-patient-text{
	align-self: center;
	font-size: 32rpx;
	color: white;
}
.the-waiting-card-top{
	background-color: white;
	border-radius: 8rpx 8rpx 0 0;
	width: 600rpx;
	align-self: center;
	display: flex;
	flex-direction: column;
}
.the-waiting-card-top-title{
	align-self: center;
	font-size: 32rpx;
	margin: 10rpx 0 6rpx 0;
}
.the-waiting-card-top-num{
	align-self: center;
	color: red;
	font-size: 52rpx;
	margin: 10rpx 0 10rpx 0;
}
.the-waiting-card-top-wait{
	align-self: center;
	font-size: 32rpx;
	margin: 10rpx 0 10rpx 0;
}
.the-waiting-card-bottom{
	background-color: white;
	width: 600rpx;
	align-self: center;
	border-radius: 0 0 8rpx 8rpx;
	display: flex;
	flex-direction: column;
}
.the-waiting-card-bottom-title{
	align-self: center;
	font-size: 32rpx;
	margin: 10rpx 0 6rpx 0;
}
.the-waiting-card-bottom-num{
	align-self: center;
	color: red;
	font-size: 52rpx;
	margin: 10rpx 0 10rpx 0;
}
.the-waiting-card-bottom-wait{
	align-self: center;
	font-size: 32rpx;
	margin: 10rpx 0 10rpx 0;
}
.the-waiting-card-bottom-strip{
	width: 570rpx;
	align-self: center;
	display: flex;
	justify-content: space-between;
	font-size: 32rpx;
	margin-bottom: 10rpx;
	color: rgba(0,0,0,.5);
}
.the-waiting-card-bottom-strip-left{
	
}
.the-waiting-card-bottom-strip-right{
	
}
.the-waiting-yuanjiao1{
	width: 600rpx;
	align-self: center;
	background-color: white;
	display: flex;
	justify-content: space-between;
}
.the-waiting-yuanjiao2{
	width: 600rpx;
	background-color: white;
	align-self: center;
	display: flex;
	justify-content: space-between;
}
.the-all-waiting{
	display: flex;
	flex-direction: column;
}
.the-all-waiting-strip{
	width: 720rpx;
	background-color: white;
	align-self: center;
	height: 140rpx;
	display: flex;
	border-radius: 6rpx;
	margin-top: 32rpx;
	justify-content: space-between;
}
.the-all-waiting-strip-left{
	display: flex;
	align-self: center;
}
.the-all-waiting-strip-icon{
	align-self: center;
}
.the-all-waiting-strip-text{
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	height: 100rpx;
}
.the-all-waiting-strip-right{
	display: flex;
}
.the-all-waiting-strip-right-text{
	display: flex;
	font-size: 32rpx;
	margin-right: 8rpx;
	align-self: center;
}
</style>
