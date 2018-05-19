<template>
  <div>
    <div class="clearfix">
      <div class="float-left"><h2>Zalogowałeś się jako {{ user }}</h2></div>
      <div class="float-right"><button @click="logout()">Wychodzę</button></div>
    </div>
    <hr>
    <meeting-page/>
  </div>
</template>

<script>
  import MeetingPage from "./MeetingPage";
  export default {
    props: ['user'],
    data () {
      return {
      }
    },
    methods: {
      logout() {
        this.$emit('logout');
      }
    },
    components: {
      MeetingPage},
  }
</script>

