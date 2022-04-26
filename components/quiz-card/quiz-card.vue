<template>
	<view class="quiz-card">
		<text className="question-number">
			Question 1 / 10
		</text>
		<text className="question-content">
			{{quizItem.question}}
		</text>
		<view class="button-wrapper" v-for="(item, index) in quizItem.answers" :key='index'>
			<button @click="handleClick(index)" :class="{correct: alreadyClicked && isCorrect(index), wrong: isClicked(index) && !isCorrect(index)}" :disabled="alreadyClicked">
				<text>{{item}}</text>
			</button>
		</view>
	</view>
</template>

<script>
	export default {
		name: "quiz-card",
		props: {
			quizItem: Object,
			default: ()=>({})
		},
		data() {
			return {
				clickedIndex: -1
			};
		},
		methods:{
			handleClick(index){
				this.$emit('selectAnswer', index)
				this.clickedIndex = index
			},
			isCorrect(index){
				return index === this.quizItem.correctAnswer
			},
			isClicked(index){
				return index === this.clickedIndex
			}
		},
		computed:{
			alreadyClicked(){
				return this.clickedIndex !== -1
			}
		}
	}
</script>

<style lang="scss">
	.quiz-card {
		width: 250px;
		background-color: #ebfeff;
		border-radius: 10px;
		border: 2px solid #0085a3;
		padding: 20px;
		box-shadow: 0 5px 10px rgba(0, 0, 0, 0.25);
		text-align: center;

		.button-wrapper {

			button {
				width: 100%;
				height: 40px;
				margin: 5px 0;

				color: #fff;
				background: linear-gradient(90deg, #56ccff, #6eafb4);
				border: 3px solid #fff;
				box-shadow: 1px 2px 0 rgba(0, 0, 0, 0.1);
				text-shadow: 0 1px 0 rgba(0, 0, 0, 0.25);
				position: relative;
				
				&.correct{
					background: linear-gradient(90deg, #56ffa4, #59bc86);
					&::before{
						content: '\e645';
						font-family: cuIcon;
						position: absolute;
						right: 5px;
					}
				}
				&.wrong{
					background: linear-gradient(90deg, #ff5656, #c16868);
					&::before{
						content: '\e646';
						font-family: cuIcon;
						position: absolute;
						right: 5px;
					}
				}

				// .feedback {
				// 	position: absolute;
				// 	right: 10px;
				// 	color: #fff;
				// }
			}
		}
	}
</style>
