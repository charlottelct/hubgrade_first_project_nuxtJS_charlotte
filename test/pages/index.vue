<template>
<div>
    <v-carousel>
      <v-carousel-item
        v-for="(item,i) in items"
        :key="i"
        :src="item.src"
      ></v-carousel-item>
    </v-carousel>
    <v-btn color="accent" to="/login">Login</v-btn>
</div> 
</template>

<script>
export default {
  auth: false,
  data () {
    return {
      items: [
        {
          src: 'http://cdn.oboxeditions.com/sites/prod/files/styles/gallery/public/photos/27-idees-de-bouffe-sur-le-pouce-pour-faire-changement-de-la-routine-443152.jpg'
        },
        {
          src: 'https://www.chaussu.com/media/catalog/product/cache/1/image/650x/040ec09b1e35df139433887a97daa66f/1/-/1-1-_56__1.jpg'
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/bird.jpg'
        },
        {
          src: 'https://cdn.vuetifyjs.com/images/carousel/planet.jpg'
        }
      ]
    }
  },
  methods: {
    logout () {
      this.$auth.logout()
    }
  }
}
</script>
