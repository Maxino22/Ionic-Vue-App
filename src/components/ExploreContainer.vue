<template>
	<div class="container">
		<ion-datetime-button
			type="danger"
			datetime="datetime"
		></ion-datetime-button>
		<ion-modal :keep-contents-mounted="true">
			<ion-datetime id="datetime"></ion-datetime>
		</ion-modal>
	</div>
</template>

<script setup lang="ts">
import { IonDatetime, IonDatetimeButton, IonModal } from '@ionic/vue'
defineProps({
	name: String,
})
</script>

<style scoped>
.container {
	margin-top: 10px;
}
</style>
