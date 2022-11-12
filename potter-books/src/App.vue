<template>
  <section>
    <topBar></topBar>
    <div class="section book">
      <h1>Books</h1>
      <ul>
        <li v-for="(book, index) in books" :key=index>
          {{ book.title }}
          <span>
            Price : {{ price }} baht
            <button @click="addToCart(book)" class="toCart"><i class="fa fa-cart-shopping"></i></button>
          </span>
        </li>
      </ul>
    </div>
    <div class="section cart" v-show="inCart.length > 0">
      <h1>Cart</h1>
      <ul>
        <li v-for="(item, index) in inCart" :key=index>
          <span>{{ item.title }}</span>
          <span>
            Quantity : {{ item.qty }}
            <button @click="minusQty(item)" class="minus"><i class="fa fa-minus"></i></button>
            <button @click="plusQty(item)" class="add"><i class="fa fa-plus"></i></button>

            <button @click="removeProduct(item)" class="remove"><i class="fa fa-trash"></i></button>
          </span>
        </li>
      </ul>
      <div class="description">
        <button @click="clear()" class="clear">Clear</button>
        <h4>Full Price: {{ total() + discount }} Baht</h4>
        <h4>Discount: {{ discount }} Baht ( {{ discountPercent }} % )</h4>
        <h4>Total: {{ total() }} Baht</h4>
      </div>
    </div>
    <div class="section promotion" v-show="inCart.length == 0">
      <h1>Promotion!!!</h1>
      <div class="description">
        <div>Buy 2 different books, get 10% discount</div>
        <div>Buy 3 different books, get 20% discount</div>
        <div>Buy 4 different books, get 30% discount</div>
        <div>Buy 5 different books, get 40% discount</div>
        <div>Buy 6 different books, get 50% discount</div>
        <div>Buy 7 different books, get 60% discount</div>
      </div>
    </div>
  </section>
</template>

<script>
import topBar from "./components/TopBar.vue";

export default {
  name: 'App',
  components: {
    topBar
  },
  data() {
    return {
      price: 100,
      books: [{
        order: 1,
        title: "Harry Potter and the Sorcerer's Stone",
        qty: 0
      }, {
        order: 2,
        title: "Harry Potter and the Chamber of Secrets",
        qty: 0
      }, {
        order: 3,
        title: "Harry Potter and the Prisoner of Azkaban",
        qty: 0
      }, {
        order: 4,
        title: "Harry Potter and the Goblet of Fire",
        qty: 0
      }, {
        order: 5,
        title: "Harry Potter and the Order of the Phoenix",
        qty: 0
      }, {
        order: 6,
        title: "Harry Potter and the Half-Blood Prince",
        qty: 0
      }, {
        order: 7,
        title: "Harry Potter and the Deathly Hallows",
        qty: 0
      }],
      inCart: [],
      discount: 0,
      discountPercent: 0
    }
  },
  methods: {
    addToCart: function (item) {
      var found = this.findIndex(item)
      this.books[found].qty = this.books[found].qty + 1
      if (item.qty <= 1) {
        this.pushData(item);
      }
      else {
        this.toCart(item);
      }
    },

    pushData(item) {
      this.inCart.push({
        order: item.order,
        title: item.title,
        qty: item.qty,
        total: this.price,
      });
    },

    toCart: function (item) {
      var foundBooks = this.findIndex(item);
      var foundCart = this.findIncart(item);
      this.inCart[foundCart].qty = this.books[foundBooks].qty
      this.inCart[foundCart].total = this.inCart[foundCart].qty * this.price
    },

    findIndex: function (item) {
      for (let i in this.books) {
        if (this.books[i].order == item.order) {
          return i;
        }
      }
      return -1;
    },

    findIncart: function (item) {
      for (let i in this.inCart) {
        if (this.inCart[i].order == item.order) {
          return i;
        }
      }
      return -1;
    },

    total: function () {
      var sum = 0;
      var percentage = 0;
      this.inCart.forEach(function (item) {
        sum += item.total;
      });
      for (let i = 1; i < this.inCart.length; i++) {
        percentage = i * 10
        this.discountPercent = percentage
      }
      sum = sum - this.percentCalculation(sum, percentage)

      return sum;
    },

    percentCalculation: function (number, percentage) {
      var c = (parseFloat(number) * parseFloat(percentage)) / 100;
      this.discount = c
      return parseFloat(c);
    },

    removeProduct(item) {
      if (confirm("Remove from list?")) {
        var foundBooks = this.findIndex(item);
        var foundCart = this.findIncart(item);
        this.inCart.splice(foundCart, 1);
        this.books[foundBooks].qty = 0
      }
      else {
        item.qty += 1
        this.books[foundBooks].qty = item.qty
      }
    },

    minusQty: function (item) {
      var foundBooks = this.findIndex(item);
      item.qty -= 1;
      this.books[foundBooks].qty = item.qty
      if (item.qty < 1) {
        this.removeProduct(item)
      }
      item.total = item.qty * this.price
    },

    plusQty: function (item) {
      var foundBooks = this.findIndex(item);
      item.qty += 1;
      this.books[foundBooks].qty = item.qty
      item.total = item.qty * this.price
    },

    clear: function () {
      if (confirm("Remove all from list?")) {
        this.inCart = []
        for (let i in this.books) {
          this.books[i].qty = 0
        }
      }
      else {
        return
      }
    }
  }
}
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Kanit:wght@200;300;400;500;600;700&display=swap");

@font-face {
  font-family: "WizardWorldFont";
  src: local("WizardWorldFont"),
    url(./fonts/WizardWorldSimplified-Kxr7.ttf) format("truetype");
}

* {
  margin: 0;
  padding: 0;
  font-family: "Kanit", sans-serif;
  font-weight: 400;
  text-align: center;

}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
}


section {
  background-color: rgb(14, 26, 65);
  height: 100vh;
}


ul {
  li {
    padding: 6px;
    text-align: left;
    display: flex;
    justify-content: space-between;
    border: 1px solid white;

    &:nth-child(even) {
      background: #740001;
      color: white;
    }

    &:nth-child(odd) {
      background: #d3a625;
      color: black;
    }

    span {
      display: flex;
      gap: 10px;
    }
  }

  li:first-child {
    border-radius: 5px 5px 0 0;
  }

  li:last-child {
    border-radius: 0 0 5px 5px;
  }
}

.section {
  margin-top: 20px;
  padding: 0 24px;

  h1 {
    font-family: "WizardWorldFont";
    font-size: 32px;
    text-align: left;
    margin: 10px 0;
  }

  .description {
    margin-top: 10px;
    font-size: 1.2rem;

    div {
      text-align: left;
    }

    h4 {
      text-align: right;
    }
  }
}

.cart {
  .description {
    display: flex;
    flex-direction: column;
    justify-content: end;
  }
}

button {
  padding: 3px 12px;
  background: white;
  border: 1px solid white;
  border-radius: 3px;
  transition: all .2s;
  cursor: pointer;
}

.toCart {
  padding: 2px 20px;
}

.remove {
  padding: 2px 20px;
}

.clear {
  width: auto;
  padding: 2px 20px;
  transition: all .2s;
}

.toCart:hover,
.add:hover {
  background: green;
  color: white;
}

.minus:hover,
.remove:hover,
.clear:hover {
  background: red;
  color: white;
}
</style>
