<template>
	<Header />
	<h1>Hello user, welcome on add restaurant page</h1>
	<form action="" class="add">
		<input type="text" name="name" id="name" placeholder="enter name" v-model="restaurant.name">
		<input type="text" name="address" id="address" placeholder="enter address" v-model="restaurant.address">
		<input type="text" name="contact" id="contact" placeholder="enter contact" v-model="restaurant.contact">
		<button type="button" @click="addRestaurant">add new restaurant</button>
	</form>
</template>

<script>
import Header from './Header.vue'
export default {
	name: 'add-page',
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
	methods: {
		addRestaurant() {
			console.warn(this.restaurant)
		}
	},
	mounted() {
		let user = localStorage.getItem('user-info')
		if (!user) {
			this.$router.push({name: 'SignUp'})
		}
	},
}
</script>