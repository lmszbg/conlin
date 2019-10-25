<template>
	<view class="doctor-information">
		<view class="doctor-information-top">
			<view class="doctor-information-top-container">
				<!-- 头像 -->
				<view class="doctor-information-touxiang">
					<view class="doctor-information-touxiang-image">
						<!-- <span class="iconfont icon-yisheng" style="font-size: 25px; align-self: center;"></span> -->
						<image :src=doctor.imageUrl style="font-size: 25px; align-self: center;height: 100px;width: 100px;"
						 mode=""></image>
					</view>
				</view>
				<!-- 个人信息 -->
				<view class="doctor-information-top-doctor">
					<view class="doctor-information-top-doctor-name">
						{{ doctor.name }}
					</view>
					<view class="doctor-information-top-doctor-do">
						{{ doctor.house }}
					</view>
				</view>
				<!-- 图标 -->
				<view class="doctor-information-top-icon">
					<!-- 收藏 -->
					<view class="">
						<span class="iconfont icon-icon-test3 doctor-information-top-myicon"></span>
					</view>
					<!-- 分享 -->
					<view class="">
						<span class="iconfont icon-icon-test doctor-information-top-myicon"></span>
					</view>
				</view>
			</view>
			<view class="doctor-information-top-text">
				擅长：{{doctor.docterTC | doctorTCfilter}}
			</view>
		</view>
		<view class="doctor-information-type">
			<view class="doctor-information-type-body">
				<view :class="isVisit?'doctor-information-type-body-item-active':''" class="register doctor-information-type-body-item "
				 @click="isVisit = true">
					挂号
				</view>
				<view :class="isVisit==false?'doctor-information-type-body-item-active':''" class="introduce doctor-information-type-body-item"
				 @click="isVisit = false">
					介绍
				</view>
			</view>
		</view>
		<view class="the-visit" v-if="isVisit" style="margin-top: 20rpx;">
			<time-chose-doctor  :days='days' :show="isTimeShow" :showIndex="timeShowIndex"
			 @showChange="theShowChange" @showIndexChange="theShowIndexChange"/>
			<view class="doctor-information-bottom">
				<view class="doctor-information-bottom-body" :style="{'border-bottom': index == theTimeAndPrice.length-1?'':'solid rgba(0, 0, 0, .2) 1px'}"
				 v-for="(item, index) in theTimeAndPrice" :key=index @click="showPopup(index)">
					<view class="doctor-information-bottom-body-strip">
						<view class="doctor-information-bottom-time">
							{{item.time}}
						</view>
						<view class="doctor-information-bottom-price" style="display: flex;color: #E87D0D;">
							￥{{item.price | priceFilter}}
							<view class="iconfont icon-youjiantou" style="align-self: center;color: rgba(0,0,0,.5);margin-left: 2px;font-size: 800;" />
						</view>
					</view>
				</view>
			</view>
			<my-uni-popup ref="popup" type="bottom">
				<view class="information-popup">
					<view class="information-popup-doctor">
						<view class="doctor-information-touxiang information-popup-touxiang">
							<view class="doctor-information-touxiang-image" style="margin-top: 24px;">
								<!-- <span class="iconfont icon-yisheng" style="font-size: 25px; align-self: center;"></span> -->
								<image :src="doctor.imageUrl" style="font-size: 25px; align-self: center;height: 100px;width: 100px;"
								 mode=""></image>
							</view>
						</view>
						<view class="doctor-information-text">
							<view class="doctor-information-text-item">
								<view class="doctor-information-text-item-left">医师：</view>
								<view class="doctor-information-text-item-right">
									{{ doctor.name }}
								</view>
							</view>
							<view class="doctor-information-text-item">
								<view style="display: flex;">
									<view class="doctor-information-text-item-left" style="align-self: flex-start;">科室：</view>
									<view class="doctor-information-text-item-right">
										{{ doctor.house }}
									</view>
								</view>
							</view>
							<view class="doctor-information-text-item">
								<view class="doctor-information-text-item-left">费用：</view>
								<view class="doctor-information-text-item-right" style="color: #E87D0D;">
									{{pupopPrice | priceFilter}}
								</view>
							</view>
							<view class="doctor-information-text-item">
								<view class="doctor-information-text-item-left">时段：</view>
								<view class="doctor-information-text-item-right">
									{{ pupopTime }}
								</view>
							</view>
							<view class="doctor-information-text-item" style="height: 18px;margin-top: -5px;">
								<view class="doctor-information-text-item-left"></view>
								<view class="doctor-information-text-item-right">
									{{ pupopTime2 }}
								</view>
							</view>
						</view>
						<view class="doctor-information-close">
							<view class="iconfont icon-close doctor-information-close-icon" @click="closePopup"></view>
						</view>
					</view>
					<view class="information-popup-patient">
						<view class="">
							<view class="information-popup-patient-title">
								请选择就诊人
							</view>
							<view class="information-popup-patient-note">
								({{ patientList[patientListIndex].name }} 门诊ID:{{ patientList[patientListIndex].patientId }})
							</view>
						</view>
						<view class="information-popup-patient-add">
							<view class="information-popup-patient-item" v-for="(item, index) in patientList" :key="index" @click="changePatientListIndex(index)">
								<view class="information-popup-chose-patient" :class="index == patientListIndex? 'information-popup-chose-patient-active': ''">
									<view class="information-popup-chose-patient-text" :style="{'color': index != patientListIndex? '#00CC99':''}">
										{{ item.name | patientNameFilter}}
									</view>
								</view>
							</view>
							<view class="iconfont icon-addto" style="font-size: 50px; color: #00CC99;" />
						</view>
					</view>
					<view class="information-popup-button">
						<view class="information-popup-button-text">
							确认挂号
						</view>
					</view>
				</view>
			</my-uni-popup>
		</view>
		<view class="the-note" v-if="isVisit==false">
			<view class="note-container">
				<view class="note-item">
					擅长
					<view class="note-item-text">
						{{doctor.docterTC}}
					</view>
				</view>
				<view style="border-bottom: solid rgba(0,0,0,.2) 1px;margin-top: 20px;" />
				<view class="note-item">
					介绍
					<view class="note-item-text">
						{{doctor.doctorJS}}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import myUniPopup from '@/components/my-uni-popup/uni-popup'
	import timeChoseDoctor from '@/components/time-chose-doctor/time-chose-doctor.vue'
	export default {
		data() {
			return {
				doctor: {
					name: '沙小东',
					house: '空腔科专家(副)/副主任医师',
					docterTC: '业务专长：擅长牙体牙髓病的诊治，对根尖周炎、根管治疗及全口义齿、可摘局部义齿，烤瓷冠桥等修复治疗积累了丰富的临床经验；擅长运用活动和固定矫正器纠正各类错合畸形；对儿童口腔不良习惯、儿童牙齿替换异常、牙畸形的早期矫治，早失牙的间隙保持等治疗也有独到之处。',
					doctorJS: '个人简介：沙小冬，女，副主任医师，从事空腔临床一线工作20余年。',
					imageUrl: '../../static/img/icon/touxiang.jpeg' ,
				},
				isVisit: true,
				isTimeShow: true,
				timeShowIndex: 0,
				days: [{
						day: '21',
						has: true
					},
					{
						day: '22',
						has: false
					},
					{
						day: '23',
						has: true
					},
					{
						day: '24',
						has: true
					},
					{
						day: '25',
						has: true
					},
					{
						day: '26',
						has: true
					},
					{
						day: '27',
						has: true
					}
				],
				//就诊时间跟价格
				theTimeAndPrice: [{
						time: '上午08：00~08.30',
						price: 22.00
					},
					{
						time: '上午08：30~09.00',
						price: 22.00
					},
					{
						time: '上午09：30~10.00',
						price: 22.00
					},
					{
						time: '上午10：00~10.30',
						price: 22.00
					}
				],
				pupopTime: '',
				pupopTime2: '',
				pupopPrice: 0,
				patientList:[
					{
						name: '张三',
						patientId: 8722857
					},
					{
						name: '马的赛',
						patientId: 8121541
					}
				],
				patientListIndex: 0
			}
		},
		components: {
			myUniPopup,
			timeChoseDoctor
		},
		onShow() {
			uni.setNavigationBarColor({
				 frontColor: '#ffffff', // 必写项
				 backgroundColor: '#00CC99', // 必写项
			})
		},
		methods: {
			showPopup: function(index) {
				this.changePupop(index)
				this.$refs['popup'].open()
			},
			closePopup: function() {
				this.$refs['popup'].close()
			},
			theShowChange: function(value) {
				this.isTimeShow = value
			},
			theShowIndexChange: function(value) {
				this.timeShowIndex = value
			},
			changePupop: function(index) {
				let time1 = ''
				let date = new Date()
				date.setDate(date.getDate() + this.timeShowIndex)
				time1 = date.getFullYear() + '-' + (date.getMonth() + 1) + '-' + date.getDate()
				switch (date.getDay()) {
					case 0:
						time1 += ' 星期日 '
						break
					case 1:
						time1 += ' 星期一 '
						break
					case 2:
						time1 += ' 星期二 '
						break
					case 3:
						time1 += ' 星期三 '
						break
					case 4:
						time1 += ' 星期四 '
						break
					case 5:
						time1 += ' 星期五 '
						break
					case 6:
						time1 += ' 星期六 '
						break
					default:
						break
				}
				let temp = this.theTimeAndPrice[index].time
				time1 += temp.substring(0,2)
				this.pupopTime2 = temp.substring(2)
				this.pupopTime = time1
				this.pupopPrice = this.theTimeAndPrice[index].price
			},
			changePatientListIndex: function(index) {
				this.patientListIndex = index
			}
		},
		filters: {
			priceFilter: function(value) {
				return parseFloat(value).toFixed(2);
			},
			doctorTCfilter: function(value) {
				if (value.length > 48) {
					return value.substring(0, 47) + '...'
				}
				return value
			},
			patientNameFilter: function(value) {
				if(value.length > 2){
					return ((value.split("").reverse().join("")).substring(0,2)).split("").reverse().join("")
				}
				return value
			}
		}
	}
</script>

<style>
	.doctor-information {
		display: flex;
		flex-direction: column;
	}

	.doctor-information-top {
		display: flex;
		flex-direction: column;
		background-color: #00CC99;
	}

	.doctor-information-top-container {
		display: flex;
	}

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

	.doctor-information-top-doctor {
		width: 350rpx;
		display: flex;
		flex-direction: column;
		color: white;
		padding: 36rpx 0 0 0;
	}

	.doctor-information-top-doctor-name {
		font-size: 22px;
		padding-bottom: 16rpx;
	}

	.doctor-information-top-doctor-do {
		font-size: 14px;
	}

	.doctor-information-top-icon {
		width: 200rpx;
		align-content: center;
	}

	.doctor-information-top-icon {
		display: flex;
		justify-content: center;
		padding: 36rpx 0 0 0;
	}

	.doctor-information-top-myicon {
		color: white;
		margin: 0 2px 0 8px;
		font-size: 24px;
	}

	.doctor-information-top-text {
		width: 680rpx;
		align-self: center;
		color: white;
		font-size: 13px;
		margin-bottom: 38rpx;
	}

	.doctor-information-type {
		background-color: white;
		display: flex;
		justify-content: center;
	}

	.doctor-information-type-body {
		width: 320rpx;
		display: flex;
		justify-content: space-between;
	}

	.doctor-information-type-body-item {
		display: flex;
		justify-content: center;
		flex-direction: column;
		height: 80rpx;
		font-size: 14px;
	}

	.doctor-information-type-body-item-active {
		border-bottom: solid #00CC99 1px;
		color: #00CC99;
	}

	.doctor-information-type-body .register {
		align-self: center;
	}

	.doctor-information-type-body .introduce {
		align-self: center;
	}

	.doctor-information-time {
		display: flex;
		flex-direction: column;
		background-color: white;
		margin-top: 20rpx;
	}

	.time-chose {
		display: flex;
		justify-content: space-between;
		height: 80rpx;
		width: 680rpx;
		color: rgba(0, 0, 0, .5);
		align-self: center;
	}

	.doctor-information-bottom {
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	.doctor-information-bottom-body-strip {
		width: 680rpx;
		display: flex;
		justify-content: space-between;
		align-self: center;
		height: 90rpx;
	}

	.doctor-information-bottom-body {
		background-color: white;

		display: flex;
		justify-content: center;
	}

	.doctor-information-bottom-time {
		align-self: center;
	}

	.doctor-information-bottom-price {
		align-self: center;
	}

	.information-popup {
		display: flex;
		flex-direction: column;
	}

	.information-popup-doctor {
		display: flex;
		border-bottom: solid rgba(0, 0, 0, .2) 1px;
	}

	.doctor-information-text {
		width: 488rpx;
		margin: 40rpx 0 40rpx 0;
	}

	.information-popup-touxiang {
		margin: 40rpx 0 40rpx 0;
	}

	.doctor-information-text-item {
		width: 488rpx;
		margin: 8px 0 8px 0;
		display: flex;
		font-size: 16px;
	}

	.doctor-information-text-item-left {
		width: 100rpx;
		align-self: center;
	}

	.doctor-information-text-item-right {
		width: 388rpx;
		align-self: center;
		color: rgba(0, 0, 0, .5);
	}

	.doctor-information-close-icon {
		font-size: 24px;
		height: 24px;
		width: 24px;
		margin-top: 6px;
		margin-right: 6px;
	}

	.information-popup-patient {
		width: 680rpx;
		align-self: center;
		display: flex;
		flex-direction: column;
		font-size: 14px;
		margin-top: 30rpx;
	}

	.information-popup-patient-title {
		height: 26px;
		display: flex;
		font-size: 16px;
	}

	.information-popup-patient-note {
		height: 24px;
		display: flex;
		color: rgba(0, 0, 0, .5);
	}

	.information-popup-patient-item {
		display: flex;
		width: 60px;
	}

	.information-popup-chose-patient {
		height: 37px;
		width: 37px;
		border-radius: 37px;
		overflow: hidden;
		color: #00CC99;
		border: solid #00CC99 3px;
		align-self: center;
		display: flex;
		justify-content: center;
	}
	
	.information-popup-chose-patient-active{
		background-color: #00CC99;
	}
	
	.information-popup-patient-add {
		margin-bottom: 12px;
		margin-top: 6px;
		display: flex;
	}

	.information-popup-chose-patient-text {
		align-self: center;
		color: white;
	}

	.information-popup-button {
		width: 750rpx;
		height: 90rpx;
		background-color: #00D4B4;
		color: white;
		display: flex;
		justify-content: center;
	}

	.information-popup-button-text {
		align-self: center;
		font-size: 16px;
	}

	.the-note {
		display: flex;
		flex-direction: column;
		justify-content: center;
		background-color: white;
		margin-top: 20rpx;
	}

	.note-container {
		width: 680rpx;
		align-self: center;
		font-size: 16px;
		margin-bottom: 30px;
	}

	.note-item {
		margin-top: 32rpx;
	}

	.note-item-text {
		font-size: 15px;
		color: rgba(0, 0, 0, .5);
		margin-top: 3px;
	}
</style>
