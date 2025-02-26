<template>
    <div class="page-loader" v-if="!isloaded">
        <svg width="400" height="300" viewBox="5 0 80 60" class="waveImg">
            <path
                class="wave"
                fill="none"
                stroke="#ff0000"
                stroke-width="3"
                stroke-linecap="round"
                d="M 0 37.5 c 7.684299348848887 0 7.172012725592294 -15 15 -15 s 7.172012725592294 15 15 15 s 7.172012725592294 -15 15 -15 s 7.172012725592294 15 15 15 s 7.172012725592294 -15 15 -15 s 7.172012725592294 15 15 15 s 7.172012725592294 -15 15 -15 s 7.172012725592294 15 15 15 s 7.172012725592294 -15 15 -15 s 7.172012725592294 15 15 15 s 7.172012725592294 -15 15 -15 s 7.172012725592294 15 15 15 s 7.172012725592294 -15 15 -15 s 7.172012725592294 15 15 15 s 7.172012725592294 -15 15 -15"
            />
        </svg>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isloaded = ref(false)

onMounted(() => {
    setTimeout(() => {
        if (document.readyState === 'complete') {
            isloaded.value = true
        }
    }, 3000)
})
</script>

<style lang="scss" scoped>
// -----------------------------------------------------
.page-loader {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: #0e1212;
    z-index: 999;
}

// -----------------------------------------------------
// body {
//   display: flex;
//   justify-content: center;
//   align-items: center;
//   height: 100vh;
//   width: 100vw;
//   margin: 0;
//   background: #282937;
// }

.waveBtn {
    background: transparent;
    height: 22px;
    width: 55px;
    border-radius: 9999rem;
    border: 1px solid var(--purple);
    position: relative;
    overflow: hidden;
    transform: scale(12);
}

.waveImg {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.wave {
    animation: moveTheWave 3400ms linear infinite;
    stroke-dasharray: 0 16 101 16;
}

@keyframes moveTheWave {
    0% {
        stroke-dashoffset: -3;
        transform: translate3d(0, 0, 0);
    }

    100% {
        stroke-dashoffset: -138;
        transform: translate3d(-90px, 0, 0);
    }
}
</style>
