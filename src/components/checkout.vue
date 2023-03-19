<template>
    <div id="app">
    <h2>Shopping Cart</h2>
    <div v-for="(lesson,index ) in lessonscart" :key="index" class="mylessons">
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

      <button class="insidecart" @click="removeFromCart(lesson)"> 
        Remove lesson from cart
     </button>
    </div>
    

    <button @click="showCheckOut"> 
        cart
    </button>
</div>
</template>

<script>
    export default {
        name: 'checkout-page',
        props: {
            lessonscart: {
                type: Array,
                required: true
            }
        },
        methods: {
            showCheckOut() {
                this.$emit('showCheck-out',null);
            },
            removeFromCart(lesson) {
                this.$emit('object-sent', lesson);
            },
        }
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
.insidecart {
    background-color: red;
    width: 125px;
    color: white;
    height:40px;
    margin-left: 20%;
}

.mylessons {
    background-color: aqua;
    text-align: left;
    margin-left: 40%;
    margin-right: 40%;
    margin-bottom: 20px;
    height: 150px;

}
</style>