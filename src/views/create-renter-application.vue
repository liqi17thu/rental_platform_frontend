// writen by xyh
<template>
  <div>
    <new-renter-application-card></new-renter-application-card>
  </div>
</template>

<script>
import newRenterApplicationCard from '../components/create-card/new-renter-application-card.vue'
export default {
  components: {
    'new-renter-application-card': newRenterApplicationCard
  },
  created () {
    if (this.$store.getters.getUserKey === 'null') {
      this.$router.push('/login')
    }
  }
}
</script>
