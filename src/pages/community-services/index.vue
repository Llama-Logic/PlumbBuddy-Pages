<template>
    <MenuToggleBreadcrumbs
        color="tertiary"
        :items="[{title: 'Community Services'}]"
    />
    <v-container>
        <SectionMenu
            :sections="sections"
        />
    </v-container>
</template>

<script setup>
    const sections = [
    {
            color: 'tertiary',
            icon: 'mdi-share',
            name: 'Redirect Hosting',
            image: 'detour.jpg',
            description: `We host redirect links, intended for creators to use in their Llama Logic mod manifests, to ensure that the manifests contain stable links.`,
            to: 'community-services/redirect-hosting',
        },
        {
            color: 'tertiary',
            icon: 'mdi-face-agent',
            name: 'Support Venues',
            image: 'support_representative.jpg',
            description: `When a player gets an error, or when they need help with a mod, or when they need help with anything game related, there’s a convenient button in PlumbBuddy that they can click and be guided through finding that help.`,
            to: 'community-services/support-venues',
        },
    ];
</script>
