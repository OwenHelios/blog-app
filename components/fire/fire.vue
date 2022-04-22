<template>
	<view>
		{{player.position}}
		<button @click="handleClick">33333</button>
	</view>
</template>

<script>
	export default {
		name:"test",
		props: {
			player: Object,
		},
		data() {
			return {
				
			};
		},
		methods:{
			handleClick(){
				console.log(this.player.position);
			}
		}
	}
</script>

<style lang="scss">

</style>