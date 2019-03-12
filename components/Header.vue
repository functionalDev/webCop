<template>
  <header>
    <nuxt-link to="/" class="left">
      <Home/>
    </nuxt-link>
    <!-- <nuxt-link to="/shopping" class="left">
      <Bulp/>
    </nuxt-link>
    <nuxt-link to="/notifications" class="right">
      <NotificationButton>
        <Bell/>
      </NotificationButton>
    </nuxt-link>
    <nuxt-link to="/user" class="right">
      <User/>
    </nuxt-link> -->
  </header>
</template>

<script>
import Home from './icons/Home';
// import User from './icons/User';
// import Bulp from './icons/Bulp';
// import Bell from './icons/Bell';
// import NotificationButton from './NotificationButton';
import gql from 'graphql-tag';
import { Fetch } from 'vue-fetch'

// you can pass in mocked fetch or Headers if required
const $ = Fetch({
  // fetch,
  // Headers,
  logging: true
})


const changeLightState = gql`
mutation changeLightState($state: Boolean = true) {
  changeLightState(state: $state)
}`;
const getLightState = gql`
query getLightState{
  lightState
}`;

export default {
  name: "",
  components: {
    // NotificationButton,
    // Bell,
    // Bulp,
    // User,
    Home
  },
  data() {
      return {
        lightState: this.getLightState(),
      };
  },
  methods: {
    getLightState() {
      // return $.get('https://192.168.178.34:8443/rest/items/Light_Living_Stair')
      //   .then(res => res.text())
      //   .then(body => JSON.parse(body))
      //   .then(response => response.state === 'ON')
      //   .catch(er => console.log(er));
    },
    toggleLight() {
      // this.lightState = !this.lightState;
      // return $.post('https://192.168.178.34:8443/rest/items/Light_Living_Stair', this.lightState ? 'ON' : 'OFF')
      // .then(res => res.text())
      // .then(body => body && JSON.parse(body))
      // .then(response => {
      //   return state;
      // })
      // .catch(er => console.log(er));
    },
  },
  // apollo: {
  //   lightState: {
  //     query: getLightState,
  //     subscribeToMore: {
  //       document: gql`subscription {
  //         lightStateUpdated
  //       }
  //       `,
  //       // Variables passed to the subscription. Since we're using a function,
  //       // they are reactive
  //       // Mutate the previous result
  //       updateQuery: (previousResult, { subscriptionData }) => {
  //         // Here, return the new result from the previous with the new data
  //         // console.log('subscriptionData', subscriptionData.data);
  //         // console.log('previousResult', previousResult.agenda);
  //         // console.log('newResult', previousResult.agenda);
  //         return subscriptionData.data.lightStateUpdated;
  //       },
  //     }
  //   },
  // },
}
</script>

<style scoped>
  button {
    background: none;
    border: none;
    outline: none;
  }
  svg.on {
    filter: drop-shadow( 0px 0px 2px white );
  }
  svg.off {
    filter: drop-shadow( 0px 0px 2px black );
  }
  svg {
    width: 50px;
    height: 50px;
    fill: white;
    padding: 15px;
  }
  svg:hover {
    padding: 10px;
  }
  a {
    color: inherit;
    text-decoration: none;
  }
  header {
    z-index: 999;
    padding: 0 10px;
    background: #006b9e;
    font-weight: 400;
    font-size: 1.5em;
    position: fixed;
    height: 3rem;
    top: 0;
    left: 0;
    width: 100vw;
    border-bottom: 1px solid lightgrey;
    display: flex;
    justify-content: flex-end;
    box-sizing: border-box;
    box-shadow: 1px 0px 1px 1px rgba(0, 0, 0, 0.2);
  }
  .logo {
    margin-right: auto;
  }
  img {
    width: 30px;
    height: 30px;
    cursor: pointer;
    opacity: 0.55;
  }
  .left:nth-child(2) {
    margin-right: auto;
  }
</style>
