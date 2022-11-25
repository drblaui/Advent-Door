<template>
	<v-container>
		<v-row justify="center" align-self="center">
			<v-col></v-col>
			<v-col class="justify-center text-center">
				<CalendarDoor class="justify-center" :day="22">
					<v-btn icon="mdi-download" color="primary" class="download-button" @click="downloadVid"></v-btn>
					<video controls>
						<source src="@/assets/cameo_video_lena.mp4" type="video/mp4" id="src"/>
					</video>
				</CalendarDoor>
			</v-col>
			<v-col></v-col>
		</v-row>
	</v-container>
	<a id="downloader" :href="link" download="melon-and-finn-cameo" />
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import CalendarDoor from '@/components/CalendarDoor.vue';
export default defineComponent({
	components: {
		CalendarDoor,
	},
	computed: {
		link(): string {
			let el = document.getElementById('src');
			if(el) {
				return (el as HTMLSourceElement).src;
			}
			return "";
		}
	},
	methods: {
		downloadVid: () => {
			document.getElementById("downloader")?.click();
		}
	}
});
</script>
<style scoped>
a {
	display: hidden;
}
.download-button {
	position: absolute;
	top: 5px;
	right: 5px;
}
video {
	max-width: 100%;
	max-height: 80%;
}
</style>