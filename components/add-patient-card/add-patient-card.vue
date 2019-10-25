<template>
	<view class="add-patient-card-container">
		<view class="add-patient-card">
			<view class="add-patient-card-text">
				+添加就诊卡
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		
	}
</script>

<style>
	.add-patient-card-container {
		display: -webkit-flex;
		display: flex;
		justify-content: center;
		margin-top: 20rpx;
	}
	
	.add-patient-card {
		display: flex;
		width: 690rpx;
		height: 150rpx;
		background-color: #00CC99;
		justify-content: center;
		align-items: center;
		border-radius: 10rpx;
	}
	
	.add-patient-card-text {
		font-size: 36rpx;
		color: white;
	}
</style>
