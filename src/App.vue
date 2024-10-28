<script setup></script>

<template>
  <header>
    <div>
      <span id="logo">ITGAM BOX EXPERINCES</span>
      <img src="./assets/logo.png" alt="logo">
    </div>
  </header>

  <div class="content">
    <h1 class="title">Coffee Plans</h1>

    <h2 class="subtitle">
      Viajamos por el mundo para encontrar el mejor café de origen único para ti
    </h2>

    <div class="plans">
      <div class="plan">
        <div class="description">
          <span class="title">
            El Soltero
          </span>
        </div>
      </div>
      <div class="plan">
        <div class="description">
          <span class="title">
            El Curioso
          </span>
        </div>
      </div>
      <div class="plan">
        <div class="description">
          <span class="title">
            El adicto
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>