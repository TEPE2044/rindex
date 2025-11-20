<script lang="ts" setup>
import { Icon } from "@iconify/vue";
import { ref } from "vue";

const isMenuOpen = ref(false);
//TODO 完善打开逻辑
const openStartMenu = () => {
  try {
    isMenuOpen.value = !isMenuOpen.value;
  } catch (err) {
    console.error("Failed to open start menu:", err);
  }
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
        title="开始"
        @click="openStartMenu"
        class="start flex justify-center items-center w-[50px] overflow-hidden"
      >
        <Icon
          class="w-full h-full start-icon"
          icon="streamline-logos:microsoft-windows-logo-1-solid"
        />
        <!-- 备选vista官方图标 <img src="/vista.png" class="w-full h-full start-icon" alt="vista"> -->
      </button>
      <Transition name="fade">
        <div class="start-menu absolute bottom-10" v-show="isMenuOpen">
          <!-- TODO 开始菜单内容 -->
          开始菜单
        </div>
      </Transition>
      <div class="search-bar"></div>
      <!-- TODO 显示左下角label,search-bar,图标，已经时间，声音等图案 -->
    </div>
  </div>
</template>
<style lang="scss" scoped>
.start {
  transition: all 0.2s ease-in-out;
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
  &:hover {
    filter: brightness(1.05);
  }
  backdrop-filter: blur(50px);
  .start-icon {
    transition: all 0.2s ease-in-out;
    padding: 10px;
    color: #ffffffd5;
    &:hover {
      color: #ffffff;
      transform: scale(1.05);
    }
    filter: drop-shadow(0 4.5px 0.5px rgba(0, 0, 0, 0.18));
  }
}

.reks-misson-bar {
  background: #000000 url("taskbar.png") repeat-x scroll 0 0;
}
</style>
