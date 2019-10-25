<template>
	<view class="" style="display: flex;flex-direction: column;" >
		<view class="" style="height: 100px;width: 750rpx;background-color: red;z-index: 2;" @click="show2">
			
		</view>
		<view class="" style="height: 300px;z-index: 1;position: absolute;"@click="show3">
			<view class="" style="height: 100px;width: 750rpx;background-color: yellow;margin-top: 100px; z-index: 5;"  @click.stop="show">
				
			</view>
		</view>
		
		<view class="" style="height: 100px;width: 750rpx;background-color: green;margin-top: 100px;">
			
		</view>
	</view>
</template>

<script>
	export default {
		methods:{
			show:function(){
				console.log(111)
			},
			show2:function(){
				console.log(222)
			},
			show3:function(){
				console.log(3333)
			}
		}

	}
</script>

<style>
</style>
