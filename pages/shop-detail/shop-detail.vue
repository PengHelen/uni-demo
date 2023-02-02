<template>
	<view>
		<uni-card :cover="cover">
			<view class="tag-view">
				<uni-tag :inverted="true" text="萌宠" type="error" />
			</view>
			<uni-section class="mb-10" title="猫咪" sub-title="两只小猫咪,白色和棕猫">
				<template v-slot:right>
					<uni-number-box :value="1" />
				</template>
			</uni-section>
		</uni-card>
		<view class="goods-carts">
			<uni-goods-nav :options="options" :fill="true" :button-group="buttonGroup" @click="onIconClick"
				@buttonClick="buttonClick" />
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				options: [{
					icon: 'shop',
					text: '店铺',
					info: 2,
					infoBackgroundColor: '#007aff',
					infoColor: "#f5f5f5"
				}, {
					icon: 'cart',
					text: '购物车',
					info: 2
				}],
				buttonGroup: [{
						text: '加入购物车',
						backgroundColor: 'linear-gradient(90deg, #FFCD1E, #FF8A18)',
						color: '#fff'
					},
					{
						text: '立即购买',
						backgroundColor: 'linear-gradient(90deg, #FE6035, #EF1224)',
						color: '#fff'
					}
				],
				cover: 'https://web-assets.dcloud.net.cn/unidoc/zh/shuijiao.jpg',
				avatar: 'https://web-assets.dcloud.net.cn/unidoc/zh/unicloudlogo.png',
				extraIcon: {
					color: '#4cd964',
					size: '22',
					type: 'gear-filled'
				}
			}
		},
		methods: {
			buttonClick(e) {
				this.options[2].info++
			},
			onIconClick(e) {
				if (e.index == 0) {
					uni.navigateBack({
						delta: 1
					})
				}
				if (e.index == 1) {
					uni.navigateTo({
						url: '/pages/cart/cart'
					})
				}
			},
			
		}
	}
</script>

<style scoped>
	.goods-carts {
		background-color: #fff;
		position: fixed;
		bottom: 0;
		left: 0;
		right: 0;
		z-index: 1;
	}
</style>
