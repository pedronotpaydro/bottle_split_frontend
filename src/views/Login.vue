<template>
  <div class="login">
    <header id="event_header">
      <div class="container">
        <div class="row">
          <div class="col-md-8 offset-md-2">
            <div class="align-self-center" id="login">
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
    <section id="contact_us">
      <div class="container">
        <div class="row">
          <div class="col-xl-8 offset-xl-2 col-lg-10 offset-lg-1 col-md-10 offset-md-1 col-sm-12">
            <div class="contact_info_card">
              <!-- Title -->
              <div class="contact_title">
                <h2>Login</h2>
                <hr class="dotted_divider_center_red" />
              </div>
              <!-- /.Title -->

              <!-- Form -->

              <div class="contact_form">
                <form class="needs-validation" v-on:submit.prevent="submit()" novalidate>
                  <div class="form-row">
                    <div class="col-md-6 mb-3">
                      <label for="validationCustom02">Email</label>
                      <input
                        type="email"
                        class="form-control"
                        id="validationCustom02"
                        placeholder="Enter Email"
                        v-model="email"
                        required
                      />
                      <div class="invalid-feedback">
                        Please provide your email.
                      </div>
                    </div>
                    <div class="col-md-6 mb-3">
                      <label for="validationCustom03">Password</label>
                      <input
                        type="password"
                        class="form-control"
                        id="validationCustom03"
                        placeholder="password"
                        v-model="password"
                        required
                      />
                      <div class="invalid-feedback">
                        Please provide a valid password.
                      </div>
                    </div>
                  </div>
                  <!-- <div class="form-row">
                    <div class="col-md-6 mb-3">
                      <label for="validationCustom03">Password</label>
                      <input
                        type="password"
                        class="form-control"
                        id="validationCustom03"
                        placeholder=""
                        v-model="password"
                        required
                      />
                      <div class="invalid-feedback">
                        Please provide a valid password.
                      </div>
                    </div>
                    <div class="col-md-6 mb-3">
                      <label for="validationCustom04">Password Confirmation</label>
                      <input
                        type="password"
                        class="form-control"
                        id="validationCustom04"
                        placeholder=""
                        v-model="passwordConfirmation"
                        required
                      />
                      <div class="invalid-feedback">
                        Please provide a valid password.
                      </div>
                    </div>
                  </div> -->

                  <div class="form-row">
                    <div class="col-sm-12 text-center">
                      <button class="btn-full-bibbona-sm" value="Submit" type="submit">Submit</button>
                    </div>
                    <ul>
                      <li class="text-danger" v-for="error in errors" :key="error.id">{{ error }}</li>
                    </ul>
                  </div>
                </form>
              </div>

              <!-- /.Form -->
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- <form v-on:submit.prevent="submit()">
      <h1>Login</h1>
      <ul>
        <li class="text-danger" v-for="error in errors" :key="error.id">{{ error }}</li>
      </ul>
      <div class="form-group">
        <label>Email:</label>
        <input type="email" class="form-control" v-model="email" />
      </div>
      <div class="form-group">
        <label>Password:</label>
        <input type="password" class="form-control" v-model="password" />
      </div>
      <input type="submit" class="btn btn-primary" value="Submit" />
    </form> -->
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      email: "",
      password: "",
      errors: [],
    };
  },
  methods: {
    submit: function() {
      var params = {
        email: this.email,
        password: this.password,
      };
      axios
        .post("/api/sessions", params)
        .then(response => {
          axios.defaults.headers.common["Authorization"] = "Bearer " + response.data.jwt;
          localStorage.setItem("jwt", response.data.jwt);
          localStorage.setItem("user_id", response.data.user_id);
        })
        .then(this.$router.push("/"))
        // eslint-disable-next-line no-unused-vars
        .catch(error => {
          this.errors = ["Invalid email or password."];
          this.email = "";
          this.password = "";
        });
    },
  },
};
</script>
