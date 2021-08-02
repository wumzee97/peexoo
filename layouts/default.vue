<template>
  <v-app dark>
    <v-app-bar
      class="white nav-bar px-8"
      flat
      :clipped-left="clipped"
      fixed
      app
    >
      <v-app-bar-nav-icon
        class="hidden-md-and-up"
        @click.stop="drawer = !drawer"
      />
      <nuxt-link to="/">
        <img src="../static/assets/logo.png" width="105" alt="" />
      </nuxt-link>
      <v-spacer />
      <nuxt-link to="#" class="nav-menu-item mx-4">
        Business Manager
      </nuxt-link>
      <nuxt-link to="#" class="nav-menu-item mx-4"> MarketPlace </nuxt-link>
      <nuxt-link to="#" class="nav-menu-item mx-4"> XooCam </nuxt-link>

      <v-menu
        bottom
        left
        offset-y
        origin="top right"
        transition="scale-transition"
      >
        <template v-slot:activator="{ attrs, on }">
          <span
            to="#"
            v-bind="attrs"
            v-on="on"
            class="nav-menu-item primary--text ml-8"
          >
            Join Peexoo <v-icon>arrow_drop_down</v-icon>
          </span>
        </template>

        <v-list width="200px" dense class="py-0">
          <v-list-item to="/profile" class="py-0 my-0">
            <v-list-item-content class="py-0 my-0">
              <v-list-item-title>Profile </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item class="py-0 my-0">
            <v-list-item-content class="py-0 my-0">
              <v-list-item-title>Settings</v-list-item-title>
            </v-list-item-content>
          </v-list-item>

          <v-list-item to="/logout">
            <v-list-item-content>
              <v-list-item-title>Logout </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
    <v-main>
      <v-container fluid px-6>
        <v-img
          class="img mb-6"
          width="100%"
          height="165"
          :src="
            require('../static/assets/joseph-gonzalez-fdlZBWIP0aM-unsplash.jpg')
          "
          style="border-radius: 10px"
        ></v-img>
        <v-row class="px-10 py-0">
          <v-col md="4" class="py-0">
            <v-card
              class="profile-card pa-6"
              min-height="500"
              flat
              v-if="showCard"
            >
              <div class="d-flex justify-end">
                <a
                  href="javascript:void(0)"
                  @click="showCard = false"
                  class="text-right hide-btn"
                  >Hide</a
                >
              </div>
              <div class="text-center">
                <v-avatar
                  size="114"
                  style="cursor: pointer"
                  @click="dialog = true"
                >
                  <v-img
                    :src="
                      require('../static/assets/tim_mcbaj_53652000_2255623191378916_4966133143083590398_n.png')
                    "
                  >
                  </v-img>
                </v-avatar>
                <h3>Ekemini Mark</h3>
                <p class="description">
                  I’m a wedding and portrait photographer based in Lagos,
                  Nigeria. I’ve been shooting weddings since I was in high
                  school (before I ever had my driver’s license!).
                </p>
              </div>
              <div class="d-flex justify-space-between">
                <div>
                  <h5 class="attributes">22.1k</h5>
                  <p class="value">Total View</p>
                </div>
                <div>
                  <h5 class="attributes">
                    <v-icon>favorite_border</v-icon> 13.1k
                  </h5>
                  <p class="value">Total Likes</p>
                </div>
                <div>
                  <h5 class="attributes">Sony 92J</h5>
                  <p class="value">Camera Lens</p>
                </div>
              </div>

              <p class="description mb-0">
                <span style="color: #4d4d4d">Category</span> <b>.</b> Food
                <b>.</b> Portrait <b>.</b> Wedding <b>.</b> Model
              </p>
              <p class="description">
                <span style="color: #4d4d4d">Location</span> Lagos, Nigeria
              </p>

              <p class="description text-center py-4">
                <v-icon color="primary">share</v-icon>www.peexoo.ai/anijohnson
              </p>
              <p class="description text-center">
                <v-icon small color="black">fab fa-twitter</v-icon
                ><v-icon color="black" class="mx-6" small
                  >fab fa-instagram</v-icon
                >
                <v-icon small color="black">fas fa-envelope</v-icon>
                <v-btn rounded class="primary ml-6" text>Book Now</v-btn>
              </p>
              <p class="sign-off mt-8">
                Built <v-icon small color="primary">fas fa-heart</v-icon> on
                Peexoo
              </p>
            </v-card>
            <div class="d-flex align-center ml-3" v-else>
              <v-avatar>
                <v-img
                  :src="
                    require('../static/assets/tim_mcbaj_53652000_2255623191378916_4966133143083590398_n.png')
                  "
                >
                </v-img>
              </v-avatar>
              <a
                href="javascript:void(0)"
                @click="showCard = true"
                class="show-card ml-4"
                >Show card</a
              >
            </div>
          </v-col>
          <v-col md="4" class="text-center pb-0">
            <v-btn rounded text to="/portfolio" class="menu-link"
              >Portfolio</v-btn
            >
            <v-btn rounded text to="/availability" class="menu-link"
              >Availability</v-btn
            >
            <v-btn rounded text to="/pricing" class="menu-link"
              >Pricing Package</v-btn
            >
          </v-col>
        </v-row>
        <v-row class="py-0" justify="end">
          <v-col :md="showCard ? 8 : 12" class="py-0">
            <nuxt />
          </v-col>
        </v-row>
      </v-container>
    </v-main>
    <v-navigation-drawer v-model="rightDrawer" :right="right" temporary fixed>
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light> mdi-repeat </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-overlay class="elevation-0" v-model="dialog" color="black" opacity="0.9">
    <div class="d-flex flex-column justify-center align-center" style="height: 100vh;">
      <v-btn @click="dialog = false" rounded width="150" text color="#383838" class="white--text">Close Image</v-btn>
        <v-avatar size="344" style="cursor: pointer; margin-top: 52%; margin-bottom:52%;">

          <v-img
            :src="
              require('../static/assets/tim_mcbaj_53652000_2255623191378916_4966133143083590398_n 2.png')
            "
          >
          </v-img>
        </v-avatar>

        <p class="text-center">
          Built for free <v-icon color="primary">favorite</v-icon> on Peexoo
        </p>

    </div>
    </v-overlay>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      showCard: false,
      dialog: false,
    }
  },
}
</script>
<style lang="scss" scoped>
.nav-bar {
  height: 70px;

  background: #ffffff 0% 0% no-repeat padding-box !important;
  box-shadow: 0px 1px 3px #00000029 !important;
  opacity: 1;
}
.nav-menu-item {
  text-align: center;
  font: normal normal normal 16px/25px Poppins;
  text-decoration: none;

  letter-spacing: -0.26px;
  color: #4d4d4d;
  opacity: 1;
}
.show-card {
  // text-align: center;
  font: normal normal normal 14px/21px Poppins;
  letter-spacing: -0.22px;
  color: #e39400;
  opacity: 1;
  text-decoration: none;
}
.profile-card {
  background: #ffffff 0% 0% no-repeat padding-box;
  border: 0.25px solid #ffb500;
  border-radius: 4px;
  position: fixed;
  width: 28%;
  // z-index: 1;

  margin-top: -150px;
  .hide-btn {
    text-align: center;
    font: normal normal normal 14px/21px Poppins;
    letter-spacing: -0.22px;
    color: #e39400;
    opacity: 1;
    text-decoration: none;
  }
  h3 {
    font: normal normal 600 30px/47px Poppins;
    letter-spacing: -1.16px;
    color: #000000;
    opacity: 1;
  }
  .description {
    // text-align: center;
    font: normal normal normal 16px/25px Poppins;
    letter-spacing: -0.26px;
    color: #000000;
    opacity: 1;
  }
  .attributes {
    text-align: left;
    font: normal normal 600 18px/27px Poppins;
    letter-spacing: -0.32px;
    color: #000000;
    opacity: 1;
  }
  .value {
    text-align: center;
    font: normal normal normal 14px/21px Poppins;
    letter-spacing: -0.22px;
    color: #4d4d4d;
    opacity: 1;
  }
  .sign-off {
    text-align: center;
    font-size: 12px;
    letter-spacing: -0.14px;
    color: #4d4d4d;
    opacity: 0.8;
  }
}
</style>
