<template>
  Index

  <div>
    <RouterLink :to="{ name: $routes.EXAMPLE }">
     To Example
    </RouterLink>
  </div>
  <div>
    <RouterLink :to="{ name: $routes.PROM }">
     To PROM
    </RouterLink>
  </div>



  <div class="grid">
    <div class="grid__item">
      123
    </div>
    <div class="grid__item">
      123
    </div>
    <btn :pr="1" @click="() => myClick()" @more="(v) => more(v)">Нажать </btn>
    <btn v-if="p > 30"  :pr="2">Вау </btn>
    <btn v-else  :pr="2">NONONO </btn>
    <btn v-for="i in r">FOR {{ i }}</btn>
    <input v-model="text" />
    <input :value="text" @input="(e) => setText(e.target.value)"/>
    {{ ppd }}
    ////
  </div>
</template>

<script lang="ts">
import btn from './../ui/btn.vue'
import { mapGetters, mapActions } from 'vuex';
export default {
  name: 'IndexPage',
  components: {
    btn
  },
  data () {
    return {
      p: 1,
      r: [1, 2, 5],
      text: ''
    }
  },
  computed: {
    ...mapGetters({
      ppd: 'getCount'
    }),
  },
  methods: {
    ...mapActions([
      'runIncrement'
    ]),
    myClick() {
      this.p += 10
    },
    more() {
      this.runIncrement(1)
    },
    setText (v) {
      this.text = v
    }
  }
}
</script>
<style scoped lang="scss">
  .grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;

    &__item {
      border: 1px solid rgb(90, 5, 90);
      color: plum;
      
    }
  }

</style>
