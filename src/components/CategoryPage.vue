<template>
  <div class="hello">

    <div class="title">Kaffe & Espresso</div>

    <div class="bttn-div">
      <button class="bttn"> Filter </button>
      <dropdown class="drop" :options="arrayOfObjects" :selected="products" v-on:updateOption="methodToRunOnSelect">

      </dropdown>


    </div>

  </div>

</template>

<script>




import dropdown from 'vue-dropdowns';


export default {
  name: 'CategoryPage',
  props: {
    msg: String
  },
  components: {
    "dropdown": dropdown,

  },
  data() {
    return {
      products: [],
      object: {
        name: 'Object Name',
      },
      methods: {
        methodToRunOnSelect(payload) {
          this.object = payload;
        }
      },
      mounted() {
        try {
          fetch('https://www.roastmarket.de/api/catalog/vue_storefront_catalog/product/_search?')
            .then(response => response.json())
            .then(response => (this.products = response.hits.hits, console.log(response.hits.hits)))



        } catch (e) {
          console.error(e);

        }



      },

      computed: {
        sortedArray: function () {
          function compare(a, b) {
            if (a.name < b.name)
              return -1;
            if (a.name > b.name)
              return 1;
            return 0;
          }

          return this.arrays.sort(compare);
        }
      }
    }
  }




}

  // drop


  // Close the dropdown menu if the user clicks outside of it
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.hello {

  width: 100%;
  padding: 20px;


  background-color: rgb(241, 241, 241);



}

.title {
  margin: 0;
  margin-bottom: 10px;
  font-size: 28px;
  line-height: 28px;
  display: -webkit-box;
  -webkit-line-clamp: 1;
  overflow: hidden;
  display: flex;
  font-weight: 700;

}


.bttn {
  background: #fa3621;
  border-radius: 2px;
  color: white;
  width: 180px;
  height: 40px;
  margin: 0 auto;
  vertical-align: middle;


}

.bttn-div {
  position: relative;
  padding-top: 40px;
  justify-content: space-between;
}
</style>
