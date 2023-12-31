<script setup lang="ts">
import { useI18n } from "vue-i18n";
import router from "src/router";
import { onMounted, ref } from "vue";
// import { Cookies } from "quasar";

const leftDrawer = ref<boolean>(true);

let { locale, t } = useI18n();

onMounted(() => {});

// Watch browser or browser page is close
window.addEventListener("beforeunload", () => {}, false);

function menuItems() {
  return [
    {
      icon: "mdi-home",
      text: t("startPage"),
      name: "startPage",
      route: "/",
      disabled: false,
      separator: false,
    },
  ];
}

function toggleLanguage() {
  locale.value = locale.value == "hu" ? "en" : "hu";
}
</script>

<template>
  <div class="q-pa-md">
    <q-layout view="hHh Lpr fFf">
      <q-header style="background-color: #1f4987;" class="text-white text-left" elevated reveal>
        <q-toolbar>
          <q-btn
            dense
            flat
            icon="mdi-menu"
            round
            @click="leftDrawer = !leftDrawer"
          />
          <q-toolbar-title
            class="my-title"
            style="cursor: pointer"
            @click="router.push({ path: '/' })"
          >
            Tibor Blascsok Resume
          </q-toolbar-title>
          <q-btn flat icon="mdi-comment-text-multiple" @click="toggleLanguage">
            <q-badge color="red" floating :label="locale" />
          </q-btn>
          <q-btn flat icon="mdi-theme-light-dark" @click="$q.dark.toggle" />
        </q-toolbar>
      </q-header>

      <q-drawer
        v-model="leftDrawer"
        bordered
        :breakpoint="500"
        :class="$q.dark.isActive ? 'bg-grey-9' : 'bg-grey-3'"
        show-if-above
        :width="200"
      >
        <q-scroll-area class="fit">
          <!-- routes: -->
          <q-list>
            <template v-for="(menuItem, index) in menuItems()" :key="index">
              <q-item
                clickable
                :disable="menuItem.disabled"
                :to="menuItem.route"
              >
                <q-item-section avatar>
                  <q-icon :name="menuItem.icon" />
                </q-item-section>
                <q-item-section>
                  {{ menuItem.text }}
                </q-item-section>
              </q-item>
              <q-separator v-if="menuItem.separator" :key="'sep' + index" />
            </template>
            <q-separator />
          </q-list>
        </q-scroll-area>
      </q-drawer>

      <q-footer style="background-color: #1f4987;" elevated reveal>
        <q-toolbar>
          <q-toolbar-title class="text-center my-title"> </q-toolbar-title>
        </q-toolbar>
      </q-footer>

      <q-page-container id="container">
        <router-view v-slot="{ Component }">
          <transition name="fade">
            <component :is="Component" />
          </transition>
        </router-view>
      </q-page-container>
    </q-layout>
  </div>
</template>

<style lang="scss">
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.my-title {
  font-size: 10px;
  @media (min-width: 400px) {
    font-size: calc(10px + 0.5vw);
  }
  @media (min-width: 800px) {
    font-size: calc(14px + 0.5vw);
  }
  @media (min-width: 1200px) {
    font-size: calc(18px + 0.5vw);
  }
}
</style>
