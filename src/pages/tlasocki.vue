<template>
  <div>
              <head>
                <title>Skład dla zwierzaków :: Vue.js</title>
                <link
                  rel="stylesheet"
                  href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css"
                  integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u"
                  crossorigin="anonymous"
                />
                <meta charset="UTF-8" />
              </head>

    <div id="app">
                          <header>
                            <div class="navbar navbar-default">
                              <div class="navbar-header">
                                <h3>{{ sitename }}</h3>
                              </div>
                              <div class="nav navbar-nav navbar-right cart">
                                <button
                                  type="button"
                                  class="btn btn-default btn-lg"
                                  v-on:click="showCheckout"
                                >
                                  Biorę
                                  <span class="glyphicon glyphicon-shopping-cart">{{ cartItemCount }}</span>
                                  szt.!
                                </button>
                              </div>
                            </div>
                          </header>

      <main>
        <div class="row product">
                    <div v-if="showProduct" class="col-md-12" >
                      <div class="col-md-2 col-md-offset-1">
                        <figure>
                          <!-- <img style="height:90px; width:90px;" :src="product.image"> -->
                          <!-- <img style="height:90px; width:90px;" src="~assets/gnomec.png"/> -->
                          <img style="height:90px; width:90px;" :src="product.image"/>
                        </figure>
                      </div>
                          <div class="col-md-7 col-md-offset-1" style="border-color: #92a8d1; border-style: outset;">
                            <!-- było md-7 za wąsko -->
                            <h4 v-text="product.title"></h4>
                            <p v-html="product.description"></p>
                            <p>
                              {{ product.price | formatPrice }}
                            </p>
                            <button class="btn btn-primary btn-lg" v-on:click="addToCart" v-if="canAddToCart">Dodaj do koszyka</button>
                            <button disabled="true" class="btn btn-primary btn-lg" v-else >Dodaj do koszyka</button>
                              <div class="rating">
                                <span v-bind:class="{'rating-active': checkRating(n)}"
                                v-for="n in 5" :key="n" style="font-size:25px;">☆
                                </span>
                              </div>
                          <div>
                            <span class="inventory-message" v-if="product.availableInventory - cartItemCount === 0" style="color:red;">Brak towaru!</span>
                            <span class="inventory-message" v-else-if="product.availableInventory - cartItemCount < 5" style="color:blue;"> Zostało tylko {{product.availableInventory - cartItemCount}}!</span>
                            <span class="inventory-message" v-else>Kupuj teraz!</span>
                        </div>
                      </div>
                    </div>
        <div v-else>
                                  <div class="col-md-12 col-md-offset-1">
                                    <div class="panel panel-info"> <!-- Panel info -->
                                      <div class="panel-heading">Formularz zamówienia</div>
                                        <div class="panel-body">

                                          <div class="form-group">
                                            <div class="col-md-12">
                                              <h4><strong>Podaj informacje o sobie</strong></h4>
                                            </div>
                                            <div class="form-group">
                                              <div class="col-md-6">
                                                <strong>Imię:</strong>
                                                <input v-model.trim="order.firstName" class="form-control" />
                                              </div>
                                              <div class="col-md-6">
                                                <strong>Nazwisko:</strong>
                                                <input v-model.trim="order.lastName" class="form-control" />
                                              </div>
                                            </div>
                                          </div>

                                          <div class="form-group">
                                            <div class="col-md-12"><strong>Adres:</strong></div>
                                            <div class="col-md-12">
                                              <input v-model.trim="order.address" class="form-control" />
                                            </div>
                                          </div>

                                          <div class="form-group">
                                            <div class="col-md-12"><strong>Miejscowość:</strong></div>
                                            <div class="col-md-12">
                                              <input v-model.trim="order.city" class="form-control" />
                                            </div>
                                          </div>

                                          <div class="form-group">
                                            <div class="col-md-3">
                                              <strong>Województwo:</strong>
                                              <select v-model="order.state" class="form-control">
                                                <option disabled value="">Województwo</option>
                                                <option v-for=" (state, key) in states" v-bind:value="state" v-bind:key="key">
                                                  {{ key }}
                                                </option>
                                              </select>
                                              </div>
                                              </div >
                                              <div class="col-md-3 col-md-offset-6">
                                                <strong>Kod pocztowy:</strong>
                                                <input v-model="order.zip" class="form-control" type="number" />
                                              </div>
                                           </div>
                                          </div>
                                          <div class="form-group">
                                            <div class="col-md-5 boxes">
                                              <input type="checkbox" id="gift" value="true"
                                                v-bind:true-value="order.sendGift"
                                                v-bind:false-value="order.dontSendGift"
                                                v-model="order.gift">
                                              <label style= "font-size:12px; margin-left: 5px;" for="gift">Wysłać jako prezent?</label>
                                            </div>
                                          </div>

                                          <div class="form-group">
                                            <div class="col-md-6 boxes col-md-offset-1">
                                              <label>Adres: </label>
                                              <input type ="radio" v-bind:value="order.home" v-model="order.method" style= "margin-left:10px;">
                                              <label style= "margin-right:10px;" for="home">Domowy</label>
                                              <input type = "radio" v-bind:value="order.business" v-model="order.method">
                                              <label style= "margin-right:0px;" for="business">Firmowy</label>

                                                        </div>
                                                                                    <div class="form-group">
                                                                                        <div class="col-md-6">
                                                                                          <button type="submit" class="btn btn-primary submit" v-on:click="submitForm">Złóż zamówienie</button>
                                                                                        </div>
<div class="col-md-12 verify">
  <pre style= "background-color: #efebe9;">
         Imię: {{order.firstName}}
     Nazwisko: {{order.lastName}}
        Adres: {{order.address}}
  Miejscowość: {{order.city}}
 Kod pocztowy: {{order.zip}}
  Województwo: {{order.state}}
       Metoda: {{order.method}}
      Prezent: {{order.gift}}
  </pre>
</div>
                                                                                    </div>
                                                      </div>
                                    </div>  <!-- Koniec Panel info -->
                                  </div>
        </div>
      </main>
    </div>
  </div>
</template>

<script>
var APP_LOG_LIFECYCLE_EVENTS = true
import axios from 'axios'
export default {
  data () {
    return {
      sitename: 'Magazyn WINF dla urz...sów',
      showProduct: true,
      order: {
        firstName: 'Zenobiusz',
        lastName: 'Glatz',
        address: 'ul. Brzęczyszczykiewicza 4 / 4',
        city: 'Chrząszczyrzewoszyce gmina Grzmiszczosławice powiat Łękołody',
        zip: '71244',
        state: '',
        method: 'Adres domowy',
        business: 'Adres firmowy',
        home: 'Adres domowy',
        gift: 'Wyślij jako prezent',
        sendGift: 'Wyślij jako prezent',
        dontSendGift: 'Nie, można owinąć w gazetę'
      },

      states: {
        ZP: 'Zachodniopomorskie',
        MO: 'Malborsko-opolskie',
        DL: 'Dolnoślunskie',
        KP: 'Kujawsko-pomorskie',
        LB: 'Lubelskie',
        LU: 'Lubuskie'
      },

      product: {
        id: 1001,
        title: 'Zestaw komputerowy',
        description: 'Dobry do gierek (eduard):<b> doopa!<b>...',
        price: 6700,
        availableInventory: 10,
        rating: 3,
        // src: 'img/quasar-logo-full.svg'
        // image
        image: 'product-fullsize.png'
        // image: './statics/product-fullsize.png'
      },
      // products: [],
      cart: []
    }
  },

  filters: {
    formatPrice (price) {
      if (!parseInt(price)) {
        return ''
      }
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

  methods: {
    addToCart: function () {
      this.cart.push(this.product.id)
      console.log(this.cart)
      console.log(this.cartItemCount)
    },
    showCheckout () {
      // this.showProduct = this.showProduct ? false: true;
      this.showProduct = !this.showProduct
      // if this.showProduct=true return 'false', if this.showProduct=false -> return 'true'
    },
    submitForm () {
      alert('Wysłano formularz!')
      // …
    },
    checkRating (n) {
      return this.product.rating - n >= 0
    }
  },

  computed: {
    cartItemCount: function () {
      return this.cart.length || '0'
    },
    canAddToCart: function () {
      return this.product.availableInventory > this.cartItemCount
    }
  },

  beforeCreate: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**beforeCreate')
    }
  },
  created: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      // debugger
      console.log('--------------------')
      console.log('**sitename-> ' + this.sitename)
      console.log('**p.id -> ' + this.product.id)
      console.log('**p.title -> ' + this.product.title)
      console.log('**p.description -> ' + this.product.description)
      console.log('**p.price -> ' + this.product.price)
      console.log('**p.availableInventory -> ' + this.product.availableInventory)
      console.log('--------------------')
      // debugger
    }
  },
  function () {
    axios.get('./products.json')
      .then((response) => {
        this.products = response.data.products
        console.log(this.products)
      })
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
      console.log('**updated -> absolute-bottom')
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

<style>
header h1{
    padding: 10px 20px;
}

body {
    max-width: 970px !important;
}
.cart {
  padding: 20px 50px;
}
.boxes {
  margin-top: 20px;
}

.verify {
  margin-top: 20px;
}

.submit {
  margin-top:20px;
  float: right;
}

.pagecheckout {
  padding: 20px 50px;
}
.description {
  font-size: 150%;
  margin-top:50px;
}

.inventory-message {
  margin-left: 20px;
  font-weight: bold;
  font-size: 120%;
}

.product {
  margin-top: 30px;
  margin-left: 20px;
  max-height:300px;
  max-width:100%;
}
/*
.figure {

}
*/
.rating-active:before {
   content: "\2605";
   position: absolute;
}
.rating {
  display: inline;
  margin-left: 10px;
  /*margin-top: 10px;
  float:right;*/
}
.rating > span {
  display: inline-block;
  position: relative;
  width: 1.1em;
}

@media (min-width: 1200px) {
    .container{
        max-width: 970px;
    }
}
</style>
