<template>
  <main>
    <user-list :users="activeUsers" @list-projects="selectUser"></user-list>
    <projects-list :user="selectedUser"></projects-list>
    <form @submit.prevent="submit">
    <rating v-model="rating"></rating>
    <button></button>
      </form>
  </main>
</template>

<script>
import USER_DATA from './dummy-data.js';

import UserList from './components/users/UserList.vue';
import ProjectsList from './components/projects/ProjectsList.vue';
import Rating from './components/form/Rating.vue';

export default {
  components: {
    UserList,
    ProjectsList,
    Rating
  },
  data() {
    return {
      selectedUser: null,
      activeUsers: USER_DATA,
      rating: null
    };
  },
  methods: {
    selectUser(uid) {
      this.selectedUser = this.activeUsers.find((usr) => usr.id === uid);
    },
    submit() {
      console.log('called');
      console.log(this.rating);
    }
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
html {
  font-family: sans-serif;
}
body {
  margin: 0;
}

main {
  display: flex;
  justify-content: space-around;
}

button {
  font: inherit;
  border: 1px solid #00006b;
  background-color: transparent;
  color: #00006b;
  padding: 0.5rem 1.5rem;
  cursor: pointer;
  margin: 0.5rem 0.5rem 0.5rem 0;
}
button:hover,
button:active {
  background-color: #efefff;
}

button.selected {
  background-color: #00006b;
  color: white;
}
</style>