<template>
	<view class="inspection">
		<view class="box-show inspection-test">
			<view class="test-title">
				计算机图文报告
			</view>
			<view class="test-body">
				<view class="test-strip">
					<view class="test-strip-left">
						检查部位
					</view>
					<view class="test-strip-right">
						子宫附件（经阴道）
					</view>
				</view>
				<view class="test-strip">
					<view class="test-strip-left">
						检查时间
					</view>
					<view class="test-strip-right">
						2010-05-26 14:27:53
					</view>
				</view>
				<view class="test-strip">
					<view class="test-strip-left">
						检查所见
					</view>
					<view class="test-strip-right">
						子宫前位，大小正常，宫腔分离0.3cm，内见液性暗区，内膜不明显，肌层回声均匀。左侧卵巢大小形态正常，右卵巢可见-4.7*3.4cm液性暗区。彩色血流信号未明显异常。
					</view>
				</view>
				<view class="test-strip">
					<view class="test-strip-left">
						检查结果
					</view>
					<view class="test-strip-right">
						右卵巢嚢肿
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
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
	.inspection{
		display: flex;
		flex-direction: column;
	}
	.inspection-test{
		margin: $box_margin;
		align-self: center;
	}
	.test-title{
		padding: 20rpx 20rpx 20rpx 20rpx;
		font-size: 36rpx;
		font-weight: 600;
		border-bottom: solid rgba(0,0,0,.2) 2rpx;
	}
	.test-body{
		font-size: 28rpx;
		padding: 20rpx 20rpx 20rpx 20rpx;
	}
	.test-strip{
		display: flex;
		margin: 20rpx 0 20rpx 0;
	}
	.test-strip-left{
		width: 180rpx;
		color: rgba(0,0,0,.5);
	}
	.test-strip-right{
		width: 500rpx;
	}
</style>
