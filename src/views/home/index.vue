<template>
<div class="container">
  <h1>{{msg.name}}</h1>
  <the-foot/>
</div>
</template>

<script>
import TheFoot from '../../components/TheFoot'
export default {
  components: {TheFoot},
  name: 'home',
  data () {
    return {
      msg: ''
    }
  },
  created () {
    this.$nextTick(() => {
      this.$_init()
    })
  },
  methods: {
    $_init () {
      this.$http(this.$api.GetName).then(({data}) => {
        this.msg = data
      }).catch(({data}) => {
        alert(data)
      })
    }
  },
  comments: {
    TheFoot
  }
}
</script>

<style scoped>

</style>
