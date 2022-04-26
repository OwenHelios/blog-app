<template>
	<view>
		<cu-custom bgColor="bg-gradual-pink">
			<block slot="content">导航栏</block>
		</cu-custom>
		<view class="nav-wrapper" style="height: 90upx;">
		<scroll-view scroll-x class="bg-white nav fixed" :style="[{top:CustomBar + 'px'}]" scroll-with-animation :scroll-left="scrollLeft">
			<view class="cu-item" :class="index==TabCur?'text-green cur':''" v-for="(item,index) in 10" :key="index" @tap="tabSelect" :data-id="index">
				Tab{{index}}
			</view>
		</scroll-view>
		</view>
		<scroll-view enable-back-to-top scroll-y class="content-scroll">
			<article-card />
			<article-card />
			<article-card />
			<article-card />
			<article-card />
			<article-card />
			<article-card />
			<article-card />
			<view class="cu-tabbar-height"></view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				TabCur: 0,
				scrollLeft: 0,
				CustomBar: this.CustomBar
			}
		},
		onLoad() {

		},
		methods: {
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
			}
		}
	}
</script>

<style lang="scss">
	.content-scroll {
		padding: 10px;
	}
</style>
