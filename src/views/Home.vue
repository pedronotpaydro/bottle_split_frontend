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
    <!-- /.Event Header -->
    <section id="menu01">
      <div class="menu_wrap">
        <div class="menu_title">
          <h2>Upcoming Events</h2>
          <hr class="dotted_divider_center_red" />
        </div>
      </div>
    </section>
    <!-- Events List -->
    <section id="events_list">
      <div class="container-fluid">
        <div class="row">
          <div class="col-lg-3 col-md-6 col-sm-6" v-for="event in events" :key="event.id">
            <div class="event_card">
              <div class="row no-padding">
                <div class="col-md-12 no-padding">
                  <div class="card_content">
                    <h2>{{ event.name }}</h2>
                    <span>
                      <small>Hosted by: {{ event.hosted_by }}</small>
                    </span>
                    <hr class="dotted_divider_left_red" />
                    <p>{{ event.beer_description }}</p>

                    <a class="btn btn-link-bibbona-sm" v-on:click="showEvent(event)">
                      More info
                      <i class="fas fa-long-arrow-alt-right" aria-hidden="true"></i>
                    </a>
                  </div>
                  <dialog id="event-details">
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
                      <div v-if="$parent.getUserId() == currentEvent.user_id">
                        <button v-on:click="updateEvent(currentEvent)">Update</button>
                        <button v-on:click="destroyEvent(currentEvent)">Delete</button>
                      </div>
                      <div>
                        <button>Close</button>
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
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- /.Events List -->
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "",
      events: [],
      currentEvent: {},

      errors: [],
    };
  },
  mounted: function() {
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
    updateEvent: function(event) {
      var params = {
        name: this.newEventName,
        location: this.newEventLocation,
        date: this.newEventDate,
      };
      axios.patch("api/events/" + event.id, params).then(response => {
        console.log("Event Updated", response.data);
      });
    },
  },
};
</script>
