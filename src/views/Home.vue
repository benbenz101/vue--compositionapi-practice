<template>
  <div class="home">
    <h1>Home</h1>
    <p ref="p">my name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">click me</button>
    <button @click="age++">Add age</button>
    <input type="text" v-model="name" />
    <br />
    <br />
    <h2>Refs</h2>
    <p>{{ bennyOne.names }} - {{ bennyOne.ages }}</p>
    <button @click="updateBennyOne">Update bennyone</button>
    <br />
    <br />
    <h2>Reactive</h2>
    <p>{{ bennyTwo.names }} - {{ bennyTwo.ages }}</p>
    <button @click="updateBennyTwo">Update bennytwo</button>
  </div>
</template>

<script>
import { ref, reactive } from "@vue/reactivity";
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

    //these data set are not reactive variables by default in the setup function
    //let name = "mario";
    //let age = 30;

    //we make them reactive by surrounding them with refs
    //we generally use refs in composition api
    //asides using refs to create reactive values, we can also use reactive
    //
    const name = ref("benson");
    const age = ref(30);

    const handleClick = () => {
      //console.log(p, p.value);
      //we can take the value and do any JS operation on it
      //p.value.classList.add("test");
      //p.value.textContent = "welcome Benny";

      name.value = "Chijioke";
      age.value = 25;
    };

    //always return anything you have in the setup to make them available in the template
    //If we don't return the p for example, it won't be associated with the p in the dorm element

    const bennyOne = ref({ names: "ceejay", ages: 20 });
    const updateBennyOne = () => {
      bennyOne.value.ages = 46;
    };

    //in reactive, we don't use dot value
    //we can't use primitive values inside reactive
    //Refs will also work better as opposed to external composition functions when compared to reactive
    
    const bennyTwo = reactive({ names: "ceejay", ages: 20 });
    const updateBennyTwo = () => {
      bennyTwo.ages = 46;
    };

    return {
      name,
      age,
      bennyOne,
      bennyTwo,
      handleClick,
      p,
      updateBennyOne,
      updateBennyTwo,
    };
  },
};
</script>
