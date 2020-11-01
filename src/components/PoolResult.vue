<template>

  <v-container>
    <v-row class="text-center">
        <v-col cols="12">
            <h2>Hello from Result window</h2>
            <p>I am {{username}}</p>

            <v-progress-circular
            :rotate="360"
            :size="100"
            :width="15"
            :value="value"
            color="teal"
            >
            {{ value }}
            </v-progress-circular>


        </v-col>
    </v-row>
    <v-col>
        <v-progress-linear
            v-model="value"
            height="25"
        >
            <strong>{{ Math.ceil(value) }}%</strong>
        </v-progress-linear>
    </v-col>
  </v-container>



</template>






<script>
export default {
    name:"PoolResult",
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
            value:12,
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

</style>