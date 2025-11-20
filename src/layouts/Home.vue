<script lang="ts" setup>
import { Icon } from "@iconify/vue";

const openStartMenu = () => {
  console.log("Start Menu Opened");
};
</script>
<template>
  <div class="reks-screen flex flex-col w-full h-screen">
    <div class="reks-desktop w-full grow overflow-hidden">
      <!-- 屏幕 高1032px -->
      <!-- TODO 设置背景壁纸，图标，窗口等 -->
      <div class="desktop-bg w-full h-full border border-black/10">
        <!-- <img class="bg-img w-full h-full object-cover" src="/blue.png" alt="blue"> -->
      </div>
    </div>
    <div class="reks-misson-bar w-full h-10 relative">
      <!-- 开始按钮 -->
      <button
        @click="openStartMenu"
        class="start flex justify-center items-center w-[50px] overflow-hidden"
      >
        <Icon
          class="w-full h-full start-icon"
          icon="streamline-logos:microsoft-windows-logo-1-solid"
        />
        <!-- <img src="/vista.png" class="w-full h-full start-icon" alt="vista"> -->
      </button>

      <div class="search-bar"></div>
      <!-- TODO 显示左下角label,search-bar,图标，已经时间，声音等图案 -->
    </div>
  </div>
</template>
<style lang="scss" scoped>
.start {
  border-radius: 50%;
  aspect-ratio: 1/1;
  overflow: visible;
  position: absolute;
  bottom: 2px;
  left: 1rem;
  /* https://grabient.com/HQJgnArANKk+1gGYIBYZKQdg0kMA2ARiJggA5yywCpVgwskojhyQqlgtig?style=linearGradient&steps=7&angle=90 */
  background: linear-gradient(
    90deg,
    rgba(164, 116, 81, 1) 0%,
    rgba(156, 152, 129, 1) 16.667%,
    rgba(115, 160, 157, 1) 33.333%,
    rgba(59, 137, 154, 1) 50%,
    rgba(9, 91, 121, 1) 66.667%,
    rgba(0, 40, 71, 1) 83.333%,
    rgba(0, 1, 22, 1) 100%
  );
  backdrop-filter: blur(40px);
  box-shadow: 0 8px 18px rgba(0, 0, 0, 0.25),
    /* 投影*/ inset 0 1px 0 rgba(255, 255, 255, 0.8);
  /* 内高光 */
  .start-icon {
    padding: 10px;
    color: #ffffffea;
    &:hover {
      color: #ffffff;
    }
    filter: drop-shadow(0 4.5px 0.5px rgba(0, 0, 0, 0.18));
  }
}

.reks-misson-bar {
  background: #000000 url("taskbar.png") repeat-x scroll 0 0;
}
</style>
