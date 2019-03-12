<template>
  <section>
    <!-- <Headline> Agenda </Headline> -->
    <table cellspacing="0">
      <thead>
        <th width="15%"></th>
        <th width="30%">Topic</th>
        <th width="5%">Votes</th>
        <th width="50%">Details</th>
      </thead>
      <tbody>
        <tr v-for="card in inventory" :class="[card.labels]">
          <td>
              <button>1</button>
              <button>2</button>
              <button>3</button>
          </td>
          <td><b>{{ card.name }}</b></td>
          <td>3</td>
          <td>{{ card.desc }}</td>
        </tr>
      </tbody>
    </table>
  </section>
</template>

<script>
import gql from 'graphql-tag';
// import Headline from '~/components/Headline';
const inventory = gql`
  {
    inventory {
      name
      members
      desc
    }
  }`;
export default {
    data() {
      return {
        inventory: [{
          labels: 'JS',
          name: 'loading',
          members: '...',
        }],
      }
    },
    components: {
      // Headline,
    },
    // methods: {
    //   getMembers(card) {
    //     return card.members !== ''
    //       ? ` (${card.members})`
    //       : ''
    //   }
    // },
    apollo: {
      inventory: {
        query: inventory,
        // subscribeToMore: {
        //   document: gql`subscription {
        //     messageAdded {
        //       id
        //       text
        //     }
        //   }`,
        //   // Variables passed to the subscription. Since we're using a function,
        //   // they are reactive
        //   // Mutate the previous result
        //   updateQuery: (previousResult, { subscriptionData }) => {
        //     // Here, return the new result from the previous with the new data
        //     console.log('subscriptionData', subscriptionData.data);
        //     console.log('previousResult', ...previousResult.messages);
        //     return previousResult.messages.push(subscriptionData.data.messageAdded);
        //   },
        // }
      },
    },
  }

</script>

<style scoped>
tbody b {
  font-size: 1.5rem;
}
button {
  cursor: pointer;
  color: #240094;
  border: 1px solid #240094;
  background: transparent;
  border-radius: 10px;
  padding: 10px 15px;
  margin: 0 5px;
  outline: none;
}
button:hover {
  color: white;
  background: #240094;
}
table {
  text-align: left;
  width: 100%;
  margin: 10px auto;
  box-shadow: 1px 2px 2px 2px rgba(0, 0, 0, 0.2);
}
tr:hover {
  background-color: rgba(200, 200, 200, 0.2);
}
li {
  padding: 0 10px;
}
td {
  margin-left: 50px;
}
td, th {
  padding: 10px;
}
td {
  border-top: 1px solid lightgrey;
}

tr.js {
  background-image: linear-gradient(to left, transparent 80%, yellow);
}
tr.orga {
  background-image: linear-gradient(to left, transparent 80%, grey);
}
tr.css {
  background-image: linear-gradient(to left, transparent 80%, blue);
}
tr.html {
  background-image: linear-gradient(to left, transparent 80%, orange);
}
.js .label > div{
  color: black;
}
  /* .js > div {
    background-color: yellow;
  }
  .orga > div {
    background-color: grey;
    color: white;
  }
  .css > div {
    background-color: blue;
    color: white;
  }
  .html > div {
    background-color: orange;
    color: white;
  } */
  .label > div {
    padding: 3px 10px;
    color: white;
  }
</style>
