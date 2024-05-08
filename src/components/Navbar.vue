<template>
  <nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Samuel Kubala</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
        aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <RouterLink to="/~xkubala/sivaStena/" class="nav-link">Galéria</RouterLink>
          </li>
          <li class="nav-item">
            <RouterLink to="/~xkubala/sivaStena/mapa" class="nav-link">Mapa Fotiek</RouterLink>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>