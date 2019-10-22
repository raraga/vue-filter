<template>
  <div class="container">
    <div class="columns">
      <div class="column is-one-quarter">
        <h1 class="title">Filters</h1>
        <label class="checkbox">
          <input type="checkbox">
          Performance
        </label>
        <label class="checkbox">
          <input type="checkbox">
          Value
        </label>
        <label class="checkbox">
          <input type="checkbox">
          Basic
        </label>
      </div>
      <div class="column is-three-quarters">
        <h1 class="title">Products</h1>
          <ul>
            <li v-for="product in products" v-bind:key="product.id"> {{ product.name }} {{ product.class }} </li>
          </ul>
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
        products: [{
            id: 1,
            name: 'Product 1',
            class: 'Performance'
          },
          {
            id: 2,
            name: 'Product 2',
            class: 'Performance'
          },
          {
            id: 3,
            name: 'Product 3',
            class: 'Performance'
          },
          {
            id: 4,
            name: 'Product 4',
            class: 'Value'
          },
          {
            id: 8,
            name: 'Product 8',
            class: 'Value'
          },
          {
            id: 9,
            name: 'Product 9',
            class: 'Basic'
          },
          {
            id: 10,
            name: 'Product 10',
            class: 'Basic'
          },
          {
            id: 11,
            name: 'Product 11',
            class: 'Basic'
          }
        ]
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

</style>
