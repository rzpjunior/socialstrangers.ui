<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <PostCard/>
      <Register/>
    </v-col>
  </v-row>
</template>
<script>
export default {
  data () {
    return {
      posts: [],
      msg: '',
    }
  }
}
</script>
