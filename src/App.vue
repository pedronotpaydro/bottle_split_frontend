<template>
  <div id="app">
    <!-- Header Home Page
    <header id="home_header">
      <div class="container">
        <div class="row">
          <div class="col-md-8 offset-md-2">
            <div class="logo-badge">
              <img
                src="cafe-bibbona/imgs/logo-badge/cafe-bibbona-badge.svg"
                width="300"
                height="115"
                class="img-fluid mx-auto d-block"
                alt="Café Bibbona - Coffee & Bakes"
              />
            </div>
            <h1>Bottle Split - Share your favorite beers</h1>
          </div>
        </div>
      </div>
    </header> -->
    <!-- Navigation -->
    <div class="fixed-top">
      <nav id="main_nav" class="navbar navbar-expand-lg navbar-light">
        <div class="container-fluid">
          <a class="navbar-brand" href="/">Bottle Split</a>
          <button
            class="custom-toggler navbar-toggler"
            type="button"
            data-toggle="collapse"
            data-target="#navbarResponsive"
            aria-controls="navbarResponsive"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarResponsive">
            <ul class="navbar-nav ml-auto">
              <li class="nav-item active">
                <a class="nav-link " href="/">Home</a>
              </li>
              <li class="nav-item">
                <a class="nav-link " v-if="isLoggedin()" href="/create">Create an event</a>
              </li>
              <li class="nav-item">
                <a class="nav-link " v-if="isLoggedin()" href="/events">All Events</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" v-if="isLoggedin()" href="/myevents">My Events</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" v-if="!isLoggedin()" href="/signup">Signup</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" v-if="!isLoggedin()" href="/login">Login</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" v-if="isLoggedin()" href="/logout">Logout</a>
              </li>
            </ul>
          </div>
        </div>
      </nav>
    </div>
    <!-- /.Navigation -->

    <router-view />
    <!-- Section Footer -->
    <footer class="dark_footer">
      <div class="container">
        <div class="footer_wrap">
          <div class="row">
            <div class="col-md-4">
              <div class="social">
                <ul class="list-inline">
                  <li class="list-inline-item">
                    <a href="#"><i class="fab fa-facebook"></i></a>
                  </li>
                  <li class="list-inline-item">
                    <a href="#"><i class="fab fa-twitter-square"></i></a>
                  </li>
                  <li class="list-inline-item">
                    <a href="#"><i class="fab fa-instagram"></i></a>
                  </li>
                </ul>
                <p class="email"><a href="mailto:bake@cafebibbona.com">bake@cafebibbona.com</a></p>
                <p class="phone"><a href="tel:+44702412887">(+44) 702 412 887</a></p>
              </div>
            </div>
            <div class="col-md-4">
              <div class="address">
                <h3>Café Bibbona</h3>
                <p class="location">
                  17, Orchard Street
                  <br />
                  Cornwall, TR5 3AY, UK
                </p>
              </div>
            </div>
            <div class="col-md-4">
              <div class="hours">
                <h3>Opening hours</h3>

                <ul class="list-unstyled">
                  <li class="">8 am to 5 pm (Monday - Friday)</li>
                  <li class="">8 am to 12 noon (Saturday & Sunday)</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </footer>
    <!-- /.Section Footer -->
  </div>
</template>

<style></style>
<script>
export default {
  data: function() {
    return {
      flashMessage: "",
    };
  },
  methods: {
    isLoggedin: function() {
      if (localStorage.getItem("jwt")) {
        return true;
      } else {
        return false;
      }
    },
    getUserId: function() {
      return localStorage.getItem("user_id");
    },
  },
};
</script>
