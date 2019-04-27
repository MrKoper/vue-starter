<template>
  <div>
    <h1>Witaj w systemie do zapisów na zajęcia</h1>
    <!--<p>{{ email }}</p>-->
	<div v-if="isAuthenticated">
		<p>Zalogowany jako {{ email }}</p>
    	<button @click="logMeOut()">Wyloguj</button>
    </div>
    <!-- <div v-else>
    	<input type="text" v-model="email">
    	<button @click="logMeIn()">Zaloguj się</button>
	</div> -->
	<div v-else>
    	<form @submit.prevent="">
		<login-form @login="logMeIn($event)"
					header="Zaloguj się e-mailem"
					button-label="Zaloguj"></login-form>
		<login-form @login="logMeIn($event)"
					header="Zarejestruj się e-mailem"
					button-label="Zarejestruj"></login-form>
    	</form>
	</div>
  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import LoginPage from "./LoginPage";

export default {
	components: {LoginForm},
	data() {
		  return {
		    email: 'mwo@agh.pl',
		    isAuthenticated: false
		  };
	},
	methods: {
		  alertMyEmail() {
		    alert(this.email);
		  }
	},
	methods: {
		logMeIn(username) {
			this.email = username;
			this.isAuthenticated = true;
		},
		logMeOut() {
			this.isAuthenticated = false;
			this.email = '';
		}
	}
}
</script>

<style>

</style>
