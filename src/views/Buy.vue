<template>
  <div id="container">
    <router-link class="back" to="/events">Back</router-link>
    <h3 class="top">
      You are about to score
      <br />some tickets to
    </h3>
    <TicketInformation v-bind:event="event" />
    <button class="book" @click="goToTickets">Beställ</button>
  </div>
</template>

<script>
import TicketInformation from "../components/TicketInformation";
import { mapActions } from "vuex";
export default {
  components: {
    TicketInformation
  },
  methods: {
    ...mapActions(["buyTicket"]),
    async goToTickets() {
      await this.buyTicket(this.event);
      this.$router.push("/tickets");
    }
  },
  computed: {
    event() {
      return this.$store.state.event;
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../scss/main.scss";
#container {
  border-top: 1px solid $purple;
  text-align: center;
  color: #2c3e50;
  box-sizing: border-box;
  background-color: $purple;
  height: 100vh;
  width: 100vw;
  margin: auto;
  .back{
            color: $purple;
            margin-left: 20px;
            margin-top: 20px;
            position: absolute;
            font-weight: bold;
            left:50px;
            text-decoration: none;
            color:$pink;
             &:hover {
                color: $white;
             }
   }
  .top {
    margin: 80px 0 0 0;
    font-family: "Fira Sans";
    font-style: italic;
    font-size: 19px;
    text-align: center;
    color: rgba(255, 255, 255, 0.8);
  }
  .book {
    width: 30%;
    height: 60px;
    background: $green;
    border-radius: 3px;
    border: none;
    outline: none;
    color: $white;
    font-weight: 600;
    font-size: 22px;
    cursor: pointer;
  }
}

</style>