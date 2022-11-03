<template>
	<div id="app">
		<div class="container">
			<h2 align="center">Workshop #3 - Product Price Calculator</h2>
			<hr />
			<div class="row">
				<div class="col-md-3" v-for="item in products" :key="item.id">
					<div class="card h-100">
						<img :src="item.image" class="card-img-top" />
						<div class="card-body">
							<h4 class="card-title">{{ item.name }}</h4>
							<p class="card-text">price {{ item.price }} baht</p>
						</div>
						<div class="card-footer">
							<input
								type="checkbox"
								class="form-control"
								@change="selected(item)"
							/>
						</div>
					</div>
				</div>
				<h4>Total: {{ total() }} Baht</h4>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "App",
	data() {
		return {
			products: [
				{
					id: 1,
					name: "Iced coffee",
					price: 30,
					image: "https://cdn.pixabay.com/photo/2019/01/02/04/23/food-3908006_960_720.jpg",
					active: false,
				},

				{
					id: 2,
					name: "Iced tea",
					price: 35,
					image: "https://cdn.pixabay.com/photo/2014/12/11/02/56/lemon-tea-563799_960_720.jpg",
					active: false,
				},
				{
					id: 3,
					name: "Caramel coffee cream",
					price: 35,
					image: "https://cdn.pixabay.com/photo/2016/11/29/09/47/caramel-1868802_960_720.jpg",
					active: false,
				},
			],
		};
	},
	methods: {
		selected: function (item) {
			item.active = !item.active;
		},
		total: function () {
			var sum = 0;
			this.products.forEach(function (item) {
				if (item.active) {
					sum += item.price;
				}
			});
			return sum;
		},
	},
};
</script>

<style></style>
