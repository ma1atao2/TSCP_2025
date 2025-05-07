<template>
<v-container>
    <v-card >
        <p
          style="display: block; text-align: center"
          class="mx-a pa-10"
        >
          {{ question.name }}
        </p>
      </v-card>
      <v-row>
        <v-col>
          <v-btn
          block
            style="display: block; text-align: center"

            min-height="100"
            class="mx-a pa-5"
            color="success"
            @click="getAnswer"
            id="answer1"
            >{{question.answer1}}</v-btn
          >
        </v-col>
        <v-col>
          <v-btn
          block
            style="display: block; text-align: center"

            min-height="100"
            class="mx-a pa-5"
            color="success"
            @click="getAnswer"
            id="answer2"
            >{{question.answer2}}</v-btn
          >
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <v-btn
          block
            style="display: block; text-align: center"

            min-height="100"
            class="mx-a pa-5"
            color="success"
            @click="getAnswer"
            id="answer3"
            >{{question.answer3}}</v-btn
          >
        </v-col>
        <v-col>
          <v-btn
          block
            style="display: block; text-align: center"

            min-height="100"
            class="mx-a pa-5"
            color="success"
            @click="getAnswer"
            id="answer4"
            >{{question.answer4}}</v-btn
          >
        </v-col>
      </v-row>
</v-container>
</template>

<script>
export default{
    name: "questionPage",
    data(){
        return{

        }
    },
    props:{
        question:{},

    },
    methods:{
        getAnswer(event){
            
            console.log(event.target.id)
            this.$emit("AnswerGot", 1)
        }
    }
}
</script>

<style scoped>

</style>