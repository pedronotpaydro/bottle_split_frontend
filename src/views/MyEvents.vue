<template>
  <div class="myevents">
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
    <a id="my_events"></a>
    <!-- /.Event Header -->
    <section class="" id="menu01">
      <div class="menu_wrap">
        <div class="menu_title ">
          <h2>My Events</h2>
          <hr class="dotted_divider_center_red" />
        </div>
      </div>
    </section>
    <!-- Events List -->
    <section id="events_list">
      <div class="container-fluid">
        <div class="row">
          <div class="col-lg-3 col-md-6 col-sm-6" v-for="event in events" :key="event.id">
            <div class="event_card h-100">
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
                    <p>{{ event.beer_description }}</p>

                    <button class="btn-full-bibbona-sm" v-on:click="showEvent(event)">
                      More info
                    </button>
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
              <div class="card-footer">
                <small class="text-muted">Last updated {{ event.ago }} ago</small>
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
  created: function() {
    this.indexEvents();
  },
  methods: {
    indexEvents: function() {
      axios.get("/api/events?my_events=this_user").then(response => {
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
        console.log("Event Updated", event.id, response.data);
      });
    },
  },
};
</script>
