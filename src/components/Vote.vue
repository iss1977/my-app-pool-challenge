<template>

  
    <v-row class="my-vote-window text-center">
        <v-col cols="12">
         
            <v-banner
                elevation="4"
                slot="icon"
            >
                <svg-icon slot ="icon" type="mdi" :path="path" ></svg-icon>

                <h2>{{poolResults.question}}</h2>
            </v-banner>
        </v-col>
        
        <v-col class="d-flex justify-space-around">
            <v-btn 
                x-large
                color="success"
                dark
                elevation="9"
                @click="castVote('yes')"
            >
                    {{poolResults.questionAnswerYes}}
            </v-btn>

            <v-btn 
                x-large
                color="success"
                dark
                elevation="9"
                @click="castVote('no')"
            >
                    {{poolResults.questionAnswerNo}}
            </v-btn>
        </v-col>

    </v-row>

    

</template>






<script>

import SvgIcon from '@jamescoyle/vue-icon'
import { mdiAutoFix  } from '@mdi/js'



export default {
    name:"Vote",
    components:{SvgIcon},
    props:{
        poolResults:{
            type: Object,
            required : true
        }
    },
    methods:{
        castVote(yesNo){
            console.log("Voted:"+yesNo);
            this.$emit('afterVote', yesNo);
        }
    },
    created: function() {
    
    
    },
    data(){
        return {
            path:mdiAutoFix ,
        }
    }
}
</script>

<style lang="scss" scoped>
.my-vote-window {
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border : 1px solid #DFE3E8;
    box-sizing: border-box;
    cursor: pointer;
    transition: all 0.25s ease;

    // &:hover{
    //     transform: rotate3d(1,1,1,45deg);
    //     transform: scale(1.1,1.1);
    // }

   

} // end of .twoot-item




</style>