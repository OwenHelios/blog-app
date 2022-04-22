<template>
	<view>
		<main v-if="PageCur=='main'"></main>
		
		<view class="cu-bar tabbar bg-white shadow foot">
			<view class="action" @click="NavChange" data-cur="main">
				<view class='cuIcon-cu-image'>
					<image :src="'/static/main' + [PageCur=='main'?'_selected':''] + '.png'"></image>
				</view>
				<view :class="PageCur=='main'?'text-blue':'text-gray'">首页</view>
			</view>
			<view class="action" @click="NavChange" data-cur="quiz">
				<view class='cuIcon-cu-image'>
					<image :src="'/static/quiz' + [PageCur == 'quiz'?'_selected':''] + '.png'"></image>
				</view>
				<view :class="PageCur=='quiz'?'text-blue':'text-gray'">答题</view>
			</view>
			<view class="action add-action" @click="NavChange" data-cur="post">
				<view class='cuIcon-cu-image'>
					<image :src="'/static/post' + [PageCur == 'post'?'_selected':''] + '.png'"></image>
				</view>
				<view :class="PageCur=='post'?'text-blue':'text-gray'">发布</view>
			</view>
			<view class="action" @click="NavChange" data-cur="news">
				<view class='cuIcon-cu-image'>
					<image :src="'/static/news' + [PageCur == 'news'?'_selected':''] + '.png'"></image>
				</view>
				<view :class="PageCur=='news'?'text-blue':'text-gray'">资讯</view>
			</view>
			<view class="action" @click="NavChange" data-cur="me">
				<view class='cuIcon-cu-image'>
					<image :src="'/static/me' + [PageCur == 'me'?'_selected':''] + '.png'"></image>
				</view>
				<view :class="PageCur=='me'?'text-blue':'text-gray'">我的</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
		return {
				PageCur: 'main'
			}
		},
		methods: {
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur
			}
		}
	}
</script>

<style lang="scss">
</style>
