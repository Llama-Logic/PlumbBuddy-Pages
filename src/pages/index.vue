<template>
    <MenuToggleBreadcrumbs />
    <v-carousel
        cycle
        :height="`${carouselHeight}px`"
    >
        <v-carousel-item
            v-for="carouselItem in carouselItems"
            :src="carouselItem.background"
            cover
        >
            <div
                class="w-100 h-100 px-4 d-flex justify-center align-end"
            >
                <v-card
                    class="mb-16 mx-16"
                    :color="carouselItem.color"
                    elevation="20"
                    :title="carouselItem.title"
                >
                    <v-card-text>
                        <p v-html="carouselItem.text"></p>
                    </v-card-text>
                    <v-card-actions>
                        <v-btn
                            :prepend-icon="carouselItem.buttonIcon"
                            :text="carouselItem.buttonText"
                            @click="handleCarouselItemButtonClicked(carouselItem)"
                        />
                    </v-card-actions>
                </v-card>
            </div>
        </v-carousel-item>
    </v-carousel>
    <div
        v-if="globalState.currentReleaseVersion.value && globalState.currentReleaseLifecycleStageName.value"
        class="ma-4 d-flex ga-4"
    >
        <v-alert
            density="compact"
            icon="mdi-application"
            variant="tonal"
        >
            <span v-if="!xs">Current version: </span>
            <strong>{{ globalState.currentReleaseVersion.value }}</strong>
        </v-alert>
        <v-alert
            :color="globalState.currentReleaseLifecycleStageThemeColor.value"
            density="compact"
            :icon="globalState.currentReleaseLifecycleStageIcon.value"
            variant="tonal"
        >
            <span v-if="!xs">Lifecycle stage: </span>
            <strong>{{ globalState.currentReleaseLifecycleStageName.value }}</strong>
        </v-alert>
    </div>
</template>

<script setup>
    import { ref, computed, onMounted, onBeforeUnmount } from 'vue';
    import { useRouter } from 'vue-router';
    import { useDisplay } from 'vuetify';
    import { useGlobalState } from '@/stores/global-state';

    const router = useRouter();
    const globalState = useGlobalState();

    const height = ref(window.innerHeight);
    const { xs } = useDisplay();

    const updateHeight = () => {
        height.value = window.innerHeight;
    }

    onMounted(async () => {
        await globalState.loadReleases();
        window.addEventListener('resize', updateHeight);
    });

    onBeforeUnmount(() => {
        window.removeEventListener('resize', updateHeight);
    });

    const carouselHeight = computed(() => height.value - 175);
    const carouselItems = [
        {
            background: '/img/yachtz.jpg',
            color: 'success',
            title: 'PlumbBuddy 1.4 is Here!',
            text: `Lumpinou has lent us her very good boi to help make sure your mods are up to date!`,
            buttonIcon: 'mdi-download',
            buttonText: 'Download Now!',
            buttonPath: '/download',
        },
        {
            background: '/img/mod_health_scans.jpg',
            color: 'primary',
            title: 'Mod Health',
            text: `Mod Health helps you by <strong>Ensuring Optimal Game Options</strong>, <strong>Finding Problems in Your Mods Folder</strong>, <strong>Pointing Out Essentials You're Missing</strong>, and <strong>Performing Analysis of Your Game &amp; Mods</strong>.`,
            buttonIcon: 'mdi-bottle-tonic-plus',
            buttonText: 'Learn More',
            buttonPath: '/features/mod-health',
        },
        {
            background: '/img/arcane_vault.jpg',
            color: 'secondary',
            title: 'Archivist',
            text: `Archivist is ready to help you never lose a save again.`,
            buttonIcon: 'mdi-archive-clock',
            buttonText: 'Learn More',
            buttonPath: '/features/archivist',
        },
        {
            background: '/img/santorini.jpg',
            color: 'secondary',
            title: 'Parlay',
            text: `Is there a mod that you love but it's just not available in your language? Parlay is there for you.`,
            buttonIcon: 'mdi-translate-variant',
            buttonText: 'Learn More',
            buttonPath: '/features/parlay',
        },
        {
            background: '/img/construction_workers.jpg',
            color: 'tertiary',
            title: 'Manifest Editor',
            text: `<em>Finally</em>, Creators can make mods self-describing: identifying <strong>who</strong> made them, <strong>where</strong> they came from, and <strong>what</strong> they need.`,
            buttonIcon: 'mdi-tag-edit',
            buttonText: 'Learn More',
            buttonPath: '/features/manifest-editor',
        },
    ];

    function handleCarouselItemButtonClicked(carouselItem) {
        if (carouselItem.buttonHref) {
            window.open(carouselItem.buttonHref, '_blank');
            return;
        }
        router.push(carouselItem.buttonPath);
    }
</script>