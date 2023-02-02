<template>
	<view>
		<view class="btns">
			<button class="button popup-success" @click="messageToggle('success')"><text
					class="button-text success-text">成功</text></button>
			<button class="button popup-error" @click="messageToggle('error')"><text
					class="button-text error-text">失败</text></button>
			<button class="button popup-warn" @click="messageToggle('warn')"><text
					class="button-text warn-text">警告</text></button>
			<button class="button popup-info" @click="messageToggle('info')"><text
					class="button-text info-text">信息</text></button>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style scoped>
	.button {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		flex: 1;
		height: 35px;
		margin: 0 5px;
		border-radius: 5px;
	}

	.button-text {
		color: #fff;
		font-size: 12px;
	}

	.popup-success {
		color: #fff;
		background-color: #e1f3d8;
	}

	.popup-warn {
		color: #fff;
		background-color: #faecd8;
	}

	.popup-error {
		color: #fff;
		background-color: #fde2e2;
	}

	.popup-info {
		color: #fff;
		background-color: #f2f6fc;
	}

	.success-text {
		color: #09bb07;
	}

	.warn-text {
		color: #e6a23c;
	}

	.error-text {
		color: #f56c6c;
	}

	.info-text {
		color: #909399;
	}
</style>
