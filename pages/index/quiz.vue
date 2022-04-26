<template>
	<view class="page">
		<cu-custom bgColor="bg-gradual-pink">
			<block slot="content">导航栏</block>
			<view slot="right"><text class="cuIcon-add"></text></view>
		</cu-custom>
		<view>
			<img class="quiz-banner" src="/static/horizontal-banner-ps-3.jpg" alt="banner" mode='aspectFit'>
		</view>
		<view class="quiz-wrapper">
			<swiper class="quiz-swiper" :current="currentIndex" @change="handleSwipe">
				<swiper-item class="quiz-swiper-item" v-for="(item,index) in quizList" :key="index">
					<quiz-card :quizItem='item' @select-answer="handleAnswer"/>
				</swiper-item>
			</swiper>
			<view class="quiz-info">
				
			
			<view class="cu-progress" style="width: 80%;margin-left: 10px;">
				<view class="bg-red" :style="[{ width:loading?progress:''}]">{{progress}}</view>
			</view>
			<view class="">
				当前分数：2/10
			</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				quizList: [{
					question: 'Lorem?',
					answers: ['firevase', 'firevase', 'firevase', 'firevase'],
					correctAnswer: 0
				}, {
					question: 'Lorem?',
					answers: ['firevase', 'firevase', 'firevase', 'firevase'],
					correctAnswer: 2
				}, {
					question: 'Lorem?',
					answers: ['firevase', 'firevase', 'firevase', 'firevase'],
					correctAnswer: 2
				}, {
					question: 'Lorem?',
					answers: ['firevase', 'firevase', 'firevase', 'firevase'],
					correctAnswer: 2
				}, {
					question: 'Lorem?',
					answers: ['firevase', 'firevase', 'firevase', 'firevase'],
					correctAnswer: 2
				}],
				currentIndex: 0,
				loading: true,
			}
		},
		methods:{
			handleAnswer(){
				
			},
			handleSwipe(e){
				this.currentIndex = e.detail.current
			}
		},
		computed:{
			progress(){
				return (this.currentIndex / this.quizList.length) * 100 + '%'
			}
		}
	}
</script>

<style lang="scss" scoped>
	.page {
		height: 100%;
		display: flex;
		flex-direction: column;
		.quiz-banner {
			height: 95px;
		}
	.quiz-wrapper {
		flex-grow: 1;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		.quiz-swiper {
			height: 250px;

			.quiz-swiper-item {
				display: flex;
				align-items: flex-start;
				justify-content: center;
			}
		}
	}}
</style>
