<template>
  <div id="app">
    <div class="container-proto">
      <router-link :to="{ name: 'home'}">
        <section class="hero-banner">
          <h1 class="hero-body has-text-white">Sähkösi</h1>
        </section>
      </router-link>
      <router-view></router-view>
    </div>

  </div>
</template>
