<template>
  <div class="counter">
    <div class="count" v-text="count"></div>
    <button class="increment" @click="increment()">+</button>
    <button class="decrement" @click="decrement()">-</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      count: 0
    }
  },
  methods: {
    increment () {
      this.count++
    },
    decrement () {
      this.count--
    }
  }
}
</script>

<tests>

let wrapper

Unite.beforeEachTest (() => {
  wrapper = Unite.$mount($component)
})

/** test */
Unite.test('It defaults the count to zero', () => {
  expect(wrapper.vm.count).toBe(0)
})

/** test */
Unite.test('It decrements the current count', () => {
  wrapper.setData({ count: 7 })

  wrapper.find('.decrement').trigger('click')

  expect(wrapper.find('.count').text()).toContain(6)
})

</tests>

