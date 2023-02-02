<template>
	<view class="login">
		<view class="content">
			<view class="logo-box">
				<image class="logo" src="../../static/uni.png" alt="logo.png"></image>
			</view>
			<uni-forms ref="form" :rules="formRules" :modelValue="formData">
				<uni-forms-item label="用户名" required name="username">
					<uni-easyinput v-model="formData.username" placeholder="请输入用户名" />
				</uni-forms-item>
				<uni-forms-item label="密码" required name="password">
					<uni-easyinput type="password" v-model="formData.password" placeholder="请输入密码" />
				</uni-forms-item>
				<uni-forms-item class="code-form" label="验证码" required name="code">
					<uni-easyinput type="digit" v-model="formData.code" placeholder="请输入验证码" />
					<!-- <image class="code" src="../../static/logo.png" alt="code.png"></image> -->
					<text class="code">{{base64Text}}</text>
				</uni-forms-item>
				<button type="default" plain="true" @click="submit()">登录</button>
				<view class="link">
					<!-- 可添加其他链接文字 -->
					<!-- <text></text> -->
					<text class="link-text" @click="handleForget">忘记密码?</text>
				</view>
			</uni-forms>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				base64Text: '',
				// 表单数据
				formData: {
					username: '',
					password: '',
					code: '',
				},
				formRules: {
					// 对name字段进行必填验证
					username: {
						rules: [{
								required: true,
								errorMessage: '请输入姓名',
							},
							{
								minLength: 6,
								maxLength: 20,
								errorMessage: '姓名长度在 {minLength} 到 {maxLength} 个字符',
							}
						]
					},
					password: {
						rules: [{
								required: true,
								errorMessage: '请输入密码',
							},
							{
								minLength: 6,
								maxLength: 18,
								errorMessage: '密码长度在 {minLength} 到 {maxLength} 个字符',
							}
						]
					},
					code: {
						rules: [{
							required: true,
							errorMessage: '请输入验证码',
						}]
					},
				},
			}
		},
		created() {
			this.generateCode()
		},
		methods: {
			generateCode() {
				let charaters = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
				let code = ''
				for (let i = 0; i < 4; i++) {
					let num = Math.floor(Math.random() * 61)
					code += charaters[num]
				}
				this.base64Text = code
			},
			// 触发提交表单
			submit() {
				// this.$refs.form.validate().then(res => {
				// 	console.log('表单数据信息：', res);
				// }).catch(err => {
				// 	console.log('表单错误信息：', err);
				// })
				uni.switchTab({
					url: '/pages/home/home'
				});
			},
			handleForget() {
				uni.navigateTo({
					url: '/pages/forget/forget'
				});
			},
		}
	}
</script>

<style scoped lang="scss">
	.login {
		// position: relative;
		width: 100%;
		height: calc(100vh - 44px);
		overflow: hidden;
		background-image: url(../../static/login.jpg);
		background-repeat: no-repeat;
		background-size: 100% 100%;

		.content {
			// position: absolute; // 严格居中对齐？
			// top: 40%;
			// right: 0;
			// left: 0;
			// transform: translateY(-50%);
			// padding: 0 10%;
			padding: 40% 10% 0;

			.logo-box {
				text-align: center;
			}

			.logo {
				height: 64px;
				width: 64px;
			}

			.link {
				height: 48px;
				line-height: 48px;
				// display: flex; // 以防增加其他文字按钮
				// justify-content: space-between;
				text-align: right;
			}

			.code-form {
				position: relative;
			}

			.code {
				position: absolute;
				width: 120px;
				height: 35px;
				top: 0;
				right: 0;
				// 文字样式-暂时
				text-align: center;
				line-height: 35px;
				color: #fff;
				font-size: 26px;
			}
		}
	}
</style>
