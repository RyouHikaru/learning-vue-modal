<template>
	<h1>{{ title }}</h1>
	<p>Welcome!</p>
	<teleport to="#modals" v-if="showModal">
		<Modal theme="sale" @close="toggleModal">
			<template v-slot:links>
				<a href="#">Sign up now</a>
				<a href="#">More info</a>
			</template>
			<h1>Ninja Giveaway</h1>
			<p>Grab your ninja swag for half price!</p>
		</Modal>
	</teleport>

	<teleport to="#modals" v-if="showModalTwo">
		<Modal @close="toggleModalTwo">
			<h1>Free Tapioca Pearls</h1>
			<p>Buy your Milktea now!</p>
		</Modal>
	</teleport>
	<button @click.alt="toggleModal">Modal 1 (Alt)</button>
	<button @click="toggleModalTwo">Modal 2</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
	name: "App",
	components: { Modal },
	data() {
		return {
			title: "Learning Vue (Modal)",
			showModal: false,
			showModalTwo: false,
		};
	},
	methods: {
		handleClick() {
			this.$refs.name.classList.add("active");
			this.$refs.name.focus();
		},
		toggleModal() {
			this.showModal = !this.showModal;
		},
		toggleModalTwo() {
			this.showModalTwo = !this.showModalTwo;
		},
	},
};
</script>

<style>
#app,
#modals {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

h1 {
	border-bottom: 1px solid #ddd;
	display: inline-block;
	padding-bottom: 10px;
}
</style>
