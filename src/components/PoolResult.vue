<template>

  <v-container>
    <v-row>
        <v-col>
            <v-radio-group row v-model="mySwitchChartLine" :mandatory="false" >
                <p>Select chart type</p>
                <v-spacer></v-spacer>
                <v-radio class="my-radio" label="Line chart" value="line"></v-radio>
                <v-radio class="my-radio" label="Pie chart" value="pie"></v-radio>
            </v-radio-group>
        </v-col>

    </v-row>
    <v-row class="text-center">
        <v-col cols="12">
            <h2>{{poolResults.question}}</h2>
            <p>We got {{poolResults.numberOfVotes}} votes.</p>
        </v-col>
        <v-col class = "view-transition">
            <transition name = "change-view-line-chart" mode="out-in" >
                <PoolResultLineChart :lineChartValues="poolResults" v-if="mySwitchChartLine==='line'"/>
                <PoolResultPieChart :lineChartValues="poolResults" v-if="mySwitchChartLine==='pie'"/>
            </transition>
        </v-col>
    </v-row>
  </v-container>

</template>






<script>

import PoolResultLineChart from './PoolResultLineChart';
import PoolResultPieChart from './PoolResultPieChart';

export default {
    name:"PoolResult",
    components: {PoolResultLineChart, PoolResultPieChart},
    props:{
        poolResults:{
            type: Object,
            required : true
        }
    },
    methods:{
        favoriteTwoot(id){
            this.$emit('favourite',id);
        },
        changeSwitch(){
            console.log("Switched");
        }
    },
    data(){
        return {
            value:12,
            mySwitchChartLine: 'line'
        }
    },
    watch: { 
        mySwitchChartLine: {
            handler (val, oldVal) {
                console.log("NEW:"+val+" OLD:"+oldVal);
            // do your stuff
            }
        }
    }
}
</script>

<style lang="scss" scoped>


v-radio-group{
    display : flex;
    flex-direction: row;
    margin-left: auto;
    v-radio{
        margin-left : 10px;
    }
}

// Configure the animation classes : "change-view" = class name + "-enter-active" or "-leave-active"
.change-view-line-chart-enter-active{
    animation: bounce-in 0.5s ;
}

.change-view-line-chart-leave-active{
    animation: bounce-in 0.5s reverse;
}

.change-view-pie-chart-enter-active{
    animation: fade-in 0.5s ;
}

.change-view-pie-chart-leave-active{
    animation: fade-in 0.5s reverse;
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


</style>