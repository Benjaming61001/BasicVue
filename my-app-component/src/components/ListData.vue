<template>
	<ul>
		<PersonInfo
			v-for="item in employees"
			:id="item.id"
			:key="item.id"
			:name="item.name"
			:salary="item.salary"
			:department="item.department"
			:isVisible="item.isVisible"
			@show="toggleVisible"
			@delete="removeEmployee"
		/>
	</ul>
</template>

<script>
import PersonInfo from "./PersonInfo.vue";

export default {
	name: "ListData",
	components: {
		PersonInfo,
	},
	data() {
		return {
			employees: [
				{
					id: 1,
					name: "Pavin Butprom",
					salary: 40000,
					department: "Programmer",
					isVisible: false,
				},
				{
					id: 2,
					name: "Jojo Dio",
					salary: 30000,
					department: "Margetting",
					isVisible: false,
				},
				{
					id: 3,
					name: "Jeans Jeans",
					salary: 15000,
					department: "Graphic",
					isVisible: false,
				},
				{
					id: 4,
					name: "Benjamin Vincent ",
					salary: 20000,
					department: "Sales",
					isVisible: false,
				},
			],
		};
	},
	methods: {
		toggleVisible(id) {
			this.employees = this.employees.map((item) => {
				if (item.id === id) {
					return { ...item, isVisible: !item.isVisible };
				}
				return item;
			});
		},
		removeEmployee(id) {
			this.employees = this.employees.filter((item) => {
				return item.id !== id;
			});
		},
	},
};
</script>

<style scoped>
ul {
	list-style: none;
	margin: 1rem 0;
	padding: 0;
}
</style>
