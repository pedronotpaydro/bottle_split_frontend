<template>
  <div class="home">
    <!-- Event Header -->
    <header id="event_header">
      <div class="container">
        <div class="row">
          <div class="col-md-8 offset-md-2">
            <div class="align-self-center">
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
    <a id="upcoming"></a>
    <!-- /.Event Header -->
    <section class="" id="menu01">
      <div class="menu_wrap">
        <div class="menu_title ">
          <h2>
            Upcoming Events
          </h2>
          <hr class="dotted_divider_center_red" />
        </div>
      </div>
    </section>
    <!-- Events List -->
    <section id="events_list">
      <div class="container-fluid">
        <div class="row">
          <div class="col-lg-3 col-md-6 col-sm-6" v-for="event in events" :key="event.id">
            <div class="event_card ">
              <div class="row no-padding">
                <div class="col-md-12 no-padding">
                  <div class="card_content">
                    <h2>{{ event.name }}</h2>
                    <span>
                      <small>
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          width="16"
                          height="16"
                          fill="currentColor"
                          class="bi bi-person-fill"
                          viewBox="0 0 16 16"
                        >
                          <path d="M3 14s-1 0-1-1 1-4 6-4 6 3 6 4-1 1-1 1H3zm5-6a3 3 0 1 0 0-6 3 3 0 0 0 0 6z" />
                          &emsp;
                        </svg>
                        <a href="url">{{ event.hosted_by }}</a>
                      </small>
                    </span>
                    <hr class="dotted_divider_left_red" />
                    <div id="summary">
                      <p class="collapse" id="collapseSummary">{{ event.beer_description }}</p>
                      <span>
                        <small>
                          <a
                            class="collapsed"
                            data-toggle="collapse"
                            href="#collapseSummary"
                            aria-expanded="false"
                            aria-controls="collapseSummary"
                          ></a>
                        </small>
                      </span>
                    </div>

                    <button
                      v-if="$parent.getUserId() == event.user_id"
                      class="btn-full-bibbona-sm"
                      v-on:click="showEvent(event)"
                    >
                      Edit Event
                    </button>
                    <button
                      v-if="$parent.getUserId() != event.user_id"
                      class="btn-full-bibbona-sm"
                      v-on:click="showEvent(event)"
                    >
                      More Info
                    </button>
                  </div>

                  <dialog v-if="$parent.getUserId() == currentEvent.user_id" id="event-details">
                    <div class="contact_form">
                      <form method="dialog" class="needs-validation" novalidate>
                        <div class="form-row">
                          <div class="col-md-6 mb-3">
                            <label for="validationCustom03">Event name</label>
                            <input
                              v-model="currentEvent.name"
                              type="text"
                              class="form-control"
                              id="validationCustom03"
                              required
                            />
                            <div class="invalid-feedback">
                              Please provide a valid Event name.
                            </div>
                          </div>
                          <div class="col-md-6 mb-3">
                            <label for="validationCustom04">Event Date</label>

                            <Datepicker format="YYYY-MM-DD h:i:s" width="100%" v-model="currentEvent.date" />
                            <div class="invalid-feedback">
                              Please provide a valid Event Date.
                            </div>
                          </div>
                          <div class="col-md-6 mb-3">
                            <label for="validationCustom04">Event Location</label>

                            <textarea
                              class="form-control"
                              v-model="currentEvent.location"
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
                              v-model="currentEvent.beer"
                              type="text"
                              class="form-control"
                              id="validationCustom01"
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
                              v-model="currentEvent.brewery"
                              class="form-control"
                              id="validationCustom02"
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
                              v-model="currentEvent.style"
                              class="form-control"
                              id="validationCustom02"
                              required
                            />
                            <div class="invalid-feedback">
                              Please provide Style.
                            </div>
                          </div>

                          <div class="col-md-6 mb-3">
                            <label for="validationCustom02">Bottle Description</label>

                            <textarea
                              class="form-control"
                              v-model="currentEvent.beer_description"
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

                        <div class="form-row"></div>
                        <div class="col-sm-12 text-center">
                          <button class="btn-full-bibbona-sm" v-on:click="updateEvent">Edit Event</button>
                          <button class="btn-full-bibbona-sm">Close</button>
                        </div>
                      </form>
                    </div>
                    <!-- <form method="dialog">
                      <p>
                        Edit Event Name:
                        <input type="text" v-model="currentEvent.name" />
                      </p>

                      <p v-if="isLoggedin()">
                        Edit Event Location:
                        <input type="text" v-model="currentEvent.location" />
                      </p>
                      <p v-if="!isLoggedin()">
                        Log in or signup to see location
                      </p>
                      <p v-if="isLoggedin()">
                        Edit Event Date:
                        <input type="text" v-model="currentEvent.date" />
                      </p>
                      <p v-if="!isLoggedin()">
                        Log in or signup to see date
                      </p>
                      <p>
                        Edit Beer:
                        <input type="text" v-model="currentEvent.beer.name" />
                      </p>
                      <p>
                        Edit Beer Description:
                        <input type="text" v-model="currentEvent.beer_description" />
                      </p>
                      <div v-if="$parent.getUserId() == currentEvent.user_id">
                        <button v-on:click="updateEvent(currentEvent)">Update</button>
                        <button v-on:click="destroyEvent(currentEvent)">Delete</button>
                      </div>
                      <div>
                        <button>Close</button>
                      </div>
                    </form> -->
                  </dialog>
                  <dialog v-else id="event-details">
                    <form method="dialog">
                      <h1>{{ currentEvent.name }}</h1>

                      <p v-if="isLoggedin()">
                        {{ currentEvent.location }}
                      </p>
                      <p v-if="!isLoggedin()">
                        Log in or signup to see location
                      </p>
                      <p v-if="isLoggedin()">
                        {{ currentEvent.date }}
                      </p>
                      <p v-if="!isLoggedin()">
                        Log in or signup to see date
                      </p>
                      <p>
                        Menu:
                        {{ currentEvent.beer }}
                      </p>
                      <p>{{ currentEvent.beer_description }}</p>

                      <div>
                        <button>Close</button>
                        <button v-if="isLoggedin()">Add Beer</button>
                      </div>
                    </form>
                  </dialog>
                </div>
                <div class="col-md-12 no-padding">
                  <div class="event_img">
                    <img
                      class="img-fluid mx-auto d-block"
                      v-bind:src="`${event.beer_image}`"
                      width="784"
                      height="600"
                    />
                  </div>
                </div>
              </div>
              <div class="card-footer">
                <small class="text-muted">Last updated {{ event.ago }} ago</small>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- /.Events List -->
    <section id="specials">
      <div class="container">
        <div class="row">
          <div class="col-xl-12">
            <div class="specials_wrap">
              <div class="row">
                <div class="col-lg-6 col-md-12 no-padding align-self-center">
                  <div class="specials_content">
                    <h2>Nearby Events</h2>
                    <hr class="dotted_divider_left_red" />
                    <p>
                      Nearby Bottle Split Events
                    </p>
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
  </div>
</template>

<style></style>

<script>
import axios from "axios";
import Datepicker from "vuejs-datetimepicker";
export default {
  data: function() {
    return {
      message: "",
      events: [],
      currentEvent: {},

      errors: [],
    };
  },
  components: {
    Datepicker,
  },
  created: function() {
    this.indexEvents();
  },

  methods: {
    indexEvents: function() {
      axios.get("/api/events?active=live").then(response => {
        this.events = response.data;
        console.log("All Events", this.events);
      });
    },
    isLoggedin: function() {
      if (localStorage.getItem("jwt")) {
        return true;
      } else {
        return false;
      }
    },
    showEvent: function(event) {
      document.querySelector("#event-details").showModal();
      this.currentEvent = event;
    },
    destroyEvent: function(event) {
      axios.delete("/api/events/" + event.id).then(response => {
        console.log("Event Deleted", response.data);
        var index = this.events.indexOf(event);
        this.events.splice(index, 1);
      });
    },
    updateEvent: function() {
      var params = {
        name: this.currentEvent.name,
        location: this.currentEvent.location,
        date: this.currentEvent.date,
        beer: this.currentEvent.beer,
        brewery: this.currentEvent.brewery,
        description: this.currentEvent.beer_description,
        style: this.currentEvent.style,
      };

      axios.patch("/api/events/" + this.currentEvent.id, params).then(response => {
        console.log("Event Updated", response.data).then(this.$router.push("/"));
      });
    },
  },
  // updateEvent: function(event) {
  //   var params = {
  //     name: this.newEventName,
  //     location: this.newEventLocation,
  //     date: this.newEventDate,
  //   };
  // axios.patch("api/events/" + event.id, params).then(response => {
  //   console.log("Event Updated", response.data);
  //   });
  // },
};
</script>
