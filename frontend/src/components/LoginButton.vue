<template>
  <li class="nav-item" :class="{ dropdown: userStore.loggedIn }">
    <template v-if="userStore.loggedIn">
      <a
        class="nav-link dropdown-toggle"
        href="#"
        role="button"
        data-bs-toggle="dropdown"
        aria-expanded="false"
      >
        <img :alt="userStore.user.username!" :src="avatarURL" />
      </a>
      <ul class="dropdown-menu dropdown-menu-end">
        <li>
          <a class="dropdown-item" @click.prevent="doLogout">
            {{ t("logout") }}
          </a>
        </li>
      </ul>
    </template>
    <a v-else @click.prevent="doLogin()" href="#" class="btn btn-primary">
      {{ t("login") }}
    </a>
  </li>
</template>

<script setup lang="ts">
import { useI18n } from "vue-i18n";
import { useRoute, useRouter } from "vue-router";
import { login, logout, useAuth } from "../auth";
import { useUserStore } from "../stores/user";
import { generateLibravatarURL } from "../util";

const auth = useAuth();
const route = useRoute();
const userStore = useUserStore();
const router = useRouter();
const { t } = useI18n();

const avatarURL = generateLibravatarURL(userStore.email, 30, "retro");

const doLogin = () => login(auth, route.fullPath);

const doLogout = () => {
  logout();
  if (route.meta.auth) {
    router.push("/");
  }
};
</script>

<i18n lang="yaml">
en-US:
  login: "Login"
  logout: "Logout"
fr-FR:
  login: "Connexion"
  logout: "Déconnexion"
</i18n>
