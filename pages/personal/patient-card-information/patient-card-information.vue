<template>
	<view class="patient-card-information">
		<view class="patient-card-information-strip">
			<view class="patient-card-information-strip-body">
				<view class="patient-card-information-strip-note">
					<!-- 左边 -->
					<!-- 数据排列 -->
					<view class="patient-card-information-strip-left">
						<!-- 就诊人 -->
						<view class="patient-card-information-strip-patient">
							{{ patient }}
							<!-- 是否默认 -->
							<view class="patient-card-information-strip-patient-default">
								默认
							</view>
						</view>
						<!-- 门诊id -->
						<view class="patient-card-information-strip-patient-id">
							门诊ID：
							<view class="patient-card-information-strip-patient-id-note">
								{{ patientId }}
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="patient-card-information-bar-code">
			<bar-code val="8722857"></bar-code>
		</view>
		<view class="add-patient-card-note-container">
			<view class="add-patient-card-note" style="padding-top: 25rpx;">
				<view class="add-patient-card-note-strip" v-for="(item, index) in columns">
						<view style="color: #CCCCCC;"> 
							{{ item }}
						</view>
						<view class="">
							{{ columnsValues[index] }}
						</view>
				</view>
			</view>
			<view class="add-patient-card-note add-patient-card-note-strip-bottom">
					<view class="add-patient-card-note-strip ">
							<view style="align-self: center;"> 
								设为默认就诊人
							</view>
							<view class="">
								<switch checked></switch>
							</view>
					</view>
				</view>
		</view>
		<view class="patient-card-information-bottom">
			<view class="patient-card-information-bottom-body">
				<view class="patient-card-information-bottom-button">
					<view class="patent-card-information-bottom-button-text button-add">
						添加到卡包
					</view>
				</view>
				<view class="patient-card-information-bottom-button">
					<view class="patent-card-information-bottom-button-text">
						删除就诊人
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import barCode from '@/components/tki-barcode/tki-barcode.vue'
	export default {
		data() {
			return {
				patient: '张某某',
				patientId: '8722857',
				barcode: '8722857',
				columns: [
					'性别',
					'出生日期',
					'身份证',
					'手机号',
					'地址'
				],
				columnsValues: [
					'男',
					'11-2-25',
					'3303**************22',
					'158****2154',
					'浙江温州皮革厂'
				]
			}
		},
		components:{
			barCode
		}
	}
</script>

<style>
	.patient-card-information{
		display: flex;
		flex-direction: column;
	}
	.patient-card-information-strip {
		display: flex;
		height: 170rpx;
		padding: 20rpx 18rpx 0rpx 18rpx;
	}

	.patient-card-information-strip-body {
		width: 100%;
		background-color: white;
		border-radius: 2px;
		display: flex;
		justify-content: center;
	}

	.patient-card-information-strip-note {
		display: flex;
		justify-content: space-between;
		height: 120rpx;
		align-self: center;
		width: 640rpx;
	}

	.patient-card-information-strip-left {
		height: 100%;
	}

	.patient-card-information-strip-patient {
		display: flex;
		font-weight: 600;
		font-size: 40rpx;
	}

	.patient-card-information-strip-patient-default {
		margin-top: 6rpx;
		margin-left: 20rpx;
		align-self: center;
		height: 32rpx;
		border: solid #CCCCCC 2rpx;
		border-radius: 4rpx;
		font-size: 28rpx;
		padding: 0px 4rpx 6rpx 8rpx;
		font-weight: 400;
		color: #CCCCCC;
	}

	.patient-card-information-strip-patient-id {
		color: #CCCCCC;
		font-size: 32rpx;
		margin-top: 22rpx;
		display: flex;
	}

	.patient-card-information-strip-patient-id-note {}

	.patient-card-information-strip-right {
		align-self: center;
	}
	.patient-card-information-bar-code{
		display: flex;
		justify-content: center;
		padding: 25rpx 0 25rpx 0;
		height: 164rpx;
	}
	.my-barcode{
		align-items: center;
	}
	.add-patient-card-note-container{
		display: flex;
		flex-direction: column;
		padding: 0rpx 18rpx 0rpx 18rpx;
	}
	.add-patient-card-note{
		width: 100%;
		background-color: white;
		border-radius: 2px;
		display: flex;
		flex-direction: column;
	}
	.add-patient-card-note-strip{
		display: flex;
		justify-content: space-between;
		width: 640rpx;
		align-self: center;
		padding: 0rpx 0 25rpx 0;
		font-size: 32rpx;
	}
	.add-patient-card-note-strip-bottom{
		border-top: solid #CCCCCC 1px;
		padding-top: 20rpx;
	}
	.patient-card-information-bottom{
		margin-top: 50rpx;
		padding: 0rpx 18rpx 0rpx 18rpx;
	}
	.patient-card-information-bottom-body{
		display: flex;
		justify-content: space-between;
		padding: 0rpx 32rpx 0rpx 32rpx;
	}
	.patient-card-information-bottom-button{
		background-color: white;
		width: 314rpx;
		height: 90rpx;
		border-radius: 5px;
		display: flex;
		justify-content: center;
	}
	.patent-card-information-bottom-button-text{
		align-self: center;
	}
	.button-add{
		color:#00CC99;
	}
</style>
