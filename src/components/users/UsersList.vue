<template>
  <button @click="doSth">Button</button>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Molestiae omnis fugiat itaque consequuntur in repudiandae molestias corporis, porro ipsa, ea asperiores accusantium quas officiis incidunt ad modi maiores, ullam rem?Repudiandae nam corporis, eius necessitatibus perspiciatis expedita! Fugit maiores itaque minima? Iure ut aliquam corrupti reprehenderit quisquam aliquid hic molestiae suscipit laborum? Ea nisi at ratione modi, veritatis atque mollitia?</p>
  <ul>
    <user-item v-for="user in users" :key="user.id" :name="user.fullName" :role="user.role"></user-item>
  </ul>
</template>

<script>
import UserItem from './UserItem.vue';

export default {
  components: {
    UserItem,
  },
  inject: ['users'],
  methods: {
    doSth() {
      this.$router.push('/teams');
    }
  }
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 2rem auto;
  max-width: 20rem;
  padding: 0;
}
</style>