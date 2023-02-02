<template>
	<view>
		<uni-list>
			<uni-list-item v-for="(item,index) in shopList" :key="index" :index="index" :title="item.title"
				:note="item.description" showArrow thumb="https://web-assets.dcloud.net.cn/unidoc/zh/unicloudlogo.png"
				thumb-size="lg" rightText="详情" @click="handleClick()" :clickable="true" />
		</uni-list>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				shopList: [{
					title: '麻辣火锅',
					description: '正宗川味火锅',
				}, {
					title: '椰汁鸡肉',
					description: '海南椰汁炖鸡',
				}, {
					title: '美蛙鱼头',
					description: '渝味鱼肉',
				}],
			}
		},
		methods: {
			handleClick(data) {
				console.log('data', data)
				uni.navigateTo({
					url: '/pages/shop-detail/shop-detail'
				})
			},
		}
	}
</script>

<style>

</style>
