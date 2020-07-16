<template>
<div>
              <!--<div class="self-center full-width no-outline">{{ sitename }}</div>-->
              <!--
              <head>
                <title>Skład dla zwierzaków :: Vue.js</title>
                <script src="https://unpkg.com/vue"></script>
                <link rel="stylesheet"  href="assets/css/app.css" />
                <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u"
                  crossorigin="anonymous">
                <meta charset="UTF-8">
              </head>
              -->
      <div id="app">
              <!--
              <header>
                <div class="navbar navbar-default">
                  <div class="navbar-header">-->
                    <!--<h1 v-text="sitename"></h1>-->
                    <div class="self-center full-width no-outline">{{ sitename }}</div>
              <!--
                  </div>
                </div>
              </header>
              -->
          <div class="row">
                      <div class="col-md-2 col-md-offset-1">
                        <figure>
                          <!--<img style="height:90px; width:90px;" :src="product.src"> -->
                          <img style="height:90px; width:90px;" src='~statics/quasar-logo-full.svg'>
                        </figure>
                      </div>
              <div class="col-md-6 col-md-offset-2 description">
                <h1 v-text="product.title"></h1>
                <p v-html="product.description"></p>
                <p class="price">
                  {{product.price | formatPrice}}
                </p>
              </div>
          </div>
      </div>

</div>
</template>

<script>
var APP_LOG_LIFECYCLE_EVENTS = true
// import image from '@/assets/product-fullsize.png'
export default {
  data () {
    return {
      sitename: 'Skład dla bydlaków...',
      product: {
        id: 1001,
        title: 'Karma dla zwierza 10',
        description: '10 kg karmy <em> wow </em>!',
        price: 6700
        // src: 'img/quasar-logo-full.svg'
        // image
        // image: './assets/product-fullsize.png'
        // image: './statics/product-fullsize.png'
      }
    }
  },

  filters: {
    formatPrice (price) {
      if (!parseInt(price)) { return '' }
      if (price > 99999) {
        var priceString = (price / 100).toFixed(2).replace('.', ',')
        var priceArray = priceString.split('').reverse()
        var index = 3
        while (priceArray.length > index + 3) {
          priceArray.splice(index + 3, 0, ' ;')
          index += 4
        }
        return priceArray.reverse().join('') + ' zł'
      } else {
        return (price / 100).toFixed(2).replace('.', ',') + ' zł'
      }
    }
  },

  computed: {

  },

  beforeCreate: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**beforeCreate')
    }
  },
  created: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      // debugger
      console.log('**created: sitename-> ' + this.sitename)
    }
  },
  beforeMount: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**beforeMount')
    }
  },
  mounted: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**mounted')
    }
  },
  beforeUpdate: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**beforeUpdate')
    }
  },
  updated: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**updated')
    }
  },
  beforeDestroy: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**beforeDestroy')
    }
  },
  destroyed: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**destroyed')
    }
  }
}
</script>
