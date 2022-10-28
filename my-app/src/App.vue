<template>
	<section>
		<img
			:src="image"
			alt="image"
			:width="size"
			:height="size"
			ref="imageEl"
		/><br />

		<h1>Name: {{ getFullName }}</h1>
		<h1>Age: {{ age }} years old</h1>
		<h1>Salary: {{ salary }} Baht</h1>
		<h1>Income per year: {{ getIncome }} Baht</h1>
		<h1>Job position: {{ getDepartment }}</h1>

		<button @:click="addSalary(5000)">Increase salary</button>
		<button @:click="toggleVisible">
			{{ isVisible ? "Hide " : "Show " }} Details
		</button>

		<article v-show="isVisible">
			<p>Address: <span v-html="address"></span></p>
			<p>Social: <a :href="social" target="_blank">Facebook</a></p>

			<p v-if="hobby.length === 0">No hobbies</p>
			<div v-else>
				<p>Hobby(s):</p>
				<ul>
					<li v-for="(item, index) in hobby" :key="index">
						{{ item }}
					</li>
				</ul>
			</div>

			<p>general infomation:</p>
			<ul>
				<li v-for="(item, key) in general" :key="key">
					{{ key }} - {{ item }}
				</li>
			</ul>
		</article>
	</section>
</template>

<script>
export default {
	name: "App",
	data() {
		return {
			firstName: "Pavin",
			lastName: "Butprom",
			age: 23,
			address: "<strong>Bangkok</strong>",
			image: "https://cdn-icons-png.flaticon.com/512/3135/3135715.png",
			size: 250,
			social: "https://www.facebook.com",
			hobby: ["Video game", "photograph", "cafe hopping", "cooking"],
			general: {
				gender: "male",
				weight: 51.5,
				height: 177,
				status: false,
			},
			isVisible: false,
			salary: 20000,
		};
	},

	methods: {
		toggleVisible() {
			this.isVisible = !this.isVisible;
		},
		addSalary(value) {
			this.salary += value;
		},
	},
	computed: {
		getFullName() {
			return this.firstName + " " + this.lastName;
		},
		getIncome() {
			return this.salary * 12;
		},
		getDepartment() {
			return this.salary >= 35000 ? "Project Manager" : "Programmer";
		},
	},
	watch: {
		salary(value) {
			if (value > 50000) {
				alert("salary shouldn't be above 50,000 baht");
				setTimeout(() => {
					this.salary = 50000;
				}, 500);
			}
		},
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;

	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

ul {
	padding: 0;
}
</style>
