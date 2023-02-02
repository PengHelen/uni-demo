<template>
	<view>
		<uni-list>
			<uni-list-item v-for="(item,index) in shopList" :key="index" :index="index" :title="item.title"
				:note="`¥${item.num}`" thumb="https://web-assets.dcloud.net.cn/unidoc/zh/unicloudlogo.png"
				thumb-size="lg" :rightText="`x${item.num}`" />
		</uni-list>
		<uni-goods-nav class="pay" :fill="true" :options="options" :button-group="customButtonGroup1" @click="onClick"
			@buttonClick="buttonClick" />
	</view>
</template>

<script>
	export default {
		data() {
			return {
				shopList: [{
					title: '麻辣火锅',
					price: 45,
					num: 4,
				}, {
					title: '椰汁鸡肉',
					price: 32,
					num: 6,
				}, {
					title: '美蛙鱼头',
					price: 50,
					num: 2,
				}],
				options: [{
					icon: 'wallet-filled',
					text: '￥56'
				}],
				customButtonGroup1: [{
					text: '立即购买',
					backgroundColor: 'linear-gradient(90deg, #FE6035, #EF1224)',
					color: '#fff'
				}]
			}
		},
		methods: {
			onClick(e) {
				uni.showToast({
					title: `点击${e.content.text}`,
					icon: 'none'
				})
			},
			buttonClick(e) {
				console.log(e)
				this.options[2].info++
			}
		}
	}
</script>

<style scoped lang="scss">
	.pay {
		position: fixed;
		right: 0;
		left: 0;
		bottom: 0;
		background-color: #fff;
	}
</style>
