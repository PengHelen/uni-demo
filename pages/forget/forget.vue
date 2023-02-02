<template>
	<view class="forget">
		<uni-forms ref="forgetForm" :rules="forgetFormRules" :modelValue="forgetFormData" err-show-type="toast"
			:label-width="80">
			<uni-forms-item label="旧密码" required name="oldPassword">
				<uni-easyinput type="password" v-model="forgetFormData.oldPassword" placeholder="请输入旧密码" clearable />
			</uni-forms-item>
			<uni-forms-item label="密码" required name="newPassword">
				<uni-easyinput type="password" v-model="forgetFormData.newPassword" placeholder="请输入新密码" clearable />
			</uni-forms-item>
			<uni-forms-item label="确认密码" required name="confirm">
				<uni-easyinput type="password" v-model="forgetFormData.confirm" placeholder="请再次输入密码" clearable
					@input="handleConfirm" />
			</uni-forms-item>
			<button type="default" plain="true" @click="submit()">提交</button>
		</uni-forms>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// 表单数据
				forgetFormData: {
					oldPassword: '',
					newPassword: '',
					confirm: '',
				},
				forgetFormRules: {
					// 对name字段进行必填验证
					oldPassword: {
						rules: [{
							required: true,
							errorMessage: '请输入旧密码',
						}]
					},
					newPassword: {
						rules: [{
							required: true,
							errorMessage: '请输入新密码',
						}]
					},
					confirm: {
						rules: [{
							required: true,
							errorMessage: '请再次输入密码',
						}]
					},

				},
			}
		},
		methods: {
			submit() {
				this.$refs.forgetForm.validate().then(res => {
					console.log('表单数据信息：', res);
				}).catch(err => {
					console.log('表单错误信息：', err);
				})
			},
			handleConfirm(e) {
				console.log('eeeeee', e)
			},
		}
	}
</script>

<style lang="scss" scoped>
	.forget {
		padding: 40% 10% 0;
	}
</style>
