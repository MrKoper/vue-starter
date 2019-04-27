<template>
  <div>
    <h1>Witaj w systemie do zapisów na zajęcia</h1>
    <!--<p>{{ email }}</p>-->
	<div v-if="isAuthenticated">
		<login-page :username="email"
					 @logout="logMeOut()">
		</login-page>			 
    </div>
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
	components: {LoginForm, LoginPage},
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
		logMeOut(username) {
			this.email = '';
			this.isAuthenticated = false;
		}
	}
}
</script>

<style>

</style>
