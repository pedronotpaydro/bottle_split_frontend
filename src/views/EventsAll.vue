<template>
  <div class="eventsall">
    <section id="menu">
      <div class="container">
        <div class="row">
          <div class="col-md-12">
            <div class="menu_wrap">
              <!-- Title -->
              <div class="menu_title">
                <h2>Upcoming Events</h2>
                <hr class="dotted_divider_center_red" />
              </div>
              <!-- /.Title -->

              <!-- Menu Content -->
              <div class="menu_content">
                <!-- Menu Filter Navigation -->
                <div class="row text-center">
                  <div class="col-lg-12">
                    <div class="menu-filter-area">
                      <ul class="menu-filter" id="menu-masonry-sort">
                        <li class="active"><a href="#" data-target=".macaroons">All</a></li>
                        <li><a href="#" data-target=".cakes">IPAs</a></li>
                        <li><a href="#" data-target=".muffins">Stouts</a></li>
                        <li><a href="#" data-target=".waffles">Sours</a></li>
                        <!-- <li><a href="#" data-target=".milkshakes">Milshakes</a></li>
                        <li><a href="#" data-target=".coffee">Coffee</a></li> -->
                      </ul>
                    </div>
                  </div>
                </div>
                <!-- /.Menu Filter Navigation -->

                <!-- Menu Items -->
                <div class="row">
                  <div class="menu-items-wrapper col-lg-12">
                    <div class="menu-items" id="menu-masonry">
                      <!-- Menu List 01 -->
                      <!-- Single Menu List -->
                      <div class="single-menu-list macaroons">
                        <div class="row">
                          <div class="col-md-6">
                            <!-- Menu Item 01 -->
                            <div class="menu-list-item" v-for="event in events" :key="event.id">
                              <h5>
                                {{ event.name }}
                                <span>
                                  <small>(Hosted by: {{ event.hosted_by }} )</small>
                                </span>
                              </h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    {{ event.beer_description }}
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">
                                    <a v-on:click="showEvent(event)" class="btn btn-link-bibbona">
                                      More
                                      <i class="fas fa-long-arrow-alt-right" aria-hidden="true"></i>
                                    </a>
                                  </p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 01 -->

                            <!-- Menu Item 02 -->

                            <!-- /. Menu Item 02 -->

                            <!-- Menu Item 03 -->

                            <!-- /. Menu Item 03 -->

                            <!-- Menu Item 04 -->

                            <!-- /. Menu Item 04 -->
                          </div>
                          <div class="col-md-6 align-self-center">
                            <!-- Menu Main List Image -->
                            <div class="menu-image">
                              <img
                                src="cafe-bibbona/imgs/menu/macaroons.png"
                                width="600"
                                height="620"
                                class="img-fluid mx-auto d-block"
                                alt="Macaroons"
                              />
                            </div>
                            <!-- Menu Main List Image -->
                          </div>
                        </div>
                      </div>
                      <!-- /.Single Menu List -->
                      <!-- /Menu List 01 -->

                      <!-- Menu List 02 -->
                      <!-- Single Menu List -->
                      <div class="single-menu-list cakes">
                        <div class="row">
                          <div class="col-md-6">
                            <!-- Menu Item 01 -->
                            <div class="menu-list-item">
                              <h5>Coconut Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 01 -->

                            <!-- Menu Item 02 -->
                            <div class="menu-list-item">
                              <h5>French Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 02 -->

                            <!-- Menu Item 03 -->
                            <div class="menu-list-item">
                              <h5>Almond Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 03 -->

                            <!-- Menu Item 04 -->
                            <div class="menu-list-item">
                              <h5>Chocolate Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 04 -->
                          </div>
                          <div class="col-md-6 align-self-center">
                            <!-- Menu Main List Image -->
                            <div class="menu-image">
                              <img
                                src="cafe-bibbona/imgs/menu/macaroons.png"
                                width="700"
                                height="620"
                                class="img-fluid mx-auto d-block"
                                alt="Macaroons"
                              />
                            </div>
                            <!-- Menu Main List Image -->
                          </div>
                        </div>
                      </div>
                      <!-- /.Single Menu List -->
                      <!-- /Menu List 02 -->

                      <!-- Menu List 03 -->
                      <!-- Single Menu List -->
                      <div class="single-menu-list muffins">
                        <div class="row">
                          <div class="col-md-6">
                            <!-- Menu Item 01 -->
                            <div class="menu-list-item">
                              <h5>Coconut Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 01 -->

                            <!-- Menu Item 02 -->
                            <div class="menu-list-item">
                              <h5>French Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 02 -->

                            <!-- Menu Item 03 -->
                            <div class="menu-list-item">
                              <h5>Almond Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 03 -->

                            <!-- Menu Item 04 -->
                            <div class="menu-list-item">
                              <h5>Chocolate Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 04 -->
                          </div>
                          <div class="col-md-6 align-self-center">
                            <!-- Menu Main List Image -->
                            <div class="menu-image">
                              <img
                                src="cafe-bibbona/imgs/menu/macaroons.png"
                                width="700"
                                height="620"
                                class="img-fluid mx-auto d-block"
                                alt="Macaroons"
                              />
                            </div>
                            <!-- Menu Main List Image -->
                          </div>
                        </div>
                      </div>
                      <!-- /.Single Menu List -->
                      <!-- /Menu List 03 -->

                      <!-- Menu List 04 -->
                      <!-- Single Menu List -->
                      <div class="single-menu-list waffles">
                        <div class="row">
                          <div class="col-md-6">
                            <!-- Menu Item 01 -->
                            <div class="menu-list-item">
                              <h5>Coconut Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 01 -->

                            <!-- Menu Item 02 -->
                            <div class="menu-list-item">
                              <h5>French Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 02 -->

                            <!-- Menu Item 03 -->
                            <div class="menu-list-item">
                              <h5>Almond Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 03 -->

                            <!-- Menu Item 04 -->
                            <div class="menu-list-item">
                              <h5>Chocolate Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 04 -->
                          </div>
                          <div class="col-md-6 align-self-center">
                            <!-- Menu Main List Image -->
                            <div class="menu-image">
                              <img
                                src="cafe-bibbona/imgs/menu/macaroons.png"
                                width="700"
                                height="620"
                                class="img-fluid mx-auto d-block"
                                alt="Macaroons"
                              />
                            </div>
                            <!-- Menu Main List Image -->
                          </div>
                        </div>
                      </div>
                      <!-- /.Single Menu List -->
                      <!-- /Menu List 04 -->

                      <!-- Menu List 05 -->
                      <!-- Single Menu List -->
                      <div class="single-menu-list milkshakes">
                        <div class="row">
                          <div class="col-md-6">
                            <!-- Menu Item 01 -->
                            <div class="menu-list-item">
                              <h5>Coconut Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 01 -->

                            <!-- Menu Item 02 -->
                            <div class="menu-list-item">
                              <h5>French Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 02 -->

                            <!-- Menu Item 03 -->
                            <div class="menu-list-item">
                              <h5>Almond Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 03 -->

                            <!-- Menu Item 04 -->
                            <div class="menu-list-item">
                              <h5>Chocolate Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 04 -->
                          </div>
                          <div class="col-md-6 align-self-center">
                            <!-- Menu Main List Image -->
                            <div class="menu-image">
                              <img
                                src="cafe-bibbona/imgs/menu/macaroons.png"
                                width="700"
                                height="620"
                                class="img-fluid mx-auto d-block"
                                alt="Macaroons"
                              />
                            </div>
                            <!-- Menu Main List Image -->
                          </div>
                        </div>
                      </div>
                      <!-- /.Single Menu List -->
                      <!-- /Menu List 05 -->

                      <!-- Menu List 06 -->
                      <!-- Single Menu List -->
                      <div class="single-menu-list coffee">
                        <div class="row">
                          <div class="col-md-6">
                            <!-- Menu Item 01 -->
                            <div class="menu-list-item">
                              <h5>Coconut Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 01 -->

                            <!-- Menu Item 02 -->
                            <div class="menu-list-item">
                              <h5>French Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 02 -->

                            <!-- Menu Item 03 -->
                            <div class="menu-list-item">
                              <h5>Almond Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 03 -->

                            <!-- Menu Item 04 -->
                            <div class="menu-list-item">
                              <h5>Chocolate Cake</h5>
                              <div class="row">
                                <div class="col-8">
                                  <p class="item-description">
                                    Contain eggs, brown sugar, vanilla, coconut, milk. Dipped in milk hazelnut
                                    chocolate.
                                  </p>
                                </div>
                                <div class="col-4">
                                  <p class="price">£ 4.00</p>
                                </div>
                              </div>
                            </div>
                            <!-- /. Menu Item 04 -->
                          </div>
                          <div class="col-md-6 align-self-center">
                            <!-- Menu Main List Image -->
                            <div class="menu-image">
                              <img
                                src="cafe-bibbona/imgs/menu/macaroons.png"
                                width="700"
                                height="620"
                                class="img-fluid mx-auto d-block"
                                alt="Macaroons"
                              />
                            </div>
                            <!-- Menu Main List Image -->
                          </div>
                        </div>
                      </div>
                      <!-- /.Single Menu List -->
                      <!-- /Menu List 06 -->
                    </div>
                  </div>
                  <!-- /.Menu Lists -->
                </div>
                <!-- /.Menu Items -->
              </div>
              <!-- /.Menu Content -->
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
      axios.get("/api/events").then(response => {
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
