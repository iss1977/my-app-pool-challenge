<template>

  
    <v-row class="my-vote-window text-center">
      <v-col cols="12">
          <h2>Hello from Vote</h2>
          <p>I am {{username}}</p>

            <v-banner
                elevation="4"
                slot="icon"
            >
                <svg-icon slot ="icon" type="mdi" :path="path" ></svg-icon>

                <h2>Corona safe?</h2>
            </v-banner>

      </v-col>
    
    
      <v-col cols="12">
            <v-card
                color="#385F73"
                dark
            >
                <v-card-title class="headline">
                Unlimited music now
                </v-card-title>

                <v-card-subtitle>Listen to your favorite artists and albums whenever and wherever, online and offline.</v-card-subtitle>

                <v-card-actions>
                <v-btn text>
                    Listen Now
                </v-btn>
                </v-card-actions>
            </v-card>
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
        username:{
            type: String,
            required: true
        }
    },
    methods:{
        favoriteTwoot(id){
            this.$emit('favourite',id);
        }
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

    &:hover{
        transform: rotate3d(1,1,1,45deg);
        transform: scale(1.1,1.1);
    }

   

} // end of .twoot-item




</style>