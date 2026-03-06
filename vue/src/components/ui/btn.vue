<template>
  <button class="btn" @click="() => add()">
    <slot>
      Кнопка
    </slot>
    <span> / {{ count }}, {{ r3 }}</span>
  </button>
</template>

<script>
export default {
  name: 'btn',
  props: {
    pr: {
      type: Number,
      default: 0,
        //required: true
    }
  },
  emits: ['more'],
  data () {
    return {
      count: 0
    }
  },
  computed: {
    r2 () {
      return this.count * this.count
    },
    r3 () {
      return this.r2 * this.count * this.pr
    }
  },
  methods: {
    add () {
      this.count +=1    
      if (this.count > 10) {
        this.$emit('more', this.count)
      }  
    }

  }
}
</script>

<style scoped lang="scss">
.btn {
  border: none;
  background: rgb(211, 181, 208);
  color:rgb(150, 36, 125);
  font-size: 18px;
  padding: 10px 20px;
}
</style>