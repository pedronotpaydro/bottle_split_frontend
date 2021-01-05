<template>
  <div class="create">
    <!-- <h1>List of beers</h1> -->
    <h2>Create New Event</h2>
    <div>
      Bottle Name:
      <input type="text" v-model="newBeerName" />
      Brewery:
      <input type="text" v-model="newBeerBrewery" />
      Description:
      <input type="text" v-model="newBeerDescription" />
      Style:
      <input type="text" v-model="newBeerStyle" />
      Event Name:
      <input type="text" v-model="newEventName" />
      Event Location:
      <input type="text" v-model="newEventLocation" />
      Event Date:
      <Datepicker format="YYYY-MM-DD h:i:s" width="100%" v-model="newEventDate" />

      <button v-on:click="createBeer">Create Event</button>
    </div>

    <!-- <div v-for="beer in beers" :key="beer.id">
      <h4>{{ beer.name }}</h4>
      <p>{{ beer.id }}</p>
    </div> -->
  </div>
</template>

<script>
import axios from "axios";
import Datepicker from "vuejs-datetimepicker";

export default {
  data: function() {
    return {
      beers: [],
      newBeerName: "",
      newBeerDescription: "",
      newBeerBrewery: "",
      newBeerStyle: "",
      newEventName: "",
      newEventLocation: "",
      newEventDate: "",
      errors: [],
    };
  },
  components: {
    Datepicker,
  },
  // created: function() {
  //   this.indexBeers();
  // },
  mounted: function() {
    this.indexBeers();
  },
  methods: {
    indexBeers: function() {
      axios.get("/api/beers").then(response => {
        this.beers = response.data;
        console.log("All Beers", this.beers);
      });
    },
    createBeer: function() {
      var beerParams = {
        name: this.newBeerName,
        brewery: this.newBeerBrewery,
        description: this.newBeerDescription,
        style: this.newBeerStyle,
      };
      var eventParams = {
        name: this.newEventName,
        location: this.newEventLocation,
        date: this.newEventDate,
      };
      axios.post("/api/beers", beerParams).then(response => {
        console.log("Beer added", response.data);
        this.beers.push(response.data);
        axios.post("/api/events", eventParams).then(console.log("event added"));
        this.$parent.flashMessage = "Event Created Successfully!";
        this.$router.push("/");
      });
    },
  },
};
</script>
