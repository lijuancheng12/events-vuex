<template>
  <div id="events">
    <h1>Events</h1>
    <EventDetails v-for="event in events" :key="event.id" v-bind:event="event" />
  </div>
</template>

<script>
import EventDetails from "../components/EventDetatils";
import { mapActions } from "vuex";
export default {
  components: { EventDetails },

  methods: {
    ...mapActions(["getEvents"])
  },
  computed: {
    events() {
      return this.$store.state.events;
    }
  },

  created() {
    this.getEvents();
  }
};
</script>

<style lang="scss" scoped>
@import "../scss/main.scss";
#events {
  height: 100vh;
  text-align: center;
  width: 100vw;
  margin: auto;
  background: $purple;

  h1 {
    font-style: normal;
    font-size: 40px;
    color: $pink;
    padding-top: 5%;
    text-align: center;
    margin-bottom: 100px;
  }
}
</style>