<template>
	<view class="quiz-wrapper">
		<cu-custom bgColor="bg-gradual-pink">
			<block slot="content">导航栏</block>
			<view slot="right"><text class="cuIcon-add"></text></view>
		</cu-custom>
		<view class="quiz-wrapper">
			<swiper class="quiz-swiper" :current="currentIndex" @change="handleSwipe">
				<swiper-item class="quiz-swiper-item" v-for="(item,index) in quizList" :key="index">
					<quiz-card :quizItem='item' @select-answer="handleAnswer"/>
				</swiper-item>
			</swiper>
			<view class="">
				{{currentIndex}}
			</view>
			<!-- <view class="cu-progress">
				<view class="bg-red" :style="[{ width:loading?'61.8%':''}]">61.8%</view>
			</view> -->
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
				currentIndex: 0
			}
		},
		methods:{
			handleAnswer(){
				
			},
			handleSwipe(e){
				this.currentIndex = e.detail.current
			}
		}
	}
</script>

<style lang="scss">
	.quiz-wrapper {
		height: 100%;

		.quiz-swiper {
			height: 100%;

			.quiz-swiper-item {
				display: flex;
				align-items: start;
				justify-content: center;
			}
		}
	}
</style>
