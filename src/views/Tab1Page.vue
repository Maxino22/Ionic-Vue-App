<template>
	<ion-page>
		<ion-header>
			<ion-toolbar>
				<ion-title>Home</ion-title>
			</ion-toolbar>
		</ion-header>
		<ion-content :fullscreen="true">
			<ion-header collapse="condense">
				<ion-toolbar>
					<ion-title size="large">Home</ion-title>
				</ion-toolbar>
			</ion-header>
			<div class="container">
				<ion-card>
					<img :src="cardDetails.image" alt="" />
					<ion-card-header>
						<ion-card-title>{{ cardDetails.title }}</ion-card-title>
						<ion-card-subtitle>{{ cardDetails.subtitle }}</ion-card-subtitle>
					</ion-card-header>

					<ion-card-content>
						{{ cardDetails.description }}
					</ion-card-content>
				</ion-card>
			</div>
		</ion-content>
	</ion-page>
</template>

<script setup lang="ts">
import {
	IonPage,
	IonHeader,
	IonToolbar,
	IonTitle,
	IonContent,
	IonCard,
	IonCardContent,
	IonCardHeader,
	IonCardSubtitle,
	IonCardTitle,
} from '@ionic/vue'
import { reactive } from 'vue'
const cardDetails = reactive({
	title: 'The Art of Love',
	subtitle: 'Listen to your heart',
	description: 'Here are tips to get you at a better place',
	image: '/sex.jpg',
})
</script>

<style scoped>
.container {
	margin: auto;
}
</style>
