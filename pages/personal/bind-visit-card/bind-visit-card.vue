<template>
	<view class="container">
		<view class="notice-bar">
			<uni-notice-bar :text='noticeBar'></uni-notice-bar>
		</view>
		<view class="bind-visit-form-type">
			<view class="bind-visit-form-type-body">
				<view id="adult-type" :class="[bindTypeIsAudlt ? 'bind-visit-person-type-active' : '', 'bind-visit-person-type-adult']"
				 @click="changeBindType">
					成人
				</view>
				<view id="children-type" :class="[bindTypeIsAudlt==false ? 'bind-visit-person-type-active' : '', 'bind-visit-person-type-children']"
				 @click="changeBindType">
					儿童
				</view>
			</view>
		</view>
		<view class="bind-visit-form">
			<view class="bind-visit-form-strips">
				<view class="bind-visit-form-strip">
					<view class="bind-visit-form-strip-left">
						姓名
					</view>
					<view class="bind-visit-form-strip-right">
						<input type="text" value="" placeholder="请输入姓名" />
					</view>
				</view>
				<view class="bind-visit-form-strip">
					<view class="bind-visit-form-strip-left">
						身份证
					</view>
					<view class="bind-visit-form-strip-right">
						<input type="idcard"  placeholder="请输入身份证号" maxlength="18"/>
					</view>
				</view>
				<view class="bind-visit-form-strip">
					<view class="bind-visit-form-strip-left">
						手机号
					</view>
					<view class="bind-visit-form-strip-right " style="width: 300rpx;">
						<input  type="number"  placeholder="请输入手机号" maxlength="11" />
					</view>
					<view class="bind-visit-form-strip-right-verification" @click="changeVerfication">
						<text>{{ verficationInfo }}</text>
					</view>
				</view>
				<view class="bind-visit-form-strip">
					<view class="bind-visit-form-strip-left">
						请输入验证码
					</view>
					<view class="bind-visit-form-strip-right">
						<input type="number" value="" placeholder="请输入验证码" maxlength="6"/>
					</view>
				</view>
				<view class="bind-visit-form-strip" style="border-bottom: none;">
					<view class="bind-visit-form-strip-left">
						家庭住址
					</view>
					<view class="bind-visit-form-strip-right">
						<input type="text" value="" placeholder="请输入家庭住址" />
					</view>
				</view>
			</view>
		</view>
		<view class="bind-visit-info">
			<view class="bind-visit-info-text">
				{{ bindVisitInfo[bindVisitInfoShow] }}
			</view>
		</view>
		<view class="bind-visit-foot">
			<button class="bind-visit-button" @click="bindCard">立即绑定</button>
		</view>
	</view>
</template>

<script>
	import uniNoticeBar from '@/components/notice-bar/uni-notice-bar.vue'

	export default {
		components: {
			uniNoticeBar,
		},
		data() {
			return {
				noticeBar: "本院实行实名制就诊,请如实填写就诊人信息,如因信息错误产生的一切后果自行负责。",
				bindTypeIsAudlt: true,
				bindVisitInfoShow: 0,
				bindVisitInfo: [
					"我们将根据您的个人真实信息,为您分配新的诊疗卡。为方便您的就诊,请如是填写你的个人信息。",
					"如果儿童暂时没有身份证号码,请携带儿童到医院挂号处挂号。"
				],
				verficationInfo: "获取验证码",
				isClickVerfication: false,
				verficationInterval: null,
				verficationNowTime: 3,
			}
		},
		watch:{
			bindTypeIsAudlt(newValue, oldValue){
				if(newValue == true){
					this.bindVisitInfoShow = 0
				}else{
					this.bindVisitInfoShow = 1
				}
			}
		},
		methods: {
			changeBindType: function(el) {
				let type = el.currentTarget.id
				if (type === "adult-type")
					this.bindTypeIsAudlt = true
				else
					this.bindTypeIsAudlt = false
			},
			changeVerfication: function(){
				if(this.isClickVerfication === false){
					this.isClickVerfication = true
					uni.showToast({
						title:"验证码已发送"
					})
					this.verficationInterval = setInterval( () => {
						this.verficationNowTime = this.verficationNowTime -1
						this.verficationInfo = this.verficationNowTime+"S"
						if(this.verficationNowTime === 0){
							this.isClickVerfication = false
							this.verficationInfo = "获取验证码"
							this.verficationNowTime = 3
							clearInterval(this.verficationInterval)
						}
					}, 1000)
				}
			},
			bindCard: function() {
				uni.showToast({
					title:"绑定成功"
				})
			},
		},
		mounted() {
			
		}
	}
</script>

<style lang="scss" scoped>
	page {
		background-color: #EEEEEE;
	}
	.container{
		background-color: #EEEEEE;
	}
	
	.bind-visit-form-type {
		display: flex;
		justify-content: center;
		height: 70rpx;
		border-bottom: solid rgba(0, 0, 0, 0.4) 1rpx;
		background-color: white;
		padding-top: 20rpx;
	}

	.bind-visit-form-type-body {
		display: flex;
		width: 490rpx;
	}

	.bind-visit-person-type-adult {
		font-size: 36rpx;
	}

	.bind-visit-person-type-children {
		margin-left: auto;
		font-size: 36rpx;
	}

	.bind-visit-person-type-active {
		border-bottom: solid rgba(0,204,153,.7) 4rpx;
		color: rgba(0,204,153,.7);
	}

	.bind-visit-form {
		display: flex;
		align-items: center;
		flex-direction: column;
		background-color: white;
	}
	.bind-visit-form-strip {
		display: flex;
		align-items: center;
		width: 700rpx;
		height: 100rpx;
		border-bottom: solid rgba(0, 0, 0, 0.2) 1rpx;
	}

	.bind-visit-form-strip-left {
		width: 220rpx;
		font-size: 30rpx;
	}

	.bind-visit-form-strip-right {
		width: 430rpx;
	}
	
	.bind-visit-info{
		display: flex;
		justify-content: center;
		margin: 50rpx 0 50rpx 0;
	}
	.bind-visit-info-text{
		font-size: 30rpx;
		color: #888888;
		width: 700rpx;
	}
	.bind-visit-foot{
		display: flex;
		justify-content: center;
	}
	.bind-visit-button{
		width: 680rpx;
		background-color: rgba(0,204,153,.7);
		color: white;
	}
	.bind-visit-form-strip-right-verification{
		display: flex;
		font-size: 30rpx;
		width: 150rpx;
		justify-content: center;
	}

</style>
