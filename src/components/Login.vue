<template>
	<h1>Login page</h1>
	<div class="login">
		<input type="email" v-model="email" placeholder="enter email">
		<input type="password" v-model="password" placeholder="enter password">
		<button @click="login">Sign up</button>
		<p>
			<router-link to="/sign-up">need an account?</router-link>
		</p>
	</div>
</template>

<script>
	export default {
		name: 'login-page'
	}
</script>