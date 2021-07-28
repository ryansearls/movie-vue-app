<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/about">About</router-link>
      |
      <router-link to="/signup">Signup</router-link>
      |
      <router-link to="/login">Login</router-link>
      |
      <router-link to="/logout">Logout</router-link>
      |
      <router-link to="/movies">Movies</router-link>
      |
      <router-link to="/movies/new">Create</router-link>
    </div>
    <router-view />
  </div>
</template>

<style>
body {
  background-image: url("./assets/blue-snow.png");
  font-family: Arial Black, Arial Bold, Gadget, sans-serif !important;
  text-align: left;
}
</style>
