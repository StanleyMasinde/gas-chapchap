<template>
  <v-app>
    <v-app-bar app flat color="blue darken-3" dark>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-toolbar-title>Gas Chap Chap</v-toolbar-title>

      <v-spacer></v-spacer>
      <v-btn @click="dialog = true" dark large rounded outlined>Order Gas Online</v-btn>
      <div class="hidden-md-and-down">
        <v-btn text to="/">Home</v-btn>
        <v-btn text to="/about" link>About</v-btn>
        <v-btn text to="/how-it-works">How It Works</v-btn>
      </div>
    </v-app-bar>
    <v-dialog
      overflow
      v-model="dialog"
      scrollable
      :overlay="true"
      persistent
      transition="dialog-transition"
    >
      <v-card flat pa-5>
        <v-layout justify-start pa-3 ma-5>
          <v-flex md>
            <v-btn @click="dialog  = false" block light x-large rounded outlined color="success">Cancel</v-btn>
          </v-flex>
        </v-layout>
        <v-layout justify-center align-center>
          <v-flex xs12 md8>
            <v-stepper v-model="e6">
              <v-stepper-header flat>
                <v-stepper-step :complete="e6 > 1" step="1">Select Gas vendor</v-stepper-step>
                <v-stepper-step :complete="e6 > 2" step="2">CHoose the service type</v-stepper-step>
                <v-stepper-step :complete="e6 > 3" step="3">Select your Location</v-stepper-step>
                <v-stepper-step step="4">Payment</v-stepper-step>
              </v-stepper-header>

              <v-stepper-content step="1">
                <v-card color="grey lighten-1" class="mb-12" height="200px">
                  Select Vendor
                </v-card>
                <v-btn color="primary" @click="e6 = 2">Continue</v-btn>
              </v-stepper-content>

              <v-stepper-content step="2">
                <v-card color="grey lighten-1" class="mb-12" height="200px">
                  Choose service type
                </v-card>
                <v-btn color="primary" @click="e6 = 3">Continue</v-btn>
              </v-stepper-content>

              <v-stepper-content step="3">
                <v-card color="grey lighten-1" class="mb-12" height="200px">
                  Select your location
                </v-card>
                <v-btn color="primary" @click="e6 = 4">Continue</v-btn>
              </v-stepper-content>

              <v-stepper-content step="4">
                <v-card color="grey lighten-1" class="mb-12" height="200px">
                  Payment
                </v-card>
                <v-btn color="primary" @click="e6 = 1">Continue</v-btn>
              </v-stepper-content>
            </v-stepper>
          </v-flex>
        </v-layout>
      </v-card>
    </v-dialog>
    <v-content>
      <router-view />
    </v-content>
    <div class="hidden-lg-and-up">
    <v-bottom-navigation app fixed absolute color="primary">
      <v-btn to="/" value="recent">
        <span>Home</span>
        <v-icon>home</v-icon>
      </v-btn>

      <v-btn to="/about" value="favorites">
        <span>About</span>
        <v-icon>info_outline</v-icon>
      </v-btn>

      <v-btn to="/how-it-works" value="nearby">
        <span>How it works</span>
        <v-icon>lightbulb_outline</v-icon>
      </v-btn>
    </v-bottom-navigation>
    </div>
  </v-app>
</template>

<script>
import OrderGasVue from "./components/OrderGas.vue";
export default {
  name: "App",
  components: OrderGasVue,
  data: () => ({
    dialog: false,
    gasVendor: null,
    e6: 1
  })
};
</script>
