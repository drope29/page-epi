<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import ButtonContact from './ButtonContact.vue';

const lineWidth = ref('5%');

const handleScroll = () => {
    const scrollY = window.scrollY;
    const screenHeight = window.innerHeight;

    const targetScroll = screenHeight * 0.5;

    const progress = Math.min(scrollY / targetScroll, 1);

    const currentWidth = 5 + (progress * 95);

    lineWidth.value = `${currentWidth}%`;
};

onMounted(() => {
    window.addEventListener('scroll', handleScroll);
    handleScroll();
});

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll);
});
</script>

<template>
    <main class="relative w-full bg-white overflow-x-hidden">

        <div
            class="fixed top-0 inset-x-0 h-[600px] bg-[radial-gradient(ellipse_at_top,_var(--tw-gradient-stops))] from-gray-100 via-transparent to-transparent opacity-70 -z-20 pointer-events-none">
        </div>
        <div
            class="fixed left-1/2 top-[40%] -translate-x-1/2 -translate-y-1/2 w-[600px] h-[400px] bg-green-500/10 blur-[120px] rounded-full -z-10 pointer-events-none">
        </div>

        <section class="relative h-screen flex flex-col items-center justify-center text-center px-4 w-full">

            <h1
                class="font-surgena text-slate-900 text-7xl md:text-8xl lg:text-9xl tracking-tight drop-shadow-sm leading-none pb-2">
                Epi Manager
            </h1>

            <p class="mt-2 text-slate-500 font-sans text-sm md:text-base uppercase tracking-[0.4em] font-medium">
                Gerenciando Suas Entregas
            </p>

            <div class="h-[3px] bg-green-600 rounded-full mt-8 transition-all duration-75 ease-linear min-w-[50px]"
                :style="{ width: lineWidth }"></div>

            <div class="mt-12">
                <ButtonContact />
            </div>
        </section>

</main></template>