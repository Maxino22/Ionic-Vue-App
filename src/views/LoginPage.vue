<template>
	<ion-page>
		<ion-header>
			<ion-toolbar>
				<ion-title>Login</ion-title>
			</ion-toolbar>
		</ion-header>
		<ion-content>
			<ion-grid>
				<ion-row class="ion-justify-content-center ion-padding">
					<ion-col size="6">
						<img class="" src="/key.png" alt="" />
					</ion-col>
				</ion-row>
				<ion-row class="ion-justify-content-center">
					<ion-col size="9">
						<ion-list inset="true">
							<form @submit.prevent="handleLogin">
								<ion-item>
									<ion-label position="stacked">Email</ion-label>
									<ion-input
										v-model="email"
										name="email"
										type="email"
									></ion-input>
								</ion-item>
								<div class="ion-text-center">
									<ion-button type="submit" fill="clear">Login</ion-button>
								</div>
							</form>
						</ion-list>
					</ion-col>
				</ion-row>
			</ion-grid>
		</ion-content>
	</ion-page>
</template>

<script setup lang="ts">
import { supabase } from '../config/superbaseClient'
import {
	IonItem,
	IonLabel,
	IonInput,
	IonButton,
	IonPage,
	IonHeader,
	IonToolbar,
	IonTitle,
	IonContent,
	IonGrid,
	IonRow,
	IonCol,
	loadingController,
	toastController,
} from '@ionic/vue'
import { ref } from 'vue'

const email = ref('')
const handleLogin = async () => {
	const loader = await loadingController.create({})
	const toast = await toastController.create({ duration: 5000 })

	try {
		await loader.present()
		const { error } = await supabase.auth.signInWithOtp({
			email: email.value,
			options: {
				emailRedirectTo: 'http:localhost:8100/account',
			},
		})
		if (error) throw error
		toast.message = 'check your email for the login link'
		await toast.present()
	} catch (error: any) {
		toast.message = error.error_description || error.message
		await toast.present()
	} finally {
		await loader.dismiss()
	}
}
</script>

<style scoped>
img {
	width: 150px;
	height: 150px;
	object-fit: cover;
}
</style>
