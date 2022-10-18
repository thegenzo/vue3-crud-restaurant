<template>
	<Header />
	<h1>Hello {{ name }}, welcome on home page</h1>
	<table border="1px">
		<tr>
			<td>ID</td>
			<td>Name</td>
			<td>Contact</td>
			<td>Address</td>
		</tr>
		<tr v-for="item in restaurant" :key="item.id">
			<td>{{ item.id }}</td>
			<td>{{ item.name }}</td>
			<td>{{ item.contact }}</td>
			<td>{{ item.address }}</td>
		</tr>
	</table>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'

export default {
	name: 'home-page',
	components: {
		Header
	},
	data() {
		return {
			name: '',
			restaurant: []
		}
	},
	async mounted() {
		let user =  localStorage.getItem('user-info')
		this.name = await JSON.parse(user).name
		if (!user) {
			this.$router.push({name: 'SignUp'})
		}

		let result = await axios.get('http://localhost:3000/restaurants')
		this.restaurant = result.data

	},
}
</script> 

<style>
td {
	width: 160px;
	height: 40px;
}
</style>