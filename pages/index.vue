<template>
  <div>
    <div class="text-right">
      <p class="sort">
        Sort Image by Category

        <v-menu
          bottom
          left
          offset-y
          origin="top right"
          transition="scale-transition"
        >
          <template v-slot:activator="{ attrs, on }">
            <v-btn text v-bind="attrs" v-on="on" class="sort-btn"
              >All <v-icon>expand_more</v-icon>
            </v-btn>
          </template>

          <v-list width="200px" dense class="py-0">
            <v-list-item to="#" class="py-0 my-0">
              <v-list-item-content class="py-0 my-0">
                <v-list-item-title>Food </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item class="py-0 my-0">
              <v-list-item-content class="py-0 my-0">
                <v-list-item-title>Wedding Images</v-list-item-title>
              </v-list-item-content>
            </v-list-item>

            <v-list-item to="#">
              <v-list-item-content>
                <v-list-item-title>Portrait </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item to="#">
              <v-list-item-content>
                <v-list-item-title>Model Shorts </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-menu>
      </p>
    </div>
    <div class="masonry mt-10">
      <div class="grid" v-for="(i, index) in images" :key="index">

          <img :src="i" class="imm" />
          <!-- <v-card v-if="hover"
            class="pa-2"
            flat
            style="
              border-top: 2px solid #ffaa0a;
              margin-top: -49px;
              border-radius: 0 0 10px 10px;
            "
          >
            <div class="d-flex justify-space-between">
              <div>
                <v-icon small>favorite_border</v-icon><small>5,328</small>
              </div>
              <div><v-icon small>favorite_border</v-icon><small>54</small></div>
              <div>
                <v-icon small>far fa-eye-slash</v-icon><small>20,328</small>
              </div>
            </div>
          </v-card> -->

          <div class="grid__body">
            <div class="relative">
              <a
                class="grid__link"
                href="javascript:void(0)"
                @click=";(activeImage = i), (overlay = true)"
              ></a>
            </div>
            <div class="mt-auto"></div>
          </div>
      <!-- </v-hover> -->
        </div>

    </div>
    <v-overlay color="black" v-model="overlay" opacity="0.9">
      <div class="text-right" style="width: 100%">
        <v-icon @click="overlay = false" class="text-right">clear</v-icon>
      </div>
      <div class="d-flex flex-column align-center">
        <v-img
          :src="activeImage"
          height="400"
          width="400"
          style="margin-bottom: 70%"
        ></v-img>
        <div
          class="d-flex justify-space-between"
          style="bottom: 0; position: absolute"
        >
          <v-img
            class="mx-4 grow"
            v-for="(i, index) in images"
            style="border-radius: 10px"
            :key="index"
            @click="changeImage(i)"
            :src="i"
            :class="i == activeImage ? 'active' : null"
            width="64"
            height="64"
          ></v-img>
        </div>
      </div>
    </v-overlay>
  </div>
</template>

<script>
export default {
  data() {
    return {
      overlay: false,
      activeImage: '',
      images: [
        require('../static/assets/alex-munsell-auIbTAcSH6E-unsplash.jpg'),
        require('../static/assets/brooke-lark-jUPOXXRNdcA-unsplash.jpg'),
        require('../static/assets/casey-lee-awj7sRviVXo-unsplash.jpg'),
        require('../static/assets/chad-montano-eeqbbemH9-c-unsplash.jpg'),
        require('../static/assets/davide-cantelli-jpkfc5_d-DI-unsplash.jpg'),
        require('../static/assets/eaters-collective-pLKgCsBOiw4-unsplash.jpg'),
        require('../static/assets/edgar-castrejon-1SPu0KT-Ejg-unsplash.jpg'),
        require('../static/assets/eiliv-sonas-aceron-ZuIDLSz3XLg-unsplash.jpg'),
        require('../static/assets/emy-XoByiBymX20-unsplash.jpg'),
        require('../static/assets/jimmy-dean-Jvw3pxgeiZw-unsplash.jpg'),
        require('../static/assets/joseph-gonzalez-fdlZBWIP0aM-unsplash.jpg'),
        require('../static/assets/monika-grabkowska-P1aohbiT-EY-unsplash.jpg'),
        require('../static/assets/lily-banse--YHSwy6uqvk-unsplash.jpg'),
        require('../static/assets/rachel-park-hrlvr2ZlUNk-unsplash.jpg'),
      ],
    }
  },
  methods: {
    changeImage(image) {
      this.activeImage = image
    },
  },
}
</script>
<style lang="scss" scoped>
.masonry {
  columns: 3;
  column-gap: 16px;
  @media (max-width: 1200px) {
    columns: 3;
  }
  @media (max-width: 992px) {
    columns: 2;
  }
  //@media (max-width: 768px) {columns: 1;}
  .grid {
    display: inline-block;
    margin-bottom: 16px;
    position: relative;
    // &:hover{
    //     border: 2px solid #FFAA0A;
    //     border-radius: 10px;
    //   }
    &:before {
      border-radius: 10px;
      content: '';
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      background-color: rgba(0, 0, 0, 0.2);
    }
    img {
      width: 100%;
      border-radius: 10px;
    }
    &__title {
      font-size: 28px;
      font-weight: bold;
      margin: 0px 0px 10px 0px;
    }
    &__author {
      font-size: 14px;
      font-weight: 300;
    }
    &__link {
      position: absolute;
      left: 0;
      right: 0;
      top: 0;
      bottom: 0;
    }
    &__body {
      position: absolute;
      left: 0;
      right: 0;
      top: 0;
      bottom: 0;
      padding: 30px 30px;
      color: #fff;
      display: flex;
      flex-direction: column;
    }
    &__tag {
      background-color: rgba(255, 255, 255, 0.8);
      color: #333;
      border-radius: 5px;
      padding: 5px 15px;
      margin-bottom: 10px;
    }
  }
}
.mt-auto {
  margin-top: auto;
}
.sort {
  font: normal normal normal 14px/21px Poppins;
  letter-spacing: -0.2px;
  color: #4d4d4d;
  opacity: 1;
}
.sort-btn {
  background: #fef5e6 0% 0% no-repeat padding-box;
  border-radius: 4px;
  opacity: 1;
}
.grow {
  transition: all 0.2s ease-in-out;
  &.active {
    transform: scale(1.5);
    border: 2px solid #f29f05;
  }
}
.imm {
  &:hover {
    border: 2px solid #ffaa0a !important;
  }
}
</style>
