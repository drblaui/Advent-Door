<template>
	<article class="box">
		<div class="box-pane" @click="addClass">
			<img src="@/assets/border-door.png" id="kranz" />
			<h2 class="box-date">
				{{ day }}
			</h2>
		</div>
		<div class="box-frame">
			<slot />
		</div>
	</article>
</template>
<script lang="ts">
import { defineComponent } from 'vue';

	export default defineComponent({
		name: "CalendarDoor",
		props: {
			day: {
				type: Number,
				required: true
			}
		},
		methods: {
			addClass: (e: Event) => {
				if(e.target) {
					document.getElementsByClassName("box-pane")[0].classList.toggle("clicked");
				}
			}
		}
	})
</script>
<style scoped>
	#kranz {
		z-index: 40;
		margin-top: 15px;
		width: 12rem;
		height: 12rem;
	}

	.box {
		width: 50vw;
		height: 90vh;
		z-index: 1;
		perspective: 53.125rem;
	}

	@media only screen and (max-width: 600px) {
		.box {
			width: 90vw;
			height: 80vh;
			z-index: 1;
			perspective: 53.125rem;
		}
	}

	.box-pane {
		display: flex;
		width: 100%;
		height: 100%;
		justify-content: center;
		align-items: center;
		background: red /*linear-gradient(135deg, #41b883 50%, #34495e 50%)*/;
		cursor: pointer;
		transition: all 1s ease-out;
		transform-style: preserve-3d;
		transform-origin: 0;
		border-radius: 4%;
		background-image: url("@/assets/christmas-lights.png");
		background-size: 100%;
		background-position-y: -50px;
	}

	.box-date {
		position: absolute;
		display: flex;
		border-radius: 50%;
		width: 7.25rem;
		height: 7.25rem;
		justify-content: center;
		align-items: center;
		background: #ffd700;
		font-size: 3.5rem;
		line-height: 7.25;
		color: white;
	}

	.box-frame {
		display: flex;
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		justify-content: center;
		align-items: center;
		z-index: -1;
		background-color: #4158D0;
		background-image: linear-gradient(43deg, #4158D0 0%, #C850C0 46%, #FFCC70 100%);
		border-radius: 4%;
	}

	.box-pane.clicked {
		transform: rotateY(-97deg);
		-webkit-transform: rotateY(-97deg);
    -moz-transform: rotateY(-97deg);
    -o-transform: rotateY(-97deg);
    -ms-transform: rotateY(-97deg);
	}
</style>