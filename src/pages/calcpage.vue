<style>
    p, input { font-family: calibri; }
    p { white-space: pre; }
  </style>
<template>
<div>
  <br>
  <p> Kalkulatorek </p>
  <div>
    <q-input class="q-pa-xs" dense clearable v-model="textx" label="Liczba X" style="max-width: 100px; text-transform: uppercase;" />
    <q-input class="q-pa-xs" dense clearable v-model="texty" label="Liczba Y" style="max-width: 100px; text-transform: uppercase;" />
    <q-field style="max-width: 100px;">
<template v-slot:control>
    <div class="self-center full-width no-outline">{{ result }}</div>
</template>
      </q-field>
      <p>Wynik X+Y</p>
  </div>
</div>
</template>

<script>
export default {

  mounted () {
  },

  data () {
    return {
      textx: 0,
      texty: 0
    }
  },

  computed: {

    result: function () {
      function isNotNumericValue (value) {
        return isNaN(value) || !isFinite(value)
      }
      const x = parseFloat(this.textx)
      if (isNotNumericValue(x)) {
        return this.name // Recursive call
      }
      const y = parseFloat(this.texty)
      if (isNotNumericValue(y)) {
        return this.name // Recursive call
      }
      console.log('Liczba X: ' + x)
      console.log('Liczba Y: ' + y)
      console.log('Suma X+Y: ' + x + y)
      return x + y
    }
  },

  methods: {
    function () {
      function isNotNumericValue (value) {
        return isNaN(value) || !isFinite(value)
      }
      const x = parseFloat(this.textx)
      if (isNotNumericValue(x)) {
        return this.name // Recursive call
      }
      const y = parseFloat(this.texty)
      if (isNotNumericValue(y)) {
        return this.name // Recursive call
      }
      console.log('Liczba X: ' + x)
      console.log('Liczba Y: ' + y)
      console.log('Suma X+Y: ' + x + y)
      return x + y
    }
  }
}
</script>
