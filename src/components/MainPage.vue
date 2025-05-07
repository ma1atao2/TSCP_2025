<template>
  <v-container>
    <!-- <div class="mt-3" v-for="(question, index) in questions" :key="question+ index"
    v-show="question.id == index">
      
    </div> -->
    <questionPage
      v-for="question of questions.slice(questionNumber, questionNumber + 1)"
      :key="question.id"
      :question="question"
      @AnswerGot="getRandomQuestion"
    />
  </v-container>
</template>

<script>
import questionPage from "../components/questionPage";
export default {
  name: "MainPage",
  components: { questionPage },
  data() {
    return {
      selected: null,
      questionNumber: null,
      questionCount: 1,
      questions: [
        {
          id: 0,
          name: "question1",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 1,
          name: "question2",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 2,
          name: "question3",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 3,
          name: "question4",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 4,
          name: "question5",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 5,
          name: "question6",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 6,
          name: "question7",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 7,
          name: "question8",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 8,
          name: "question9",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 9,
          name: "question10",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 10,
          name: "question11",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 11,
          name: "question12",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 12,
          name: "question13",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 13,
          name: "question14",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 14,
          name: "question15",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 15,
          name: "question16",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 16,
          name: "question17",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 17,
          name: "question18",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 18,
          name: "question19",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
        {
          id: 19,
          name: "question20",
          answer1: "answ1",
          answer2: "answ2",
          answer3: "answ3",
          answer4: "answ4",
        },
      ],
    };
  },
  methods: {
    nextNumber(i) {
      this.questionNumber += i;
      console.log(this.questionNumber);
    },
    getRandomInt(max) {
      return Math.floor(Math.random() * max);
    },
    getRandomQuestion() {},
    get_seed(user) {
      var seed = `${user["group"]}${user["user_name"]}${user["user_surname"]}`;
      // console.log(seed)
      return seed;
    },
    cyrb128(str) {
      let h1 = 1779033703,
        h2 = 3144134277,
        h3 = 1013904242,
        h4 = 2773480762;
      for (let i = 0, k; i < str.length; i++) {
        k = str.charCodeAt(i);
        h1 = h2 ^ Math.imul(h1 ^ k, 597399067);
        h2 = h3 ^ Math.imul(h2 ^ k, 2869860233);
        h3 = h4 ^ Math.imul(h3 ^ k, 951274213);
        h4 = h1 ^ Math.imul(h4 ^ k, 2716044179);
      }
      h1 = Math.imul(h3 ^ (h1 >>> 18), 597399067);
      h2 = Math.imul(h4 ^ (h2 >>> 22), 2869860233);
      h3 = Math.imul(h1 ^ (h3 >>> 17), 951274213);
      h4 = Math.imul(h2 ^ (h4 >>> 19), 2716044179);
      (h1 ^= h2 ^ h3 ^ h4), (h2 ^= h1), (h3 ^= h1), (h4 ^= h1);
      return [h1 >>> 0, h2 >>> 0, h3 >>> 0, h4 >>> 0];
    },
    // Side note: Only designed & tested for seed generation,
    // may be suboptimal as a general 128-bit hash.
    get_rand(str) {
      var arr = this.cyrb128(str);
      // console.log(arr)
      for (var j = 0; j < 7; j++) {
        for (var i = 0; i < 4; i++) {
          arr.push(this.cyrb128(arr[j])[i]);
        }
      }
      // console.log(arr)
      // возвращаю массив из случайных чисел
      return arr;
    },
    shuffle_arr(array, rand_num_arr) {
      console.log("array", array);
      let currentIndex = array.length;
      // While there remain elements to shuffle...
      while (currentIndex != 0) {
        // Pick a remaining element...
        let randomIndex = rand_num_arr[0] % (array.length - currentIndex + 1);
        currentIndex--;
        // And swap it with the current element.
        [array[currentIndex], array[randomIndex]] = [
          array[randomIndex],
          array[currentIndex],
        ];
      }
    },
    get_questions(r_num_array) {
      // что я делаю:
      // 1) создаю массив номеров доступных вопросов (они по порядку)
      // 2) начинаю цикл, в котором:
      //    2.1) выбирается случайный индекс массива доступных вопросов
      var answer_arr = [];
      this.questions_num_list = answer_arr;
      // список номеров вопросов
      var options_list = [];
      for (var j = 0; j < this.questions_list.length; j++) {
        options_list.push(j);
      }
      console.log("options_list", options_list);
      this.quiz_list = options_list;
      console.log("this.questions_list.length", this.questions_list.length);
      this.shuffle_arr(options_list, r_num_array);
      // this.shuffle_arr(this.quiz_list, r_num_array)
      this.questions_num_list = options_list;

      for (var i = 0; i < this.questions_num_list.length; i++) {
        this.questions_final_list.push(
          this.questions_list[this.questions_num_list[i]]
        );
      }
      console.log(this.questions_final_list);
    },
  },
  mounted() {
    // var rand_arr = this.get_rand(this.get_seed(this.user))
    //   this.generate_questions()
    //   this.get_questions(rand_arr)
    //   this.get_question_answers(rand_arr)
  },
};
</script>

<style scoped></style>
