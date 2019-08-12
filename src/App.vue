<template>
  <v-app>
    <v-app-bar app flat color="blue darken-3" dark>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-toolbar-title>Gas Chap Chap</v-toolbar-title>

      <v-spacer></v-spacer>
      <v-btn @click="dialog = true" dark large rounded outlined>Order Gas Online</v-btn>
      <v-btn text to="/">Home</v-btn>
      <v-btn text to="/about" link>About</v-btn>
      <v-btn text to="/how-it-works">How It Works</v-btn>
    </v-app-bar>
    <v-dialog v-model="dialog" scrollable :overlay="true" persistent transition="dialog-transition">
      <v-card flat pa-5 ma-4>
        <v-layout justify-start pa-3 ma-5>
          <v-flex md>
            <v-btn @click="dialog  = false" light x-large rounded outlined color="success">Cancel</v-btn>
          </v-flex>
        </v-layout>
        <v-layout justify-center align-center ma-4>
          <v-flex xs12 md8>
            <v-stepper v-model="e6" vertical>
              <v-stepper-step :complete="e6 > 1" step="1">Select Gas vendor</v-stepper-step>

              <v-stepper-content step="1">
                <v-card color="grey lighten-1" class="mb-12" height="200px"></v-card>
                <v-btn color="primary" @click="e6 = 2">Continue</v-btn>
                <v-btn text>Cancel</v-btn>
              </v-stepper-content>

              <v-stepper-step :complete="e6 > 2" step="2">CHoose the service type</v-stepper-step>

              <v-stepper-content step="2">
                <v-card color="grey lighten-1" class="mb-12" height="200px"></v-card>
                <v-btn color="primary" @click="e6 = 3">Continue</v-btn>
                <v-btn text>Cancel</v-btn>
              </v-stepper-content>

              <v-stepper-step :complete="e6 > 3" step="3">Select your Location</v-stepper-step>

              <v-stepper-content step="3">
                <v-card color="grey lighten-1" class="mb-12" height="200px"></v-card>
                <v-btn color="primary" @click="e6 = 4">Continue</v-btn>
                <v-btn text>Cancel</v-btn>
              </v-stepper-content>

              <v-stepper-step step="4">Payment</v-stepper-step>
              <v-stepper-content step="4">
                <v-card color="grey lighten-1" class="mb-12" height="200px"></v-card>
                <v-btn color="primary" @click="e6 = 1">Continue</v-btn>
                <v-btn text>Cancel</v-btn>
              </v-stepper-content>
            </v-stepper>
          </v-flex>
        </v-layout>
      </v-card>
    </v-dialog>
    <v-content>
      <router-view />
    </v-content>
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
