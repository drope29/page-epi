<script setup>
import ButtonContact from './ButtonContact.vue';

</script>

<template>
    <nav class="bg-sky-900 h-[130px] relative flex items-center px-12">

        <div class="flex-1"></div>

        <div class="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2">
            <img src="/images/logoepimanager.png" alt="Logo Epi Manager" class="h-[300px] w-auto object-contain">
        </div>

        <div class="flex-1 flex justify-end">
            <ButtonContact />
        </div>

    </nav>
</template>