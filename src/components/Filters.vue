<template>
	<div class="container">
		<div class="columns">
			<div class="column is-one-quarter">
				<h1 class="title">Filters</h1>
        <label>Performance</label>
				<input type="checkbox" value="Performance" v-model="categories"
          v-on:click="togglePerformance()" />
				<label>Value</label>
				<input type="checkbox" value="Value" v-model="categories"
          v-on:click="toggleValue()"
        />
				<label>Basic</label>
				<input type="checkbox" value="Basic" v-model="categories"
          v-on:click="toggleBasic()"
        />
			</div>
			<div class="column is-three-quarters">
				<h1 class="title">Number of Products: {{ productCount }}</h1>
          <!-- Performance Products -->
          <div class="products" v-if="showPerformance == true">
            <table class="table is-striped">
            <thead>
              <td>Product</td>
              <td>Max Voltage (V)</td>
              <td>Max Current (A)</td>
              <td>Max Power (W)</td>
              <td>Number of Outputs</td>
              <td>Class</td>
            </thead>
             <tr v-for="product in getPerformance" v-bind:key="product.id">
                <td>{{ product.name }}</td>
                <td>{{ product.maxVoltage }}</td>
                <td>{{ product.maxCurrent }}</td>
                <td>{{ product.maxPower }}</td>
                <td>{{ product.numberOutputs }}</td>
                <td>{{ product.class }}</td>
            </tr>
          </table>
          </div>
         <!-- Value Products  -->
          <div class="products" v-if="showValue == true">
             <table class="table is-striped">
            <thead>
              <td>Product</td>
              <td>Max Voltage (V)</td>
              <td>Max Current (A)</td>
              <td>Max Power (W)</td>
              <td>Number of Outputs</td>
              <td>Class</td>
            </thead>
             <tr v-for="product in getValue" v-bind:key="product.id">
                <td>{{ product.name }}</td>
                <td>{{ product.maxVoltage }}</td>
                <td>{{ product.maxCurrent }}</td>
                <td>{{ product.maxPower }}</td>
                <td>{{ product.numberOutputs }}</td>
                <td>{{ product.class }}</td>
            </tr>
             </table>
          </div>
        <!-- Basic Products  -->
          <div class="products" v-if="showBasic == true">
            <table class="table is-striped">
            <thead>
              <td>Product</td>
              <td>Max Voltage (V)</td>
              <td>Max Current (A)</td>
              <td>Max Power (W)</td>
              <td>Number of Outputs</td>
              <td>Class</td>
            </thead>
             <tr v-for="product in getBasic" v-bind:key="product.id">
                <td>{{ product.name }}</td>
                <td>{{ product.maxVoltage }}</td>
                <td>{{ product.maxCurrent }}</td>
                <td>{{ product.maxPower }}</td>
                <td>{{ product.numberOutputs }}</td>
                <td>{{ product.class }}</td>
            </tr>
          </table>
          </div>
       <!-- Default Product view  -->
        <div class="products" v-if="showPerformance == false && showValue == false && showBasic == false">
            <table class="table is-striped">
              <thead>
                <td>Product</td>
                <td>Max Voltage (V)</td>
                <td>Max Current (A)</td>
                <td>Max Power (W)</td>
                <td>Number of Outputs</td>
                <td>Class</td>
              </thead>
              <tr v-for="product in products" v-bind:key="product.id">
                  <td>{{ product.name }}</td>
                  <td>{{ product.maxVoltage }}</td>
                  <td>{{ product.maxCurrent }}</td>
                  <td>{{ product.maxPower }}</td>
                  <td>{{ product.numberOutputs }}</td>
                  <td>{{ product.class }}</td>
              </tr>
          </table>
        </div>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'Filters',
		props: {
			msg: String
		},
		data() {
			return {
        categories: [],
        users: [],
				products: [],
        productCount: 0,
        allProductCount: 65,
        allProducts: true,
        showPerformance: false,
        showValue: false,
        showBasic: false,
        errors: []
			}
    },
    created () {
      this.fetch_products()
    },
    mounted() {
      let count = this.products.length
      this.productCount = count
    },
    computed: {
      getPerformance() {
        return this.products
          .filter(performanceProduct => performanceProduct.class == "Performance")
      },
      getValue() {
        return this.products
          .filter(valueProduct => valueProduct.class == "Value")
      },
      getBasic() {
        return this.products
          .filter(basicProduct => basicProduct.class == "Basic")
      }
    },
		methods: {
      fetch_products() {
        const baseURI = "http://localhost:3000/products"
        this.$http.get(baseURI)
          .then(response => (
            this.products= response.data
          ))
          .catch (e => {
            this.errors.push(e)
          })
      },
      togglePerformance() {
        this.showPerformance = !this.showPerformance
        // Update productCount with our new filtered items.
        let count = this.getPerformance.length
        let allProducts = this.products.length
        this.productCount = count

        // Set it back to the original count when we uncheck the box.
        if (this.productCount == allProducts) {
          this.productCount == this.allProductCount
        }
      },
      toggleValue() {
        this.showValue= !this.showValue
        let count = this.getValue.length
        this.productCount = count
      },
      toggleBasic() {
        this.showBasic = !this.showBasic
        let count = this.getBasic.length
        this.productCount = count
      },
      updateCount() {
        // Updating the productCount variable.
        let count = this.getPerformance.length
        this.productCount = count
      }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.is-one-quarter {
		background: #fafafa;
	}
	.is-three-quarters {
		background: #ebebeb;
	}
	.column li {
		text-align: left;
	}
  label {
    margin-right: 5px;
  }
</style>
