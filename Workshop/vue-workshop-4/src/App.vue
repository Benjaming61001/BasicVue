<template>
	<div id="app">
		<div class="container">
			<h2 align="center">Workshop #4 - Product Cart System</h2>
			<hr />
			<div class="row">
				<div class="col-md-2" v-for="item in products" :key="item.id">
					<div class="card h-100">
						<img :src="item.image" class="card-img-top" />
						<div class="card-body">
							<h4 class="card-title">{{ item.name }}</h4>
							<p class="card-text">price {{ item.price }} baht</p>
						</div>
						<div class="card-footer">
							<button
								class="btn btn-primary"
								@click="addToCart(item)"
							>
								Add to cart
							</button>
						</div>
					</div>
				</div>

				<div class="col-md-8" v-if="inCart != 0">
					<h4>
						<i class="fa fa-shopping-cart"></i>
						Cart
					</h4>
					<hr />
					<table class="table">
						<thead class="thead-dark">
							<tr>
								<th scope="col">Image</th>
								<th scope="col">Name</th>
								<th scope="col">Price</th>
								<th scope="col">Quantity</th>
								<th scope="col">Total</th>
								<th scope="col">Remove</th>
							</tr>
						</thead>
						<tbody>
							<tr v-for="(product, index) in inCart" :key="index">
								<td>
									<img
										:src="product.image"
										alt=""
										class="img-fluid"
									/>
								</td>
								<td>{{ product.name }}</td>
								<td>{{ product.price }}</td>
								<td>
									<i
										class="fa fa-minus qty-minus"
										@click="minusQty(product)"
									></i>
									{{ product.qty }}
									<i
										class="fa fa-plus qty-plus"
										@click="plusQty(product)"
									></i>
								</td>
								<td>{{ product.total }}</td>
								<td>
									<button
										@click="removeProduct(product)"
										class="btn-danger"
									>
										<i class="fa fa-trash"></i>
									</button>
								</td>
							</tr>
						</tbody>
					</table>
					<h4 align="right">Total: {{ total() }} Baht</h4>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "App",
	data() {
		return {
			inCart: [],
			coffee: 0,
			tea: 0,
			caramel: 0,
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
				// {
				// 	id: 3,
				// 	name: "Caramel coffee cream",
				// 	price: 35,
				// 	image: "https://cdn.pixabay.com/photo/2016/11/29/09/47/caramel-1868802_960_720.jpg",
				// 	active: false,
				// },
			],
		};
	},
	methods: {
		addToCart: function (item) {
			if (item.id == 1) {
				this.coffee += 1;
				if (this.coffee <= 1) {
					this.pushData(item);
				} else {
					this.toCart(item);
				}
			} else if (item.id == 2) {
				this.tea += 1;
				if (this.tea <= 1) {
					this.pushData(item);
				} else {
					this.toCart(item);
				}
			} else {
				this.caramel += 1;
				if (this.caramel <= 1) {
					this.pushData(item);
				} else {
					this.toCart(item);
				}
			}
		},
		pushData(item) {
			this.inCart.push({
				id: item.id,
				name: item.name,
				price: item.price,
				image: item.image,
				qty: 1,
				total: item.price,
			});
		},
		findIndex: function (item) {
			for (var i = 0; i < this.inCart.length; i++) {
				if (this.inCart[i].id == item.id) {
					return i;
				}
			}
			return -1;
		},
		toCart: function (item) {
			var found = this.findIndex(item);
			this.inCart[found].qty += 1;
			this.inCart[found].total =
				this.inCart[found].qty * this.inCart[found].price;
		},
		minusQty: function (product) {
			product.qty -= 1;
			if (product.qty <= 1) {
				product.qty = 1;
			}
			product.total = product.price * product.qty;
		},
		plusQty: function (product) {
			product.qty += 1;

			product.total = product.price * product.qty;
		},
		removeProduct(product) {
			if (confirm("Are you sure?")) {
				var index = this.inCart.indexOf(product);
				this.inCart.splice(index, 1);
				if (product.id == 1) {
					this.coffee = 0;
				} else if (product.id == 2) {
					this.tea = 0;
				} else {
					this.caramel = 0;
				}
			}
		},
		total: function () {
			var sum = 0;
			this.inCart.forEach(function (item) {
				sum += item.total;
			});
			return sum;
		},
	},
};
</script>

<style scoped>
td img {
	width: 100px;
}

.qty-minus {
	cursor: pointer;
	margin-right: 20px;
}

.qty-plus {
	cursor: pointer;
	margin-left: 20px;
}
</style>
