<script setup lang="ts">
import "~/init";
import { dayNo, daySince, isDev } from "~/state";
import { colorblind } from "~/storage";
import { DAYS_PLAY_BACK } from "~/logic/constants";

const { height } = useWindowSize();

watchEffect(() => {
  document.documentElement.style.setProperty("--vh", `${height.value / 100}px`);
});
</script>

<template>
  <main
    font-sans
    text="center gray-700 dark:gray-300"
    select-none
    :class="{ colorblind }"
  >
    <NotTodayBanner v-if="dayNo < daySince" />
    <Navbar />
    <div p="4">
      <Play />
    </div>
  </main>
</template>
