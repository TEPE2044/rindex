<script lang="ts" setup>
import { Icon } from "@iconify/vue";
import { ref } from "vue";

const appList = [
    { icon: 'logos:microsoft-edge', name: 'Edge' },
    { icon: 'mdi:github', name: 'Github' }
]

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
        <div class="reks-desktop w-full flex-1 overflow-hidden">
            <!-- 屏幕 高1032px -->


            <!-- TODO 设置背景壁纸，图标，窗口等 -->
            <div class="desktop-bg w-full h-full border border-black/10">
                <img class="bg-img w-full h-full object-cover" src="/blue.png" alt="blue">
            </div>
        </div>
        <Transition name="fade">
            <div class="start-menu box absolute border border-black w-[400px] h-[500px] flex" v-show="isMenuOpen">
                <div class="left-part w-[200px] flex flex-col justify-center items-center box-border">
                    <!-- 应用列表（容器），内部项使用 v-for -->
                    <div class="menu-list mt-2 ml-4 p-1 w-full overflow-auto flex-1 bg-white rounded box-border">
                        <div class="menu-card w-full flex items-center gap-3 pl-2 pr-2 py-2 hover:bg-amber-100"
                            v-for="app in appList" :key="app.name">
                            <Icon :icon="app.icon" width="35" height="35" style="color: #194317" />
                            <div class="name">{{ app.name }}</div>
                        </div>
                    </div>

                    <!-- 底部搜索，和 menu-list 等宽 -->
                    <div class="search-bar mb-4 ml-4 w-full box-border">
                        <input class="bg-white rounded w-full h-7 px-2" type="search" placeholder="Search" />
                    </div>
                </div>

                <!-- 右侧占位（暂不处理） -->
                <div class="right-part flex-1"></div>
             </div>
        </Transition>
        <div class="reks-misson-bar w-full h-10 relative">
            <!-- 开始按钮 -->
            <button title="开始" @click="openStartMenu"
                class="start flex justify-center items-center w-[45px] overflow-hidden">
                <Icon class="w-full h-full start-icon" icon="streamline-logos:microsoft-windows-logo-1-solid" />
                <!-- 备选vista官方图标 <img src="/vista.png" class="w-full h-full start-icon" alt="vista"> -->
            </button>

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
    left: 0.5rem;
    /* https://grabient.com/HQJgnArANKk+1gGYIBYZKQdg0kMA2ARiJggA5yywCpVgwskojhyQqlgtig?style=linearGradient&steps=7&angle=90 */
    background: linear-gradient(90deg,
            rgba(164, 116, 81, 1) 0%,
            rgba(156, 152, 129, 1) 16.667%,
            rgba(115, 160, 157, 1) 33.333%,
            rgba(59, 137, 154, 1) 50%,
            rgba(9, 91, 121, 1) 66.667%,
            rgba(0, 40, 71, 1) 83.333%,
            rgba(0, 1, 22, 1) 100%);

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

.start-menu {
    background: #0f0f0fb0;
    box-shadow: #000 4px 5px 8px;
    border-radius: 5px;
    bottom: 35px;

    /* 左侧面板固定宽度，子元素使用 w-full + box-border 保持等宽 */
    .left-part {
        width: 200px;
        box-sizing: border-box;
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
        padding: 0;
        height: 100%;
    }

    .menu-list {
        flex: 1 1 auto;
        overflow: auto;
    }

    .menu-card {
        cursor: pointer;
        border-radius: 6px;
        display: flex;
        align-items: center;
    }

    .search-bar {
        flex: 0 0 auto;
    }
}

.reks-misson-bar {
    background: #000000 url("taskbar.png") repeat-x scroll 0 0;
}

// 过渡效果
.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.3s;
}

// 开始和结束状态
.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}
</style>
