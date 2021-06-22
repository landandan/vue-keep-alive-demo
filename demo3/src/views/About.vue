<template>
  <div class="about">
    <h1>This is an about page</h1>
    <router-link :to="{ name: 'Home' }">Home</router-link>
    <router-link :to="{ name: 'List' }">List</router-link>
  </div>
</template>
