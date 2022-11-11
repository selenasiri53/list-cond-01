<template>
  <header>
    <h1>Vue Course Goals</h1>
  </header>
  <section id="app">
    <h2>My course goals</h2>
    <input type="text" v-model="enteredGoalValue" />

    <button @click="addGoal">Add Goal</button>

    <p v-if="goals.length === 0">
      No goals have been added yet - please start adding some!
    </p>
    <ul v-else>
      <li
        v-for="(goal, index) in goals"
        :key="index"
        @click="removeGoal(index)"
      >
        {{ goal }} - {{ index }}
        <!-- pastes the goal and index, i.e. goalName - 0, goalName - 1 -->
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  name: 'App',
  components: {},
  data() {
    return {
      enteredGoalValue: '',
      goals: [],
    };
  },
  methods: {
    addGoal() {
      this.goals.push(this.enteredGoalValue);
      this.enteredGoalValue = '';
    },
    removeGoal(idx) {
      this.goals.splice(idx, 1);
      // splice - ?
    },
  },
};
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
