<template>
  <div class="create">
    <!-- Section Specials -->
    <section id="specials">
      <div class="container">
        <div class="row">
          <div class="col-xl-12">
            <div class="specials_wrap">
              <div class="row">
                <div class="col-lg-6 col-md-12 no-padding align-self-center">
                  <div class="specials_content">
                    <h2>Specials</h2>
                    <hr class="dotted_divider_left_red" />
                    <p>
                      Chef Manue loves experimenting with flavours and ingredients but sometimes she loves to follow
                      strictly recipes from French pastry chefs.
                    </p>

                    <a href="specials.html" class="btn btn-link-bibbona">
                      More
                      <i class="fas fa-long-arrow-alt-right" aria-hidden="true"></i>
                    </a>
                  </div>
                </div>
                <div class="col-lg-6 col-md-12 no-padding">
                  <div class="specials_img"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- /.Section Specials -->
    <!-- <h2>Create New Event</h2>
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
    // eslint-disable-next-line vue/no-unused-components
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
