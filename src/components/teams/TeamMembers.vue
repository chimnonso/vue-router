<template>
  <section>
    <h2>{{ teamName }}</h2>
    <ul>
      <user-item
        v-for="member in members"
        :key="member.id"
        :name="member.fullName"
        :role="member.role"
      ></user-item>
    </ul>
    <router-link to="/teams/t2">go to team 2</router-link>
  </section>
</template>

<script>
import UserItem from '../users/UserItem.vue';

export default {
  props: ['teamId'],
  inject: ['teams', 'users'],
  components: {
    UserItem
  },
  data() {
    return {
      // users: '',
      members: '',
      teamName: ''
    };
  },

  methods: {
    loadTeamMeambers(teamId) {
      // const teamId = route.params.teamId;
      console.log(this.users);
      const selectedTeam = this.teams.find( team => teamId === team.id);
      const members = selectedTeam.members;
      const selectedMembers = [];
      for (const member of members) {
        // console.log(members[member]);
        const selectedUser = this.users.find(user => user.id === member);
        selectedMembers.push(selectedUser);
      }
      this.members = selectedMembers;
      this.teamName = selectedTeam.name;
    }
  },

  created() {
    this.loadTeamMeambers(this.teamId);
  },
  watch: {
    // $route(newRoute) {
    //   if (newRoute.params.teamId) {
    //     this.loadTeamMeambers(newRoute);
    //   }
    // }
    teamId(newId) {
      this.loadTeamMeambers(newId);
    }
  }
};
</script>

<style scoped>
section {
  margin: 2rem auto;
  max-width: 40rem;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  border-radius: 12px;
}

h2 {
  margin: 0.5rem 0;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>