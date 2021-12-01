<template>
  <div class="hello">
<div v-for="ship in ships" :key="ship.id" class="ships_div">
  <img v-if="ship.image" :src="ship.image" alt="">
  <img v-else src="../images/noimage.png" alt="">
  <div class="text">
    <h3>Name</h3>
    <p>{{ship.name}}</p>
    <h3>Type</h3>
    <p>{{ship.type}}</p>
    <h3>Year built</h3>
    <p v-if="ship.year_built">{{ship.year_built}}</p>
    <p v-else>/</p>
    <a :href="ship.url"><b-button variant="light">More info</b-button></a>
  </div>
  <div class="table_div">
    <h2>Missions</h2>
    <b-table striped borderless table-variant="light" head-row-variant="dark" class="table" sticky-header :items="ship.missions" head-variant="light"></b-table>
  </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      ships: [],
    };
  },
  methods: {
    async getData() {
      try {
        const response = await this.$http.get(
          "http://api.spacex.land/rest/ships"
        );
        this.ships = response.data;
      } catch(error) {
        console.log(error);
      }
    },
  },
  created() {
    this.getData();
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

img {
 height: 170px;
 width: 170px;
 margin: 5px;
 border: 3px solid white;
}

h2 {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: white;
  text-align: center;
}

h1 {
  text-align: center;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  color: #0d6efd;
  padding-bottom: 50px;
}

p {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: 20px;
  color: white;
  text-align: left;
  padding-left: 10px;
  font-size: 16px;
}

h3 {
  text-align: left;
  font-size: 20px;
  color: #42b983;
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
  text-decoration: none;
}

button {
  background-color: #42b983;
  color: white;
  border: #42b983;
}

button:hover {
  background-color: white;
  color: #42b983;
}

.table_div {
  flex-basis: 100%;
  margin: 5px;
}

.ships_div {
  width: auto;
  height: auto;
  border: 2px solid #42b983;
  border-radius: 10px;
  box-shadow: grey;
  background-color: black;
  margin: 20px;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

.hello {
  display: grid;
  grid-template-columns: auto auto auto;
}

.text {
  margin: 10px;
  display: grid;
  grid-template-columns: auto auto;
  height: fit-content;
}

/*.noimage {
  width: 200px;
  height: 200px;
}*/

</style>
