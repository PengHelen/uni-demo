<template>
	<view class="container">
		<view>
			<uni-calendar :lunar="true" ref="calendar" :insert="false" @confirm="confirm" />
			<button @click="open">打开日历</button>
		</view>
		<uni-collapse ref="collapse">
			<uni-collapse-item title="折叠内容">
				<view class="content">
					<uni-list>
						<uni-list-item title="列表文字"></uni-list-item>
						<uni-list-item :disabled="true" title="列表禁用状态"></uni-list-item>
						<uni-list-item title="列表文字" note="列表描述信息"></uni-list-item>
						<uni-list-item :disabled="true" title="列表文字" note="列表禁用状态"></uni-list-item>
						<uni-list-item title="列表右侧显示 switch" :show-switch="true" @switchChange="switchChange">
						</uni-list-item>
					</uni-list>
				</view>
			</uni-collapse-item>
		</uni-collapse>
		<uni-icons type="color" size="30"></uni-icons>
		<uni-link href="https://penghelen.github.io/" text="Helen Peng"></uni-link>
		<uni-group title="card 简介" mode="card">
			<view> 第一行文字 </view>
			<view> 第二行文字 </view>
		</uni-group>
		<uni-data-picker :localdata="classes" popup-title="请选择班级" @change="onchange" @nodeclick="onnodeclick">
		</uni-data-picker>
		<view class="uni-padding-wrap uni-common-mt">
			<uni-segmented-control :current="current" :values="items" :style-type="styleType"
				:active-color="activeColor" @clickItem="onClickItem" />
		</view>
		<uni-load-more :status="status" :content-text="contentText" />
		<uni-steps :options="list1" :active="active" />
	</view>
</template>

<script>
	export default {
		data() {
			return {
				candidates: ['北京', '南京', '东京', '武汉', '天津', '上海', '海口'],
				city: '',
				classes: [{
						text: "一年级",
						value: "1-0",
						children: [{
								text: "1.1班",
								value: "1-1"
							},
							{
								text: "1.2班",
								value: "1-2"
							}
						]
					},
					{
						text: "二年级",
						value: "2-0"
					},
					{
						text: "三年级",
						value: "3-0"
					}
				],
				modeIndex: -1,
				styleIndex: -1,
				current: 0,
				items: ['选项卡1', '选项卡2', '选项卡3'],
				styles: [{
						value: 'button',
						text: '按钮',
						checked: true
					},
					{
						value: 'text',
						text: '文字'
					}
				],
				colors: ['#007aff', '#4cd964', '#dd524d'],
				current: 0,
				colorIndex: 0,
				activeColor: '#007aff',
				styleType: 'text',
				status: 'more',
				contentText: {
					contentdown: '查看更多',
					contentrefresh: '加载中',
					contentnomore: '没有更多'
				},
				active: 1,
				list1: [{
					title: '事件一'
				}, {
					title: '事件二'
				}, {
					title: '事件三'
				}, {
					title: '事件四'
				}],
			}
		},
		methods: {
			open() {
				this.$refs.calendar.open();
			},
			confirm(e) {
				console.log(e);
			},
			change(e) {
				this.current = e.detail.current
			},
			selectStyle(index) {
				this.dotsStyles = this.dotStyle[index]
				this.styleIndex = index
			},
			selectMode(mode, index) {
				this.mode = mode
				this.modeIndex = index
				this.styleIndex = -1
				this.dotsStyles = this.dotStyle[0]
			},
			onBanner(index) {
				console.log(22222, index);
			},
			onClickItem(e) {
				if (this.current !== e.currentIndex) {
					this.current = e.currentIndex
				}
			},
			styleChange(e) {
				if (this.styleType !== e.detail.value) {
					this.styleType = e.detail.value
				}
			},
			colorChange(e) {
				if (this.styleType !== e.detail.value) {
					console.log(e.detail.value);
					this.activeColor = e.detail.value
				}
			},
			onchange(e) {
				const value = e.detail.value
			},
			onnodeclick(node) {},
		}
	}
</script>

<style>
	.container {
		padding: 44px 8px 60px;
		font-size: 14px;
		line-height: 24px;
		height: calc(100vh - 104px);
		overflow-y: auto;
	}
</style>
