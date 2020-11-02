<template>
    <v-row>
        <v-col>
             <br>
            <p class="text-left">{{lineChartValues.numberOfYes}} votes</p>
            <v-progress-linear
                height="25"
                :value = "(lineChartValues.numberOfYes / lineChartValues.numberOfVotes*100).toFixed(0)+'%'"
            >
                <strong>{{(lineChartValues.numberOfYes / lineChartValues.numberOfVotes*100).toFixed(0) }}%</strong>
            </v-progress-linear>
            <br>
            <p class="text-left">{{lineChartValues.numberOfYes}} votes</p>
            <v-progress-linear
                :value = "(lineChartValues.numberOfNo / lineChartValues.numberOfVotes*100).toFixed(0)+'%'"
                height="25"
            >
                <strong>{{(lineChartValues.numberOfNo / lineChartValues.numberOfVotes*100).toFixed(0) }}%</strong>
            </v-progress-linear>

        </v-col>
    </v-row>
</template>






<script>
export default {
    name:"PoolResultLineChart",
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
        console.log(this.lineChartValues.valueYes);
    },
    data(){
        return {
           
        }
    }
}
</script>

<style lang="scss" scoped>
    p{
    margin-bottom: 2px;
    }

</style>