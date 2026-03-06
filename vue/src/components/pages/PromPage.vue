<template>
  <div class="prom">
    {{ getPoints }}
    <div class="prom__ball" :style="styles">
      
    </div>
  </div>
</template>

<script lang="ts">
import { mapGetters, mapActions } from 'vuex';
export default {
  name: 'PromPage',
  data () {
    return {
      
    }
  },
  computed: {
    ...mapGetters('ball', [
      'getCoords',
      'getPoints'
    ]),
    styles () {
      return {
        transform: `translateX(${this.getCoords.x}px) translateY(${this.getCoords.y}px)`
      }
    }
  },
  mounted () {
    this.start()
  },
  methods: {
    ...mapActions('ball', [
      'runBall', 
      'addPoints'
    ]),
    start() {
      this.runBall()
        .then(() => {
          const x = this.getCoords.x 
          if (x === 300) {
            this.addPoints(5)
          }
          if (x === 0) {
            this.addPoints(10)
          }
          return true
        })
        .then(() => this.start())
    }
  }
}
</script>
<style scoped lang="scss">
.prom {
  
  &__ball {
    border-radius: 50%;
    background: rgb(59, 110, 181);
    width: 100px;
    height: 100px;
    transform: translateX(0) translateY(0);
    transition: 0.5s;
  }
}

</style>
