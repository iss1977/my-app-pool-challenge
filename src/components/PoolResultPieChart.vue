<template>
    <v-row>
    <v-col>
        <h3>{{lineChartValues.questionAnswerYes}}</h3>
        <br>
        <v-progress-circular
            :rotate="360"
            :size="100"
            :width="15"
            :value="(lineChartValues.numberOfYes / lineChartValues.numberOfVotes*100).toFixed(0)+'%'"
            color="teal"
        >
            {{ (lineChartValues.numberOfYes / lineChartValues.numberOfVotes*100).toFixed(0) }} %
        </v-progress-circular>
        <br>
        <p>{{lineChartValues.numberOfYes}} votes</p>
    </v-col>

    <v-col>
        <h3>{{lineChartValues.questionAnswerNo}}</h3>
        <br>
        <v-progress-circular
            :rotate="360"
            :size="100"
            :width="15"
            :value="(lineChartValues.numberOfNo / lineChartValues.numberOfVotes*100).toFixed(0)+'%'"
            color="teal"
        >
            {{(lineChartValues.numberOfNo / lineChartValues.numberOfVotes*100).toFixed(0)+'%' }}
        </v-progress-circular>
        <br>
        <p>{{lineChartValues.numberOfNo}} votes</p>

    </v-col>
    </v-row>

</template>






<script>
export default {
    name:"PoolResultPieChart",
    props:{
        lineChartValues: {
        type: Object,
        required: true
        }
    },
    methods:{
        loadComponent(){
            console.log("Component loaded");
        }
    },
    created(){
        console.log("Created");
        console.log(this.lineChartValues.numberOfYes);
    },
    data(){
        return {
           
        }
    }
}
</script>

<style lang="scss" scoped>


</style>