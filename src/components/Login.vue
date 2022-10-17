<template>
	<h1>Login page</h1>
	<div class="login">
		<input type="email" v-model="email" placeholder="enter email">
		<input type="password" v-model="password" placeholder="enter password">
		<button @click="login">Login</button>
		<p>
			<router-link to="/sign-up">need an account?</router-link>
		</p>
		<p style="color: red">{{ errorMessage }}</p>
	</div>
</template>

<script>
	import axios from 'axios'
	export default {
		name: 'login-page',
		data() {
			return {
				email: '',
				password: '',
				errorMessage: ''
			}
		},
		methods: {
			async login() {
				let result = await axios.get(
					`http://localhost:3000/users?email=${this.email}&password=${this.password}`
				)
				console.log(result)

				if (result.status == 200 && result.data.length > 0) {
					localStorage.setItem("user-info", JSON.stringify(result.data[0]))
					this.$router.push({name: 'Home'})
				} else {
					this.errorMessage = 'email or password is incorrect'
					this.email = ''
					this.password = ''
				}
			}
		},
		mounted() {
			let user = localStorage.getItem('user-info')
			if (user) {
				this.$router.push({name: 'Home'})
			}
		}
	}
</script>