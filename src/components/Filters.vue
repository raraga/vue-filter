<template>
	<div class="container">
		<div class="columns">
			<div class="column is-one-quarter">
				<h1 class="title">Filters</h1>

        <label>Performance</label>
				<input
          type="checkbox"
          value="Performance"
          v-model="content.categories"
          v-on:click="togglePerformance()"
        />

				<label>Value</label>
				<input
          type="checkbox"
          value="Value"
          v-model="content.categories"
          v-on:click="toggleValue()"
        />

				<label>Basic</label>
				<input
          type="checkbox"
          value="Basic"
          v-model="content.categories"
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
             <tr v-for="product in content.products" v-bind:key="product.id">
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
		data: function () {
			return {
				content: {
          title: "",
					categories: [],
					products: [
            { id: 1, name: 'Product 1', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 2, name: 'Product 2', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 3, name: 'Product 3', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 4, name: 'Product 4', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 5, name: 'Product 5', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 6, name: 'Product 6', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 7, name: 'Product 7', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 8, name: 'Product 8', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 9, name: 'Product 9', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 10, name: 'Product 10', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 11, name: 'Product 11', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 12, name: 'Product 12', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 13, name: 'Product 13', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 14, name: 'Product 14', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 15, name: 'Product 15', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 16, name: 'Product 16', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 17, name: 'Product 17', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 18, name: 'Product 18', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 19, name: 'Product 19', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 20, name: 'Product 20', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Performance' },
            { id: 21, name: 'Product 21', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 22, name: 'Product 22', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 23, name: 'Product 23', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 24, name: 'Product 24', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 25, name: 'Product 25', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 26, name: 'Product 26', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 27, name: 'Product 27', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 28, name: 'Product 28', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 29, name: 'Product 29', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 30, name: 'Product 30', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 31, name: 'Product 31', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 32, name: 'Product 32', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 33, name: 'Product 33', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 34, name: 'Product 34', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 35, name: 'Product 35', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 36, name: 'Product 36', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 37, name: 'Product 37', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 38, name: 'Product 38', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 39, name: 'Product 39', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 40, name: 'Product 40', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 41, name: 'Product 41', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 42, name: 'Product 42', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 43, name: 'Product 43', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 44, name: 'Product 44', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 45, name: 'Product 45', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 46, name: 'Product 46', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 47, name: 'Product 47', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 48, name: 'Product 48', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 49, name: 'Product 49', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 50, name: 'Product 50', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Value' },
            { id: 51, name: 'Product 51', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 52, name: 'Product 52', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 53, name: 'Product 53', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 54, name: 'Product 54', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 55, name: 'Product 55', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 56, name: 'Product 56', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 57, name: 'Product 57', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 58, name: 'Product 58', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 59, name: 'Product 59', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 60, name: 'Product 60', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 61, name: 'Product 61', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 62, name: 'Product 62', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 63, name: 'Product 63', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 64, name: 'Product 64', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
            { id: 65, name: 'Product 65', maxVoltage: 300, maxCurrent: 30, maxPower: 3000, numberOutputs: 1, class: 'Basic' },
					]
        },
        productCount: 0,
        allProductCount: 65,
        allProducts: true,
        showPerformance: false,
        showValue: false,
        showBasic: false
			}
    },
    mounted() { 
      let count = this.content.products.length
      this.productCount = count
    },
    computed: {
      getPerformance: function () {
        return this.content.products.filter(performanceProduct => performanceProduct.class == "Performance")
      },
      getValue: function () {
        return this.content.products.filter(valueProduct => valueProduct.class == "Value")
      },
      getBasic: function () {
        return this.content.products.filter(basicProduct => basicProduct.class == "Basic")
      }
    },
		methods: {
      togglePerformance: function() {
        this.showPerformance = !this.showPerformance

        // Update productCount with our new filtered items. 
        let count = this.getPerformance.length
        let allProducts = this.content.products.length
        this.productCount = count

        // Set it back to the original count when we uncheck the box.
        if (this.productCount == allProducts) {
          this.productCount == this.allProductCount
        }
      },
      toggleValue: function() {
        this.showValue= !this.showValue
        let count = this.getValue.length
        this.productCount= count
      },
      toggleBasic: function() {
        this.showBasic = !this.showBasic
        let count = this.getBasic.length
        this.productCount= count
      },
      updateCount: function() {
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
