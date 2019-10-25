<template>
	<view class="container">
		<!-- <scroll-view :scroll-y="true" :scroll-x="false">
			<view class="index-head">
				<view class="">
					<search-bar class="search-bar"></search-bar>
				</view>
				<navigator url="../../doctor-information/doctor-information"><add-patient-card></add-patient-card></navigator>
				
			</view>
			<view class="index-body">
				<view class="quick-handing-channel-card">
					<view class="my-card quick-handing-channel-uni-card">
						<view class="quick-handing-channel-card-title">
							<view>
								快速办理通道
							</view>
						</view>
						<view class="quick-handing-channel-card-body">
							<view v-for="(item, index) in quickTitles">
								<card-strip :title=item :note=quickNotes[index] :iconSrc=quickIcon[index] :class="index==quickNumber-1?'':'quick-handing-channel-card-xiahuaxian'"></card-strip>
							</view>
						</view>
					</view>
				</view>
			</view>

		</scroll-view> -->
		<!-- <waiting-queue-information></waiting-queue-information> -->
		<waitingQueue></waitingQueue>
	</view>
</template>

<script>
	import searchBar from '@/pages/index/search-bar/search-bar.vue'
	import addPatientCard from '@/components/add-patient-card/add-patient-card.vue'
	import uniCard from '@dcloudio/uni-ui/lib/uni-card/uni-card'
	import cardStrip from '@/components/card-strip/card-strip.vue'
	import waitingQueueInformation from '@/pages/waiting-queue-information/waiting-queue-information.vue'
	import waitingQueue from '@/pages/waiting-queue/waiting-queue.vue'
	export default {
		components: {
			searchBar,
			addPatientCard,
			uniCard,
			cardStrip,
			waitingQueueInformation,
			waitingQueue
		},
		data() {
			return {
				quickNumber: 3,
				quickTitles: [
					"预约挂号",
					"门诊缴费",
					"住院服务"
				],
				quickNotes: [
					"实时查看医生情况",
					"快速缴费不排队",
					"省心省力安心养病"
				],
				quickIcon: [
					"#icon-Stone-add-circle",
					"#icon-Stone-bed",
					"#icon-Stone-bed"
				]
			}
		},
		onLoad() {

		},
		onShow() {

		},
		methods: {

		}
	}
</script>

<style>
	.container {}

	.index-head {
		background-color: white;
		padding: 0 0 30rpx 0;
		/* box-shadow: 0 1px 3px rgba(26,26,26,.1); */
	}

	.quick-handing-channel-card {
		display: flex;
		justify-content: center;
		margin-top: 30rpx;
	}

	.quick-handing-channel-uni-card {
		padding: 25rpx 25rpx 25rpx 25rpx;
	}

	.quick-handing-channel-card-body {
		margin-top: 20rpx;
	}

	.quick-handing-channel-card-xiahuaxian {
		border-bottom: solid rgba(0, 0, 0, .1) 1px;
	}

	.my-card {
		width: 650rpx;
		box-shadow: 0px 0px 1px rgba(0, 0, 0, .1);
		background-color: white;
		border-radius: 3px;
	}
</style>
