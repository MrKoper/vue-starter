<template>
  <div>
    <h1>Witaj w systemie do zapisów na zajęcia</h1>
    <!--<p>{{ email }}</p>-->
	<div v-if="isAuthenticated">
		<p>Zalogowany jako {{ email}}</p>
    	<button @click="logMeOut()">Wyloguj</button>
    </div>
    <div v-else>
    	<input type="text" v-model="email">
    	<button @click="logMeIn()">Zaloguj się</button>
	</div>
  </div>
</template>

<script>
export default {
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
		logMeIn() {
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
