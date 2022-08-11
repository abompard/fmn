<script setup lang="ts">
import { useI18n } from "vue-i18n";
import HelloWorld from "./HelloWorld.vue";
import LoginButton from "./LoginButton.vue";
import MainNavLink from "./MainNavLink.vue";

const { t } = useI18n();
</script>

<template>
  <header>
    <nav
      class="navbar navbar-expand-lg navbar-light masthead justify-content-between py-2"
    >
      <div class="container">
        <a class="navbar-brand" href="/"
          ><img
            src="@/assets/logo.png"
            alt="Fedora Account System logo"
            height="40"
        /></a>
        <ul class="navbar-nav fw-bold align-items-center">
          <MainNavLink to="/">{{ t("home") }}</MainNavLink>
          <MainNavLink to="/about">{{ t("about") }}</MainNavLink>
          <MainNavLink to="/rules">{{ t("rules") }}</MainNavLink>
          <MainNavLink to="/destinations">{{ t("destinations") }}</MainNavLink>
          <LoginButton />
        </ul>
      </div>
    </nav>

    <div class="bg-light border-bottom py-5">
      <div class="container">
        <HelloWorld msg="You did it!!!" />
      </div>
    </div>
  </header>
</template>

<i18n lang="yaml">
en-US:
  home: "Home"
  about: "About"
  rules: "Rules"
  destinations: "Destinations"
fr-FR:
  home: "Accueil"
  about: "À propos"
  rules: "Règles"
  destinations: "Destinations"
</i18n>
