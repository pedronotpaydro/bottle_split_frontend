<template>
  <div class="home">
    <h1>My Events</h1>

    <div v-for="event in events" :key="event.id">
      <h2>{{ event.name }}</h2>
      <h4>Featured Bottle: {{ event.beer }}</h4>
      <h4>Hosted by: {{ event.hosted_by }}</h4>
      <h4>When : {{ event.date }}</h4>
      <h4>Where : {{ event.location }}</h4>
      <div><button v-on:click="showEvent(event)">More info</button></div>
    </div>
    <dialog id="event-details">
      <form method="dialog">
        <h1>Event Info</h1>
        <p>
          Name:
          <input type="text" v-model="currentEvent.name" />
        </p>
        <p>
          Location:
          <input type="text" v-model="currentEvent.location" />
        </p>
        <p>
          Featured Bottle:
          <input type="text" v-model="currentEvent.beer" />
        </p>
        <p>
          Description:
          <input type="text" v-model="currentEvent.beer_description" />
        </p>
        <div v-if="$parent.getUserId() == currentEvent.user_id">
          <button v-on:click="updateEvent(currentEvent)">Update</button>
          <button v-on:click="destroyEvent(currentEvent)">Delete</button>
          <button>Close</button>
        </div>
      </form>
    </dialog>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Bottle Split!",
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
      axios.get("/api/events?my_events=this_user").then(response => {
        this.events = response.data;
        console.log("All Events", this.events);
      });
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
