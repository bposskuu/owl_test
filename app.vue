<template>
  <div>
    <NuxtPage />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Unbounded:wght@200..900&family=Onest:wght@100..900&display=swap');

* {
  margin: 0;
  padding: 0;
  outline: none;
  text-decoration: none;
  font-family: 'Onest', cursive;
  font-size: .0625vw;

  @media (max-width: 768px) {
    & {
      font-size: .1389vw;
    }
  }
}

body {
  background-color: #423F3FB2;
}

</style>