<template>
  <header>
    <h1><img src="../assets/kong.jpeg" alt="logo-alura" /></h1>
    <h3>Kong Tarefas</h3>
  </header>
</template>

<script>
export default {
  name: "BarraLateral",
};
</script>


<style scoped>
* {
  padding: 1rem;
}
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
}

img {
  width: 150px;
  height: 150px;
  margin: auto;
  display: flex;
  border-radius: 50%;
  transition: all .4s ease-in-out;
}

img:hover {
  box-shadow: 0 1px 10px yellow;
  cursor: pointer;
}

h3 {
  margin-top: 1rem;
  text-align: center;
  color: lightgoldenrodyellow;
  font-family: Arial, Helvetica, sans-serif;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>