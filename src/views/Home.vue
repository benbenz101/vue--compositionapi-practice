<template>
  <div class="home">
    <h1>Home</h1>
    <p>my name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick" >click me</button>
  </div>
</template>

<script>
export default {
  name: "Home",
  //the setup will run before any of the lifecycle hooks
  //the compositio api allows you to put all the data, lifecycle hooks, computed and components and methods in one setup function
  //we can run any javascript in the setup function
  setup() {
    // console.log("setup");

    //this alone isnt reactive like the options api
    //if the values changes here, it won't reflect on the template
    let name = "mario";
    let age = 30;

    const handleClick = () => {
      console.log("you clicked me");
    };

    //always return anything you have in the setup to make them available in the template

    return { name, age, handleClick };
  },
};
</script>
