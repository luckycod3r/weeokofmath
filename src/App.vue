<template>
  <nav>
    <span>Неделя математики в МАОУ СОШ 22 г. Южно-Сахалинск</span>
  </nav>
  <router-view/>
</template>

<style>
.container{
  max-width: 90vw;
  margin: 0 auto;
}
input{
  padding: 5px;
  border-radius: 10px;
  outline: none;
  border: none;
  font-size: 1.5em;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
button{
  border-radius: 5px;
  background: orangered;
  color: #fff;
  padding: 5px 10px;
  margin-top: 10px;
  border: none;
  font-size: 1.3em;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
  color: #e4e4e4;
}
body{
  background: #e69040;
}
nav {
  padding: 15px;
  border-radius: 10px;
  font-weight: bold;
  text-transform: uppercase;
  color: #111;
  background: #fff;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
