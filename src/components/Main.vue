<template>
  <v-container class="mx-auto" fluid style="margin: 0px; padding: 0px; width: 80% ; min-width:300px; max-width:800px;">
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/logo.png')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <h2 class="display-2 font-weight-bold mb-3">
          I have a question ...
        </h2>
      </v-col>
    </v-row>

    <v-row class="text-center" >
          <v-col class="mb-4">
            <transition name = "change-view-to-results" mode="out-in" >
                    <Vote :poolResults="poolResults" @afterVote="setVoteResult" v-if="currentStatus==='voting'"/>
                    <PoolResult  :poolResults="poolResults" v-if="currentStatus==='show-results'"/>
            </transition>
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
                'question':"Where do the birds go when it's cold?",
                'numberOfVotes': 1197,
                'questionAnswerYes': "To Africa",
                'questionAnswerNo': "To America",
                'numberOfYes': 1001,
                'numberOfNo': 196            
      },
      currentStatus:'voting'
    }),
    methods:{
      setVoteResult(yesOrNo){
        if(typeof(yesOrNo)==='string'){ // it should be a string with 'yes' or 'no'
          this.poolResults.numberOfVotes ++;
          if (yesOrNo ==='yes'){
              this.poolResults.numberOfYes++;
          }
          if (yesOrNo ==='no'){
              this.poolResults.numberOfNo++;
          }
          this.currentStatus = "show-results";
        }
      }
    }
  }
</script>



<style lang="scss" scoped>

v-container{
  max-width: 800px;
  min-width: 400px;
}

// Configure the animation classes : "change-view" = class name + "-enter-active" or "-leave-active"

.change-view-to-results-enter-active{
    animation: bounce-in 0.5s ;
}

.change-view-to-results-leave-active{
    animation: bounce-in 0.5s reverse;
}


@keyframes bounce-in {
    0% {
        transform: scale(0);
        opacity: 0;
    }
    50% {
        transform: scale(1.5);
        opacity: 0;
    }
    100% {
        transform: scale(1);
        opacity: 1;
    }
} // @keyframes bounce-in

@keyframes fade-in {
    0% {
        opacity: 0;
    }
    50% {
        opacity: 0;
    }
    100% {
        opacity: 1;
    }
}//@keyframes fade-in

PoolResultLineChart{

}

PoolResultPieChart{

}

.view-transition{

}

</style>
