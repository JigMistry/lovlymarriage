<template>
	<div class="heart" ref="heartSec"></div>
</template>
<script>
	export default {
		data() {
			return {
				heartInterval: null,
			}
		},
		methods: {

		},
		mounted() {
			this.heartInterval = setInterval(() => {
				document.querySelector('.heart').classList.remove('animationClass')
				setTimeout(() => {
					document.querySelector('.heart').classList.add('animationClass')
				}, 1500)				
			}, 3500);
		},
		beforeDestroy() {
			clearInterval(this.heartInterval);
		}
	}
</script>
<style scoped>
	.heart {
	  width: 100px;
	  height: 100px;
	  position: absolute;
	  left: 50%;
	  top: 25px;
	  transform: translate(-50%, -50%);
	  background: url(https://cssanimation.rocks/images/posts/steps/heart.png) no-repeat;
	  background-position: 0 0;
	  cursor: pointer;
	  animation: fave-heart 1s steps(28);
	}
	.heart:hover {
	  
	}
	.animationClass {
		background-position: -2800px 0;
	  	transition: background 1s steps(28);
	}
	@keyframes fave-heart {
	  0% {
	    background-position: 0 0;
	  }
	  100% {
	    background-position: -2800px 0;
	  }
	}

</style>