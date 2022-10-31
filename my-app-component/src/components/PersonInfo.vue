<template>
	<CardPrototype>
		<template v-slot:card-header>
			<h1>{{ name }}</h1>
		</template>

		<template v-slot:card-button>
			<button @click="showDescription(id)">
				{{ isVisible ? "Hide " : "Show " }}Details
			</button>
			&nbsp;
			<button @click="deleteEmployee(id)">Delete</button>
		</template>

		<template v-slot:card-content>
			<transition name="fade">
				<div v-show="isVisible">
					<p>
						Salary: {{ salary }} Baht | Department: {{ department }}
					</p>
				</div>
			</transition>
		</template>
	</CardPrototype>
</template>

<script>
import CardPrototype from "./CardPrototype.vue";
export default {
	name: "PersonInfo",
	components: {
		CardPrototype,
	},
	props: {
		id: {
			type: Number,
		},
		name: {
			type: String,
			required: true,
		},
		salary: {
			type: Number,
			default: 15000,
		},
		department: {
			type: String,
			required: true,
		},
		isVisible: {
			type: Boolean,
		},
	},
	methods: {
		showDescription(id) {
			this.$emit("show", id);
		},
		deleteEmployee(id) {
			this.$emit("delete", id);
		},
	},
};
</script>

<style scoped>
button {
	font: inherit;
	cursor: pointer;
	border: 1px solid #ff0077;
	background: #ff0077;
	color: white;
	padding: 0.05rem 1rem;
	box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}
.fade-enter-from {
	opacity: 0;
}
.fade-enter-active {
	transition: all 0.5s linear;
}
</style>
