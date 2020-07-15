<template>
<div>
    <head>
        <title>Tytuł ale się nie wyświetla...</title>
    </head>
    <div>
      <header>
        <div class="self-center full-width no-outline">{{ sitename }}</div>
      </header>
    </div>
</div>
</template>

<script>
var APP_LOG_LIFECYCLE_EVENTS = true

export default {
  data () {
    return {
      sitename: 'Skład dla bydlaków...',
      product: {
        id: 1001,
        title: 'Karma dla zwierza 10',
        description: '10 kg karmy <em>oprze</em>!',
        price: 6700,
        image: 'assets/images/product-fullsize.png'
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
