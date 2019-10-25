<template>
	<view>
		<uni-search-bar placeholder="搜索科室、医生" clearButton="auto" @confirm="search"></uni-search-bar>
	</view>
</template>

<script>
	import uniSearchBar from '@dcloudio/uni-ui/lib/uni-search-bar/uni-search-bar'
	import uicon from '@dcloudio/uni-ui/lib/uni-icons/uni-icons'
	export default {
		components:{
			uniSearchBar
		}
	}
</script>

<style>
</style>
