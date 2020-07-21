<template>
    <div>
        <head>
          <title>Obliczanie pola prostokąta</title>
          <!-- <script src="https://unpkg.com/vue/dist/vue.js" type="text/javascript"></script> -->
        </head>
            <div>
                <div>Pole wynosi: {{ 44444 }}</div>
                <p>
                  <button v-on:click="length += 1">Inkrementuj długość</button>
                  <button v-on:click="width += 1">Inkrementuj szerokość</button>
                </p>
            </div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      length: 5,
      width: 3
  }
},

computed: {
  area: function() {
    return this.width * this.length;
  }
},

      watch: {
        length: function(newVal, oldVal) {
          console.log('Poprzednia wartość właściwości length: '
                      + oldVal +
                      '\nNowa wartość właściwości length: '
                      + newVal);
        },
        width: function(newVal, oldVal) {
          console.log('Poprzednia wartość właściwości width: '
                      + oldVal +
                      '\nNowa wartość właściwości width: '
                      + newVal);
        },
        area: function(newVal, oldVal) {
          console.log('Poprzednia wartość właściwości area: '
                      + oldVal +
                      '\nNowa wartość właściwości area: '
                      + newVal);
        }
      },

      beforeUpdate: function() {
        console.log('Wszystkie te zmiany zostały wykonane '
                    + 'przed aktualizacją wyników.');
      }
    }
  </script>
