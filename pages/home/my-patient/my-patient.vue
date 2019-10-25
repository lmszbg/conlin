<template>
	<view class="">
		<view class="">
			<view v-for="(item, index) in patientArr" :key='index'>
				<visit-card-information-strip :patientId='patientIdArr[index]' :patient='item'></visit-card-information-strip>
			</view>
			<view class="add-card-information-strip">
				<view class="add-card-information-strip-body" @click="gotoBindVisitCard">
					<view class="add-card-information-strip-note">
						<!-- 左边 -->
						<!-- 数据排列 -->
						<view class="add-card-information-strip-left">
							<view class="add-card-information-strip-left-icon">
								<span class="iconfont icon-addto my-icon-add"></span>
							</view>
							<view class="add-card-information-strip-left-text">
								<view class="add-card-information-strip-patient">
									添加就诊人
								</view>
								<view class="add-card-information-strip-patient-id">
									{{ addPatientMsg }}
								</view>
							</view>
						</view>
						<!-- 右边 -->
						<view class="add-card-information-strip-right">
							<my-right-icon color="#bbb" size="20"></my-right-icon>
						</view>
					</view>

				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import visitCardInformationStrip from '@/components/visit-card-information-strip/visit-card-information-strip.vue'
	import myRightIcon from '@/components/my-right-icon/uni-icons.vue'
	export default {
		components: {
			visitCardInformationStrip,
			myRightIcon
		},
		data() {
			return {
				addPatientNum: 4,
				addPatientMsg: '还可以添加4人',
				patientArr: [
					'张三',
					'李四',
					'王五',
					'赵六'
				],
				patientIdArr: [
					8754231,
					2132142,
					1214841,
					2113214
				]
			}
		},
		watch: {
			addPatientNum(oldValue, newValue) {
				this.chaneAddPatientMsg(newValue)
			}
		},
		onShow: function() {
			this.chaneAddPatientMsg(this.addPatientNum)
		},
		methods: {
			chaneAddPatientMsg: function(number) {
				if (number === 0) {

				} else {
					this.addPatientMsg = '还可以添加' + newValue + '人'
				}
			},
			gotoBindVisitCard: function() {
				uni.navigateTo({
					url: '../../personal/bind-visit-card/bind-visit-card'
				})
			}
		}
	}
</script>

<style>
	.add-card-information-strip {
		display: flex;
		height: 170rpx;
		padding: 20rpx 18rpx 0rpx 18rpx;
	}

	.add-card-information-strip-body {
		width: 100%;
		background-color: white;
		border-radius: 2px;
		display: flex;
		justify-content: center;
	}

	.add-card-information-strip-note {
		display: flex;
		justify-content: space-between;
		height: 120rpx;
		align-self: center;
		width: 640rpx;
	}

	.add-card-information-strip-left {
		display: flex;
		justify-content: center;
		height: 100%;
	}

	.add-card-information-strip-left-icon {
		display: flex;
	}

	.add-card-information-strip-left-text {
		display: flex;
		flex-direction: column;
		justify-content: center;
		height: 100%;
	}

	.add-card-information-strip-patient {
		display: flex;
		font-weight: 400;
		font-size: 40rpx;
	}

	.add-card-information-strip-patient-default {
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

	.add-card-information-strip-patient-id {
		color: #CCCCCC;
		font-size: 32rpx;
		margin-top: 6rpx;
		display: flex;
	}

	.add-card-information-strip-patient-id-note {}

	.add-card-information-strip-right {
		align-self: center;
	}

	.my-icon-add {
		align-self: center;
		color: #4CD964;
		font-size: 120rpx;
		margin-left: -20rpx;
	}
</style>
