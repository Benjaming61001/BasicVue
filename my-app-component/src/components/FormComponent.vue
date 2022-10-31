<template>
	<form @submit.prevent="submitForm">
		<div class="form-control">
			<label for="emp-name">Employee's name</label>
			<input
				type="text"
				v-model.trim="employee.name"
				placeholder="firstname lastname"
			/>
		</div>
		<div class="form-control">
			<label for="salary">Employee's salary</label>
			<input type="number" v-model="employee.salary" />
		</div>
		<div class="form-control">
			<label for="department">Employee's department</label>
			<select v-model="employee.department">
				<option value="Marketing">Marketing</option>
				<option value="Accountant">Accountant</option>
				<option value="Sales">Sales</option>
			</select>
		</div>
		<div class="form-control">
			<h2>Gender</h2>
			<div>
				<input type="radio" value="Male" v-model="employee.gender" />
				<label for="gender-name">Male</label>
			</div>
			<div>
				<input type="radio" value="Female" v-model="employee.gender" />
				<label for="gender-name">Female</label>
			</div>
		</div>
		<div class="form-control">
			<h2>Language skills</h2>
			<div>
				<input type="checkbox" value="Thai" v-model="employee.skill" />
				<label for="skill">Thai</label>
			</div>
			<div>
				<input
					type="checkbox"
					value="English"
					v-model="employee.skill"
				/>
				<label for="skill">English</label>
			</div>
			<div>
				<input
					type="checkbox"
					value="Japanese"
					v-model="employee.skill"
				/>
				<label for="skill">Japanese</label>
			</div>
			<div>
				<input
					type="checkbox"
					value="Chinese"
					v-model="employee.skill"
				/>
				<label for="skill">Chinese</label>
			</div>
		</div>
		<div>
			<button>Save</button>
		</div>
	</form>
</template>

<script>
export default {
	name: "FormComponent",
	data() {
		return {
			employee: {
				name: "",
				salary: 15000,
				department: "Marketing",
				gender: "",
				skill: [],
			},
		};
	},
	methods: {
		submitForm() {
			if (!this.employee.name || !this.employee.gender) {
				return;
			}
			const newEmployee = {
				name: this.employee.name,
				salary: this.employee.salary,
				department: this.employee.department,
				gender: this.employee.gender,
				skill: this.employee.skill,
			};
			this.$emit("save", newEmployee);
			this.resetForm();
		},
		resetForm() {
			this.employee.name = "";
			this.employee.salary = 0;
			this.employee.department = "Marketing";
			this.employee.gender = "";
			this.employee.skill = [];
		},
	},
};
</script>

<style scoped>
form {
	margin: 2rem auto;
	max-width: 40rem;
	border-radius: 12px;
	box-shadow: 0 2px 10px rgba(0, 0, 0, 0.25);
	padding: 2rem;
	background: #fff;
}

.form-control {
	margin: 0.5rem 0;
}
label {
	font-weight: bold;
}
input,
select {
	display: block;
	width: 100%;
	font: inherit;
	margin-top: 0.5rem;
}
button {
	font: inherit;
	background: orangered;
	color: white;
	cursor: pointer;
	padding: 0.5rem 1rem;
	border-radius: 15px;
}
input[type="radio"],
input[type="checkbox"] {
	display: inline-block;
	width: auto;
	margin-right: 1rem;
}
input[type="radio"] + label,
input[type="checkbox"] + label {
	font-weight: normal;
}
h2 {
	font-size: 1rem;
	margin: 0.5rem 0;
}
</style>
