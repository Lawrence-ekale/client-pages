<template>
    <div id="app">
    <h2>Lessons</h2>
    <div v-for="lesson in lessons" :key="lesson.location" class="mylessons">
      <ul>
        <li >
          Topic: {{ lesson.topic }}
        </li>
        <li >
          Location: {{ lesson.location }}
        </li>
        <li >
          Price: {{ lesson.price }}
        </li>
      </ul>

      <button class="inside" @click="addToCart(lesson)"> 
        Add lesson to cart
     </button>
    </div>
    
   <!-- <div id="searchDiv">
      <p>Search: <input type="text" v-model="searchInput" v-on:input="searchLessons()"> </p>
      <p>{{searchInput}}</p>
    </div>-->

    <button @click="showCheckOut"> 
        cart
    </button>
</div>
</template>

<script>
    export default {
        name: 'lesson-page',
        props: {
            lessons: {
                type: Array,
                required: true
            }
        },
        methods: {
            addToCart(lesson) {
                this.$emit('object-sent', lesson);
            },
            showCheckOut() {
                this.$emit('showCheck-out',null);
            },
        },
    }
</script>

<style>
button {
    background-color: green;
    width: 120px;
    border: none;
    color: white;
    height:30px;
}
.inside {
    background-color: yellow;
    width: 120px;
    color: black;
    height:30px;
    margin-left: 20%;
}

.mylessons {
    background-color: aqua;
    text-align: left;
    margin-left: 40%;
    margin-right: 40%;
    margin-bottom: 20px;
    height: 120px;

}
</style>