<template>
  <el-button type="success"
             @click="approve">通过
  </el-button>
</template>

<script>
import Axios from 'axios'
import qs from 'qs'
export default {
  props: {
    id: Number,
    target: String,
    comments: String
  },
  methods: {
    approve: function () {
      console.log(this.comments)
      const data = { comments: this.comments }
      Axios({
        url: '/api/v1/' + this.target + '/' + this.id + '/approve/',
        method: 'post',
        data: qs.stringify(data),
        headers: {
          Authorization: 'Token ' + this.$store.getters.getUserKey
        }
      })
        .then((response) => {
          location.reload()
          this.$message('通过成功')
          console.log(response)

          // this.$router.push({ name: 'admin' })
          // location.reload()
        })
        .catch((error) => {
          console.log(error.response)
          this.$alert(error.response.data)
        })
    }
  }
}
</script>
