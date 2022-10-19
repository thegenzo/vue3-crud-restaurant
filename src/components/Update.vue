<template>
	<Header />
	<h1>Hello user, welcome on update restaurant page</h1>
	<form action="" class="add">
		<input type="text" name="name" id="name" placeholder="enter name" v-model="restaurant.name">
		<input type="text" name="address" id="address" placeholder="enter address" v-model="restaurant.address">
		<input type="text" name="contact" id="contact" placeholder="enter contact" v-model="restaurant.contact">
		<button type="button" @click="updateRestaurant()">update restaurant</button>
	</form>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'

export default {
	name: 'update-page',
	components: {
		Header
	},
	data() {
		return {
			restaurant: {
				name: '',
				address: '',
				contact: ''
			}
		}
	},
	async mounted() {
		let user = localStorage.getItem('user-info')
		if (!user) {
			this.$router.push({name: 'SignUp'})
		}

		const result = await axios.get('http://localhost:3000/restaurants/' + this.$route.params.id)
		this.restaurant.name = result.data.name
		this.restaurant.address = result.data.address
		this.restaurant.contact = result.data.contact
	},
	methods: {
		async updateRestaurant() {
			let result = await axios.put('http://localhost:3000/restaurants/' + this.$route.params.id, {
				name: this.restaurant.name,
				address: this.restaurant.address,
				contact: this.restaurant.contact
			})

			if (result.status == 200) {
				this.$router.push({name: 'Home'})
			}
		}
	}
}
</script>