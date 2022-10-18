<template>
	<img alt="Vue logo" class="logo" src="../assets/logo.png">
	<h1>Sign up</h1>
	<div class="register">
		<input type="text" v-model="name" placeholder="enter name">
		<input type="email" v-model="email" placeholder="enter email">
		<input type="password" v-model="password" placeholder="enter password">
		<button @click="signUp">Sign up</button>
		<p>
			<router-link to="/login">already have an account?</router-link>
		</p>
	</div>
</template>

<script>
	import axios from 'axios'

	export default {
		name: 'SignUp',
		data() {
			return {
				name: '',
				email: '',
				password: ''
			}
		},
		methods: {
			async signUp() {
				let result = await axios.post("http://localhost:3000/users", {
					name: this.name,
					email: this.email,
					password: this.password
				})

				console.warn(result)

				if (result.status == 201) {
					localStorage.setItem("user-info", JSON.stringify(result.data))
					this.$router.push({name: 'Home'})
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