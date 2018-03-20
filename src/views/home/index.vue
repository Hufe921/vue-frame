<template>
<div class="container">
  <h1>{{msg.name}}</h1>
  <p>by {{screen}}</p>
  <the-foot/>
</div>
</template>

<script>
import TheFoot from '../../components/TheFoot'
import { createNamespacedHelpers } from 'vuex'
const {mapState, mapMutations, mapGetters, mapActions} = createNamespacedHelpers('home')

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
    },
    ...mapMutations(['updateScreenByMutation']),
    ...mapActions(['updateScreenByAction']),
    byMutation () {
      this.updateScreenByMutation('mutation')
    },
    byAction () {
      this.updateScreenByAction('action')
    }
  },
  computed: {
    ...mapState(['screen']),
    ...mapGetters(['getterMsg'])
  },
  comments: {
    TheFoot
  }
}
</script>

<style scoped>

</style>
