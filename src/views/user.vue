// writen by xyh
<template>
  <div>
    <user-card :id="id"></user-card>
  </div>
</template>

<script>
import userCard from '../components/card/user-card.vue'
export default {
  components: {
    'user-card': userCard
  },
  data: function () {
    return {
      id: parseInt(this.$route.params.userId)
    }
  },
  created () {
    if (this.$store.getters.getUserKey === 'null') {
      this.$router.push('/login')
    }
  }
}
</script>
