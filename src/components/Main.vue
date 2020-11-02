<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/logo.svg')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Welcome to My Pool Challenge
        </h1>
      </v-col>
    </v-row>



    <v-row class="text-center" v-if="currentStatus==='voting'">
      <v-col class="mb-4">
        <Vote :poolResults="poolResults" @afterVote="setVoteResult"/>
      </v-col>
    </v-row>   

    <v-row class="text-center" v-if="currentStatus!=='voting'">
      <v-col class="mb-4">
        <PoolResult  :poolResults="poolResults"/>
      </v-col>
    </v-row>

  </v-container>
</template>

<script>
import Vote from './Vote';
import PoolResult from './PoolResult';

  export default {
    name: 'Main',
    components : {Vote, PoolResult},
    data: () => ({
      poolResults:{
                'question':"Where to the birds in winter fly ?",
                'numberOfVotes': 1197,
                'questionAnswerYes': "To Africa",
                'questionAnswerNo': "To America",
                'numberOfYes': 1001,
                'numberOfNo': 196            
      },
      currentStatus:'voting'
    }),
    methods:{
      setVoteResult(number){
        console.log("Vote result is back !"+number);
        this.currentStatus = "show-results";
      }
    }
  }
</script>
