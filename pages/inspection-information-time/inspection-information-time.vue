<template>
	<view class="inspection-information-time">
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
		</view>
		<view class="time-body">
			<view class="" v-for="(item,index) in list" :style="{'margin-top':index!=0?'-30rpx':''}" style="display: flex;font-size: 28rpx;">
				<view class="time-shijianzhou" >
					<view class="yuan" :class="{'yuan-active': item.type==1}"></view>
					<view class="xian" :class="{'xian-active': index+1<list.length&&list[index+1].type==1}"  :style="{'display':index==list.length-1?'none':''}"></view>
				</view>
				<view class="" style="margin-top: 20rpx;" :style="{'color': item.type==1?'#5ff12b':''}">
					{{ item.note }}
				</view>
				<view class="time-text" >
					<view style="display: flex;">
						<view class="">
							送检医生:
						</view>
						<view style="margin-left: 16rpx;">
							{{ item.doctor }}
						</view>
					</view>
					<view style="margin-top: 8rpx;display: flex;">
						<view class="">
							时&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;间:
						</view>
						<view  style="margin-left: 16rpx;">
							{{ item.time }}
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				list: [
					{
						type: 1,
						time: '2019-11-2 2:11:37',
						note: '已收集',
						doctor: '周通'
					},{
						type: 1,
						time: '2019-11-2 2:11:37',
						note: '已收集',
						doctor: '周通'
					},{
						type: 0,
						time: '2019-11-2 2:11:37',
						note: '未收集',
						doctor: '周通'
					}
					
				]
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
	.inspection-information-time{
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
	.yuan{
		height: 28rpx;
		width: 28rpx;
		border-radius: 28rpx;
		align-self: center;
		background-color: #adadad
	}
	.yuan-active{
		background-color: #5ff12b;
	}
	.xian{
		height: 150rpx;
		width: 4rpx;
		background-color: #adadad;
		align-self: center;
	}
	.xian-active{
		background-color: #5ff12b;
	}
	.time-body{
		border-radius: $box_radius;
		width: $box_width;
		align-self: center;
		margin-top: 30rpx;
		font-size: 28rpx;
	}
	.time-shijianzhou{
		display: flex;
		flex-direction: column;
		margin-top: 26rpx;
		width: 100rpx;
	}
	.time-text{
		background-color: white;
		width: 456rpx;
		margin-left: 40rpx;
		padding: 20rpx;
		height: 80rpx;
	}
</style>
