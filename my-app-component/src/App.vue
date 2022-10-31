<template>
	<div>
		<header>
			<h1>Employee management system</h1>
		</header>
		<form-component @save="insertEmployee" />
		<section class="employee-content" v-if="employees.length > 0">
			<h2>Employees details</h2>
			<ListData :employees="employees" />
		</section>
	</div>
</template>

<script>
import FormComponent from "./components/FormComponent.vue";
import ListData from "./components/ListData.vue";

export default {
	name: "App",
	components: {
		FormComponent,
		ListData,
	},
	data() {
		return {
			employees: [],
		};
	},
	methods: {
		insertEmployee(data) {
			this.employees.push(data);
		},
	},
};
</script>

<style>
* {
	box-sizing: border-box;
}
body {
	margin: 0;
}
header {
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
	margin: 3rem;
	border-radius: 10px;
	padding: 1rem;
	background-color: purple;
	color: white;
	text-align: center;
}
.employee-content {
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
	margin: 3rem;
	border-radius: 10px;
	padding: 1rem;
	text-align: center;
}
.employee-content h2 {
	font-size: 2rem;
	border-bottom: 4px solid #ccc;
	color: purple;
	margin: 0 0 1rem 0;
}
</style>
