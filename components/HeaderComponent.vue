<template>
  <header>
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
      <div class="container-fluid">
        <NuxtLink class="navbar-brand" to="/">LiteraLib</NuxtLink>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div id="navbarNavAltMarkup" class="collapse navbar-collapse">
          <div class="navbar-nav">
            <NuxtLink class="nav-link active" aria-current="page" to="/">Home</NuxtLink>
            <NuxtLink class="nav-link" to="/about">about</NuxtLink>
            <NuxtLink class="nav-link" to="/contact">Contact</NuxtLink>
            <!-- <router-link class="nav-link disabled" aria-disabled="true">Disabled</router-link> -->
          </div>
        </div>
      </div>
    </nav>
  </header>
</template>
