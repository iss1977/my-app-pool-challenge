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
        <v-col>
        <PoolResultLineChart :lineChartValues="poolResults" v-if="mySwitchChartLine==='line'"/>
        <PoolResultPieChart :lineChartValues="poolResults" v-if="mySwitchChartLine==='pie'"/>
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
        username:{
            type: String,
            required: true
        },
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
.twoot-item{
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border : 1px solid #DFE3E8;
    box-sizing: border-box;
    cursor: pointer;
    transition: all 0.25s ease;

    &:hover{
        transform: rotate3d(1,1,1,45deg);
        transform: scale(1.1,1.1);
    }

    .twoot-item__user{
        font-weight: bold;
    }

} // end of .twoot-item



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

// Setting the switch to fix color - regardless of state

v-radio-group{
    display : flex;
    flex-direction: row;
    margin-left: auto;

    v-radio{
        margin-left : 10px;
    }
}

</style>