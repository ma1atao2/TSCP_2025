<template>
<v-container>
    <v-card elevation="10">
      <v-app-bar flat color="primary">
        <v-toolbar-title class="text-h6 white--text pl-3">
          <!-- <p
          style="display: block; text-align:center"
          class="mx-a pa-10"
        > -->
          Вопрос №{{ question.id +1 }}
        <!-- </p> -->
        </v-toolbar-title>
      </v-app-bar>
      <v-card-text height="150" class="pa-10 text-h6" style="text-align: center;">
        {{ question.name }}
      </v-card-text>
        
      <v-card-actions>

        <v-col>
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
      </v-col>
      <v-col>
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
      </v-col>
      </v-card-actions>
      </v-card>

      
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