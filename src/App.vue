<template>
  <Headernav />
  <lesson :lessons="lessons" v-on:object-sent="handleObject" v-if = "showLessons" v-on:showCheck-out="showCheck"/>
  <checkout :lessonscart="lessonscart" v-if = "!showLessons" v-on:showCheck-out="showLesson" v-on:object-sent="removeObject" />
</template>

<script>
import Headernav from './components/header.vue'
import lesson from './components/lesson.vue'
import checkout from './components/checkout.vue'

export default {
  name: 'App',
  components: {
    Headernav,
    lesson,
    checkout,
  },
  data() {
    return {
      lessons : [
        /*{topic: "maths", location: "heroku", price:23},
        {topic: "engo", location: "heroku2", price:10},
        {topic: "kiswahili", location: "heroku3", price:43}*/
      ],
      lessonscart: [
        /*{topic: "phyc", location: "heroku", price:23},
        {topic: "scien", location: "heroku2", price:10},
        {topic: "hello", location: "heroku3", price:43}*/
      ],
      showLessons: true,
    }
  },
  methods: {
    handleObject(lesson) {
      this.lessonscart.push(lesson)
    },
    showCheck() {
      this.showLessons = false;
    },
    showLesson() {
      this.showLessons = true;
    },
    removeObject(lessonout) {
      this.lessonscart = this.lessonscart.filter((lesson) => {
          return lesson.topic !== lessonout.topic || lesson.location !== lessonout.location || lesson.price !== lessonout.price;
      });
    },
    async getLessons() {
        try {
          const response = await fetch('https://assignment-class3.herokuapp.com/lessons');
          const lessons = await response.json();
          this.lessons = lessons;
        } catch (error) {
          console.error(error);
        }
    },
  },
  created() {
    this.getLessons()
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
