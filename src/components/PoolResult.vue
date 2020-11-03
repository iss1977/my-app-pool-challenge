<template>

  <v-container>
    <v-row>
        <v-col>
            <v-radio-group row v-model="mySwitchChartLine" :mandatory="false">
                <p>Select chart type</p>
                <v-spacer></v-spacer>
                <v-radio label="Line chart" value="line"></v-radio>
                <v-radio label="Pie chart" value="pie"></v-radio>
            </v-radio-group>
        </v-col>

    </v-row>
    <v-row class="text-center">
        <v-col cols="12">
            <h2>{{poolResults.question}}</h2>
            <p>There were {{poolResults.numberOfVotes}} votes casted.</p>
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
.view-transition{
    min-height: 300px;
}



.vote-window__main{

    background-color: aquamarine;
    padding: 1px;

    .vote-window__question-label{
        background-color: aliceblue;
        opacity: 60%;
        border-radius: 10px;
        box-shadow: -10px 0px 13px -7px #000000, 10px 0px 13px -7px #000000, 5px 5px 15px 5px rgba(0,0,0,0);
        margin : 20px;
        border: 1px solid darkgray;

    }

    .vote-window__buttons-area{
        margin: 10px;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        

        button{
            width : 30%;
            max-width: 300px;
            min-width: max-content;
            padding: 10px;
            transition: all 0.3s cubic-bezier(.44,.57,.89,-0.21);

            &:hover{
                transform: scale(1.1,1.3);
                opacity: 0.7;
                border : 3px solid blueviolet;
                padding:7px;
            }
        }
    }

}

//  radio group styling

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