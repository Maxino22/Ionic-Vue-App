<template>
	<ion-page>
		<ion-header>
			<ion-toolbar>
				<ion-title>Account</ion-title>
			</ion-toolbar>
		</ion-header>
		<ion-content :fullscreen="true">
			<ion-header collapse="condense">
				<ion-toolbar>
					<ion-title size="large">Account</ion-title>
				</ion-toolbar>
			</ion-header>
			<ion-content>
				<form @submit.prevent="updateProfile">
					<ion-item>
						<ion-label>
							<p>Email</p>
							<p>{{ session?.user?.email }}</p>
						</ion-label>
					</ion-item>

					<ion-item>
						<ion-label position="stacked">Name</ion-label>
						<ion-input
							type="text"
							name="username"
							v-model="profile.username"
						></ion-input>
					</ion-item>

					<ion-item>
						<ion-label position="stacked">Website</ion-label>
						<ion-input
							type="url"
							name="website"
							v-model="profile.website"
						></ion-input>
					</ion-item>
					<div class="ion-text-center">
						<ion-button fill="clear" type="submit">Update Profile</ion-button>
					</div>
				</form>

				<div class="ion-text-center">
					<ion-button fill="clear" @click="signOut">Log Out</ion-button>
				</div>
			</ion-content>
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
	IonItem,
	IonButton,
	IonLabel,
	IonInput,
} from '@ionic/vue'
import { User } from '@supabase/supabase-js'

import { supabase } from '../config/superbaseClient'
import { reactive, ref } from 'vue'

const session = ref(supabase.auth.getSession())
const profile = reactive({
	username: '',
	website: '',
	avatar_url: '',
})
</script>
