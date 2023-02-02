<template>
	<view>
		<uni-notice-bar class="bar" show-icon scrollable text="这是一条滚动提示信息" />
		<uni-swiper-dot class="swipers" @clickItem="clickItem" :info="info" :current="current" :mode="mode"
			:dots-styles="dotsStyles" field="content">
			<swiper @change="change" :current="swiperDotIndex">
				<swiper-item v-for="(item, index) in 3" :key="index">
					<view class="swiper-item" :class="'swiper-item' + index">
						<text style="color: #fff; font-size: 32px;">{{index+1}}</text>
					</view>
				</swiper-item>
			</swiper>
		</uni-swiper-dot>
		<uni-grid :column="3" :highlight="true" :showBorder="false" @change="change">
			<uni-grid-item v-for="(item, index) in list" :index="index" :key="index">
				<view class="grid-item-box" @click="handleClick(item)">
					<uni-icons :type="item.icon" :size="30" color="#777" />
					<text class="text">{{item.text}}</text>
				</view>
			</uni-grid-item>
		</uni-grid>
		<uni-popup ref="message" type="message">
			<uni-popup-message :type="msgType" :message="messageText" :duration="2000"></uni-popup-message>
		</uni-popup>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swiperDotIndex: 0,
				mode: 'default',
				dotsStyles: {},
				info: [],
				current: 0,
				list: [{
						icon: 'shop-filled',
						text: '商店',
						path: 'shop',
					},
					{
						icon: 'images-filled',
						text: '图库',
						path: 'images',
					},
					{
						icon: 'chat-filled',
						text: '讨论',
						path: 'index',
					},
					{
						icon: 'contact',
						text: '联系人',
						path: 'index',
					}
				],
				type: 'center',
				msgType: 'success',
				messageText: '这是一条成功提示'
			}
		},
		created() {
			uni.setTabBarBadge({
				index: 0,
				text: ''
			})
		},
		methods: {
			clickItem(e) {
				this.swiperDotIndex = e
			},
			change(e) {
				this.current = e.detail.current
			},
			handleClick(data) {
				console.log('data', data)
				uni.navigateTo({
					url: `/pages/${data.path}/${data.path}`
				})
				if (data.path == 'index') {
					let arrays = ['success', 'error', 'warn', 'info']
					let index = Math.floor(Math.random() * 4)
					this.msgType = arrays[index]
					this.messageText = `这是一条${arrays[index]}消息提示`
					this.$refs.message.open()
				}
			},
		}
	}
</script>

<style>
	.bar {
		position: fixed;
		top: 44px;
		left: 0;
		right: 0;
		z-index: 1;
	}

	.swipers {
		margin-top: 44px;
	}

	.swiper-item {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 200px;
		color: #fff;
	}

	.swiper-item0 {
		background-color: #cee1fd;
	}

	.swiper-item1 {
		background-color: #b2cef7;
	}

	.swiper-item2 {
		background-color: #cee1fd;
	}

	.grid-item-box {
		flex: 1;
		// position: relative;
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: column;
		align-items: center;
		justify-content: center;
		padding: 15px 0;
	}
</style>
