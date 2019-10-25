<template>
	<view class="" style="display: flex; flex-direction: column;">
		<!-- 个人信息 -->
		<view class="box-show inspection-patient">
			<switch-patient :cardinfo="cardinfo" :isShowTip="true" :indexId="0" :defaultId="0"></switch-patient>
		</view>
		<view class="inspection-chose">
			<view class="inspection-chose-time" style="border-right: solid rgba(0,0,0,.1) 2rpx;">
				<my-select :list="mouthList" :initValue="0" ref="select1"></my-select>
			</view>
			<view class="inspection-chose-type" style="border-left: solid rgba(0,0,0,.1) 2rpx;">
				<my-select :list="typeList" :initValue="0"></my-select>
			</view>
		</view>
		<view class="inspection-strip box-show" v-for="(item, index) in inspectionList" @click="gotoInformation(item.type)">
			<view class="container">
				<view class="superscript">
					<view class="gradual" :style="{ background: 'linear-gradient(135deg, ' + jiaobiao[item.status] + ' 50%, transparent 50%)' }"></view>
					<view class="desc">{{ jiaobiaoText[item.type] }}</view>
				</view>
			</view>
			<view class="inspection-strip-container">
				<view class="inspection-strip-text">
					<view class="inspection-strip-text-left">
						<view class="inspection-strip-text-item">
							<view style="width: 122rpx;color: rgba(0,0,0,.5);">
								检验项目:
							</view>
							<view style="margin-left: 8rpx;">
								 {{ item.project }}
							</view>
						</view>
						<view class="inspection-strip-text-item">
							<view style="width: 122rpx;color: rgba(0,0,0,.5);">
								时&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;间: 
							</view>
							<view style="margin-left: 8rpx;">
								{{ item.time }}
							</view>
						</view>
					</view>
					<view class="inspection-strip-text-left" style="justify-content: center;">
						<view class="iconfont icon-next" style="align-self: center;"/>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
import mySelect from '@/components/my-select/xfl-select.vue';
import switchPatient from '@/components/switch-patient/switch-patient.vue';
export default {
	components: {
		switchPatient,
		mySelect
	},
	data() {
		return {
			cardinfo: [
				{
					name: '张三',
					cardid: '1548588'
				},
				{
					name: '李四',
					cardid: '00000'
				}
			],
			isMyWait: true,
			mouthList: [
				'全部', 
				'一周',
				'一月',
				'三月'
			],
			typeList: ['报告类型(不限)', '检查报告', '检验报告'],
			jiaobiao: [
				'#40de40',
				'#ff0101'
			],
			jiaobiaoText: [
				'检查',
				'检验'
			],
			inspectionList:[
				{
					type: 0,
					status: 0,
					time: '2019-10-14 11:31:17',
					project: '血常规+CRP'
				},
				{
					type: 1,
					status: 1,
					time: '2019-10-14 11:31:17',
					project: '血常规+CRP'
				}
			]
		}
	},
	methods:{
		gotoInformation: function (type){
			let url = ''
			if(type == 0){
				url = '../../inspection-test/inspection-test'
			}else if(type == 1){
				url = '../../inspection-information/inspection-information'	
			}
			uni.navigateTo({
				url: url
			})
		},
		closeSelect: function(){
			this.$refs.select1.myClose()
		}
	}
};
</script>

<style lang="scss">
$box_background_color: white; //框背景颜色
$box_radius: 4rpx; //框圆角
$box_width: 720rpx; //框高度
$box_margin: 16rpx 0 16rpx 0;

.box-show {
	background-color: $box_background_color;
	border-radius: $box_radius;
	width: $box_width;
	align-self: center;
}

.inspection-patient {
	display: flex;
	justify-content: center;
	align-self: center;
	margin: $box_margin;
}
.inspection-chose {
	display: flex;
	justify-content: center;
}
.inspection-strip {
	height: 140rpx;
	margin: 16rpx 0 0 0;
}
.inspection-strip-container{
	display: flex;
	height: 100%;
}

.inspection-strip-text{
	width: 560rpx;
	display: flex;
	justify-content: space-between;
	font-size: 28rpx;
	align-self: center;
	margin-left: 96rpx;
}
.inspection-strip-text-left{
	display: flex;
	height: 92rpx;
	flex-direction: column;
	justify-content: space-between;
}

.inspection-strip-text-item{
	margin: 2rpx 0 2rpx 0;
	display: flex;
}

.container {
	position: absolute;
	width: 90upx;
	height: 90upx;
	z-index: 11;
}

.superscript {
	position: absolute;
	top: 0px;
	left: 0px;
	width: 90upx;
	height: 90upx;
	overflow: hidden;
}

/* 使用背景色渐变 */
.superscript .gradual {
	width: 100%;
	height: 100%;
}

.superscript .desc {
	position: absolute;
	width: 100%;
	height: 100%;
	left: 10%;
	top: 10%;
	font-size: 18rpx;
	text-align: center;
	color: #fffdef;
	z-index: 1;
	transform: rotate(-45deg);
}
</style>
