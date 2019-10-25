<template>
	<view class="registration">
		<!-- 左边 -->
		<!-- 图标 -->
		<view class="registration-icon-container">
			<!-- <svg class="icon registration-icon" aria-hidden="true">
			  <use xlink:href="#icon-Stone-add-circle"></use>
			</svg> -->
		</view>
		<!-- 数据排列 -->
		<view class="registration-note">
			<!-- 挂号是否成功 -->
			<view class="registration-note-title">
				{{ msg }}
			</view>
			<!-- 就诊人 -->
			<view class="">
				{{ people }}
			</view>
			<!-- 医生 -->
			<view class="">
				{{ doctor }}
			</view>
		</view>
		<!-- 右边 -->
		<view class="">
			<view class="">
				就诊时间
			</view>
			<view>
				{{ time }}
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				msg: "取消挂号成功",
				people: "张某某",
				doctor: "皮肤科专家[副]/季晓红",
				time: "2019-10-21"
			}
		}
	}
</script>

<style>
	.registration{
		display: flex;
		background-color: red;
		height: 170rpx;
	}
	.registration-note{
		display: flex;
		flex-direction: column;
	}
	.registration-note-title{
		font-size: 32rpx;
	}
	.registration-note-text{
		
	}
	.registration-icon{
		font-size: 80rpx;
	}
	.registration-icon-container{
		display: flex;
		align-items: center;
		width: 110rpx;
		justify-content: center;
	}
</style>
