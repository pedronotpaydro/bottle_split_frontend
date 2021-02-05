<template>
  <div class="create">
    <header id="event_header">
      <div class="container">
        <div class="row">
          <div class="col-md-8 offset-md-2">
            <div class="align-self-center" id="create">
              <!-- <div class="logo-badge">
                <img
                  src="cafe-bibbona/imgs/logo-badge/cafe-bibbona-badge.svg"
                  width="300"
                  height="115"
                  class="img-fluid mx-auto d-block"
                  alt="Café Bibbona - Coffee & Bakes"
                />
              </div> -->
            </div>
          </div>
        </div>
      </div>
    </header>
    <!-- Contact us -->
    <section id="contact_us">
      <div class="container">
        <div class="row">
          <div
            class="col-xl-8 offset-xl-2 col-lg-10 offset-lg-1 col-md-10 offset-md-1 col-sm-12"
          >
            <div class="contact_info_card">
              <!-- Title -->
              <div class="contact_title">
                <h2>Create Event</h2>
                <hr class="dotted_divider_center_red" />
              </div>
              <!-- /.Title -->

              <!-- Form -->

              <div class="contact_form">
                <form class="needs-validation" novalidate>
                  <div class="form-row">
                    <div class="col-md-6 mb-3">
                      <label for="validationCustom03">Event name</label>
                      <input
                        v-model="newEventName"
                        type="Event name"
                        class="form-control"
                        id="validationCustom03"
                        placeholder="Event name"
                        required
                      />
                      <div class="invalid-feedback">
                        Please provide a valid Event name.
                      </div>
                    </div>
                    <div class="col-md-6 mb-3">
                      <label for="validationCustom04">Event Date</label>

                      <Datepicker
                        format="YYYY-MM-DD h:i:s"
                        width="100%"
                        v-model="newEventDate"
                      />
                      <div class="invalid-feedback">
                        Please provide a valid Event Date.
                      </div>
                    </div>
                    <div class="col-md-6 mb-3">
                      <label for="validationCustom04">Event Location</label>
                      <!-- <input
                        v-model="newEventLocation"
                        type="textarea"
                        class="form-control"
                        id="validationCustom04"
                        placeholder="Event Location"
                        required
                      /> -->
                      <textarea
                        placeholder="Event Location"
                        class="form-control"
                        v-model="newEventLocation"
                        id="exampleFormControlTextarea1"
                        rows="2"
                        required
                      ></textarea>
                      <div class="invalid-feedback">
                        Please provide a valid Event Location.
                      </div>
                    </div>
                    <div class="w-100">
                      <hr class="dotted_divider_center_red" />
                    </div>

                    <div class="col-md-6 mb-3">
                      <label for="validationCustom01">Bottle Name</label>
                      <input
                        v-model="newBeerName"
                        type="text"
                        class="form-control"
                        id="validationCustom01"
                        placeholder="Bottle Name"
                        required
                      />
                      <div class="invalid-feedback">
                        Please provide name of bottle.
                      </div>
                    </div>
                    <div class="col-md-6 mb-3">
                      <label for="validationCustom02">Brewery</label>
                      <input
                        type="text"
                        v-model="newBeerBrewery"
                        class="form-control"
                        id="validationCustom02"
                        placeholder="Brewery"
                        required
                      />
                      <div class="invalid-feedback">
                        Please provide Brewery.
                      </div>
                    </div>
                    <div class="col-md-6 mb-3">
                      <label for="validationCustom02">Style</label>
                      <input
                        type="text"
                        v-model="newBeerStyle"
                        class="form-control"
                        id="validationCustom02"
                        placeholder="Style"
                        required
                      />
                      <div class="invalid-feedback">
                        Please provide Style.
                      </div>
                    </div>

                    <div class="col-md-6 mb-3">
                      <label for="validationCustom02">Bottle Description</label>
                      <!-- <input
                        v-model="newBeerDescription"
                        type="text"
                        class="form-control"
                        id="validationCustom02"
                        placeholder="Description"
                        required
                      /> -->
                      <textarea
                        placeholder="Description"
                        class="form-control"
                        v-model="newBeerDescription"
                        id="exampleFormControlTextarea1"
                        rows="2"
                        required
                      ></textarea>
                      <div class="invalid-feedback">
                        Please provide Description.
                      </div>
                    </div>
                  </div>
                  <div class="form-row"></div>

                  <!-- <div class="form-row">
                    <div class="col-sm-12">
                      <div class="form-group">
                        <label for="exampleFormControlTextarea1">Your Message</label>
                        <textarea class="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
                      </div>
                    </div>
                  </div> -->
                  <div class="form-row"></div>
                </form>
                <div class="col-sm-12 text-center">
                  <button class="btn-full-bibbona-sm" v-on:click="createEvent">
                    Create Event
                  </button>
                </div>
              </div>

              <!-- /.Form -->
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- /.Contact us -->

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
    Datepicker,
  },
  // created: function() {
  //   this.indexBeers();
  // },
  mounted: function() {
    // this.indexBeers();
  },
  methods: {
    // indexBeers: function() {
    //   axios.get("/api/beers").then((response) => {
    //     this.beers = response.data;
    //     console.log("All Beers", this.beers);
    //   });
    // },
    createEvent: function() {
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
      axios
        .post("/api/beers", beerParams)
        .then(response => {
          console.log("beer added", response.data);
        })
        .then(
          axios.post("/api/events", eventParams).then(response => {
            console.log("event added", response.data);
          })
        )
        .then(this.$router.push("/"));
    },
  },
};
</script>
