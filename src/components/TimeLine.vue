<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const timelineItems = [
    {
        id: 1,
        title: "Cadastro Inteligente",
        description: "Sistema completo de registro de EPIs e colaboradores com informações personalizáveis."
    },
    {
        id: 2,
        title: "Gestão de Movimentação",
        description: "Controle preciso de retiradas e devoluções com histórico completo."
    },
    {
        id: 3,
        title: "Redução de Perdas",
        description: "Minimização drástica de erros operacionais e perdas de materiais através de rastreamento preciso e controle inteligente."
    },
    {
        id: 4,
        title: "Eficiência Operacional",
        description: "Economia significativa de tempo administrativo e aumento mensurável da produtividade das equipes."
    },
    {
        id: 5,
        title: "Transparência Total",
        description: "Melhoria radical na transparência dos processos e facilitação de auditorias internas e externas."
    },
];

const timelineRef = ref(null);
const progressHeight = ref('0%');
const itemRefs = ref([]);

const handleScroll = () => {
    if (!timelineRef.value) return;

    const container = timelineRef.value;
    const containerTop = container.offsetTop;
    const containerHeight = container.offsetHeight;
    const scrollY = window.scrollY;
    const screenHeight = window.innerHeight;

    const triggerPoint = scrollY + screenHeight / 2;
    const relativeScroll = triggerPoint - containerTop;

    let progress = (relativeScroll / containerHeight);
    progress = Math.max(0, Math.min(progress, 1));

    progressHeight.value = `${progress * 100}%`;
};

onMounted(() => {
    window.addEventListener('scroll', handleScroll);
    handleScroll();

    const observer = new IntersectionObserver(
        (entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('is-visible');
                }
            });
        },
        { threshold: 0.3 }
    );

    itemRefs.value.forEach((item) => {
        if (item) observer.observe(item);
    });
});

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll);
});
</script>

<template>
    <section class="py-24 bg-white overflow-hidden">
        <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">

            <div class="text-center mb-20">
                <h2 class="text-4xl md:text-5xl font-bold text-slate-900 font-sans">Nossa Solução</h2>
                <p class="mt-4 text-slate-500 tracking-[0.2em] uppercase text-sm">Evolução Contínua</p>
            </div>

            <div ref="timelineRef" class="relative pb-12">

                <div class="absolute left-1/2 transform -translate-x-1/2 h-full w-[3px] bg-gray-100 top-0 rounded-full">
                </div>

                <div class="absolute left-1/2 transform -translate-x-1/2 w-[3px] bg-green-600 top-0 transition-all duration-100 ease-linear rounded-full origin-top"
                    :style="{ height: progressHeight }"></div>

                <div class="relative z-10">
                    <div v-for="(item, i) in timelineItems" :key="item.id" ref="itemRefs"
                        class="timeline-item relative flex items-center mb-24 opacity-0 translate-y-12 transition-all duration-1000 ease-out"
                        :class="[
                            i % 2 === 0 ? 'justify-start' : 'flex-row-reverse justify-start'
                        ]">

                        <div class="hidden md:block w-5/12"></div>

                        <div class="w-2/12 flex justify-center relative">
                            <div
                                class="h-6 w-6 md:h-8 md:w-8 bg-white rounded-full flex items-center justify-center border-4 border-green-600 z-20 shadow-[0_0_0_8px_rgba(255,255,255,1)]">
                            </div>
                        </div>

                        <div class="w-full md:w-5/12 pl-2 pr-0 md:px-6"
                            :class="i % 2 === 0 ? 'text-left' : 'text-left md:text-right'">
                            <h3 class="text-2xl font-bold text-slate-900 mb-3 font-sans">
                                {{ item.title }}
                            </h3>
                            <p class="text-slate-600 leading-relaxed text-base">
                                {{ item.description }}
                            </p>
                        </div>

                    </div>
                </div>

            </div>
        </div>
    </section>
</template>

<style scoped>
.timeline-item.is-visible {
    opacity: 1;
    transform: translateY(0);
}
</style>