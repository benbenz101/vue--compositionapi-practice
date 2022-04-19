<template>
  <div class="home">
    <h1>Home</h1>
    <p ref="p">my name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">click me</button>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
export default {
  name: "Home",
  //the setup will run before any of the lifecycle hooks
  //the compositio api allows you to put all the data, lifecycle hooks, computed and components and methods in one setup function
  //we can run any javascript in the setup function
  setup() {
    // console.log("setup");

    //this alone isnt reactive like the options api
    //if the values changes here, it won't reflect on the template
    //we can use template ref to store references in our template  normallyin vue, but in composition-api, it is used to make data elements reactive
    //the 'this' keyword isn't available in the setup function
    //in composition api, we import the part that we need from vue
    //

    const p = ref(null);

    let name = "mario";
    let age = 30;

    const handleClick = () => {
      console.log(p, p.value);
      //we can take the value and do any JS operation on it
      p.value.classList.add("test");
      p.value.textContent = "welcome Benny";
    };

    //always return anything you have in the setup to make them available in the template
    //If we don't return the p for example, it won't be associated with the p in the dorm element
    //

    return { name, age, handleClick, p };
  },
};
</script>
