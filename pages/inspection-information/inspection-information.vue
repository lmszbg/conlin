<template>
	<view class="inspection-information">
		<view class="box-show inspection-information-top">
			<view class="inspection-information-top-left">
				<view class="inspection-information-top-item">
					患者姓名：孔令周
				</view>
				<view class="inspection-information-top-item">
					报告单号：20191014G0520410
				</view>
				<view class="inspection-information-top-item">
					检验名称：血常规+CRP
				</view>
				<view class="inspection-information-top-item">
					检查时间：2019-10-14 11:31:17
				</view>
			</view>
			<view class="inspection-information-top-right">
				<view style="height: 62rpx;align-self: flex-end;display: flex;">
					<view style="display: flex;justify-content: space-between;height: 40rpx;" @click="gotoTimeInformation">
						<view class="">
								进度详情
						</view>
						<view class="iconfont icon-next" style="align-self: center; font-size: 28rpx;"/>
					</view>
				</view>
			</view>
		</view>
		<view class="inspection-promting">
			<view class="">
				以下检验结果仅供参考，实际以医院检验单为准！
			</view>
		</view>
		<view class="box-show inspection-body">
			<view class="inspection-body-title">
				<view class="inspection-body-title-text">
					<view class="inspection-body-item1">
						检查项目
					</view>
					<view class="inspection-body-item2">
						参考范围
					</view>
					<view class="inspection-body-item3">
						结果
					</view>
				</view>
			</view>
			<view class="inspection-body-strip" v-for="(item, index) in list">
				<view class="inspection-body-strip-text">
					<view class="inspection-body-item1">
						{{ item.project }}
					</view>
					<view class="inspection-body-item2">
						{{ item.promting }}
					</view>
					<view class="inspection-body-item3">
						{{ item.result }}
					</view>
					<view v-if="item.status==0" class="iconfont icon-arrow-up-" style="color: red; font-size: 28rpx;"/>
					<view v-if="item.status==1" class="iconfont icon-arrow-down-" style="color: #4CD964;font-size: 28rpx;"/>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [
					{
						project: '白细胞',
						promting: '4.0-10.0',
						result: '7.710^9/L',
						status: 0
					},{
						project: '中性粒细胞%',
						promting: '46.50-76.50',
						result: '70.40%',
						status: 1
					},{
						project: '淋巴细胞%',
						promting: '18.70-47.00',
						result: '3.80%',
						status: 1
					},{
						project: '单核细胞%',
						promting: '2.00-12.00',
						result: '25.70%',
						status: -1
					},{
						project: '嗜酸性粒细胞%',
						promting: '0.00-6.00',
						result: '0.10%',
						status: 0
					}	
				]
			}
		},
		methods:{
			gotoTimeInformation: function () {
				uni.navigateTo({
					url: '../inspection-information-time/inspection-information-time'
				})
			}
		}
	}
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
	.inspection-information{
		display: flex;
		flex-direction: column;
	}
	
	.inspection-information-top{
		margin-top: 16rpx;
		display: flex;
	}
	
	.inspection-information-top-left{
		padding: 20rpx 0px 20rpx 20rpx;
		width: 530rpx;
		font-size: 28rpx;
	}
	.inspection-information-top-item{
		display: flex;
		padding: 4rpx 0 4rpx 0;
	}
	.inspection-information-top-right{
		font-size: 28rpx;
		width: 150rpx;
		display: flex;
	}
	.inspection-promting{
		font-size: 24rpx;
		width: 680rpx;
		align-self: center;
		color: red;
		margin-top: 20rpx;
		margin-bottom: 20rpx;
	}
	.inspection-body{
		font-size: 28rpx;
		display: flex;
		flex-direction: column;
	}
	.inspection-body-title{
		display: flex;
		padding: 0 20rpx 0 20rpx;
		height: 60rpx;
		border-bottom: solid rgba(0,0,0,.2) 1px;
		background-color: #00CC99;
		border-top-left-radius: $box_radius;
		border-top-right-radius: $box_radius;
	}
	.inspection-body-title-text{
		display: flex;
		align-self: center;
	}
	.inspection-body-item1{
		width: 280rpx;
	}
	.inspection-body-item2{
		width: 200rpx;
	}
	.inspection-body-item3{
		width: 160rpx;
	}
	.inspection-body-strip{
		display: flex;
		padding: 0 20rpx 0 20rpx;
		height: 60rpx;
	}
	.inspection-body-strip-text{
		display: flex;
		align-self: center;
	}
</style>
