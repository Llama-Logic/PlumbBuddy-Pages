<template>
    <MenuToggleBreadcrumbs
        color="primary"
        :items="[{title: 'PlumbBuddy Setup Guide for Creators'}]"
    />
    <v-container>
        <iframe src="https://www.youtube.com/embed/5qze0OZn1Rw?si=EB9Zh3d7VOFGiVqQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen style="width: 100%; aspect-ratio: 16/9;"></iframe>
        <p style="font-size:1.2em;">
            <center>How to get PlumbBuddy up and running</center>
        </p>
    </v-container>
    <ContentMenu
        :contents="contents"
    />
</template>

<script setup>
    const contents = [
        {
            color: 'primary',
            icon: 'mdi-download-circle',
            name: 'Downloading PlumbBuddy',
            image: 'DownloadArrowGreen.jpeg',
            description: `How to download and install PlumbBuddy.`,
            to: 'enthusiast-download',
        },
        {
            color: 'secondary',
            icon: 'mdi-clipboard-play',
            name: 'PlumbBuddy First Time Setup',
            image: 'ToggleGreen.png',
            description: `How to get it all up and running.`,
            to: 'creator-onboarding',
        },
        {
            color: 'success',
            icon: 'mdi-menu',
            name: 'User Interface Overview',
            image: 'checklist.png',
            description: `What are you looking at?`,
            to: 'creator-ui',
        },
        {
            color: 'info',
            icon: 'mdi-lifebuoy',
            name: 'The Features',
            image: 'helping-hand.jpeg',
            description: `What can PlumbBuddy do for you?`,
            to: 'creator-features',
        },
        {
            color: 'success',
            icon: 'mdi-radar',
            name: 'Mod Health',
            image: 'nurse-health.jpeg',
            description: `What the Scans Tell You`,
            to: 'creator-mod-health',
        },
        {
            color: 'success',
            icon: 'mdi-radar',
            name: 'Mod Hound',
            image: 'ModHoundLogoSm.png',
            description: `A Different Way to Check Your Mods and Have Players Check *Their* Mods`,
            to: 'creator-mod-hound',
        },
        {
            color: 'success',
            icon: 'mdi-radar',
            name: 'Archivist',
            image: 'treasure-7879866_640.png',
            description: `Saving Your Saves`,
            to: 'archivist',
        },
        {
            color: 'success',
            icon: 'mdi-radar',
            name: 'Parlay',
            image: 'chat-balloons.jpeg',
            description: `Your Mods in Your Language`,
            to: 'creator-parlay',
        },
    ];
</script>