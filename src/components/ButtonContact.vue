<script setup>

</script>

<template>
    <button
        class="group relative w-48 h-14 overflow-hidden rounded-full bg-green-600 text-white shadow-lg transition-all duration-500 hover:bg-green-700 hover:shadow-xl cursor-pointer">
        <div class="relative h-full w-full flex items-center justify-center">

            <span
                class="absolute transform transition-all duration-500 ease-out group-hover:-translate-x-10 group-hover:opacity-0 font-bold text-xl">
                Contatos
            </span>

            <span
                class="absolute transform translate-x-10 opacity-0 transition-all duration-500 ease-out group-hover:translate-x-0 group-hover:opacity-100 flex items-center justify-center">
                <svg class="h-7 w-7 rotate-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"
                    stroke-linecap="round" stroke-linejoin="round">
                    <line x1="22" y1="2" x2="11" y2="13"></line>
                    <polygon points="22 2 15 22 11 13 2 9 22 2"></polygon>
                </svg>
            </span>

        </div>
    </button>
</template>