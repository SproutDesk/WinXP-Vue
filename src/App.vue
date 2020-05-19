<template>
    <div class="h-screen flex flex-col">
        <div class="desktop h-full w-full overflow-hidden relative bg-cover">
            <AppWindow
            title="Test Title 1">
                AAAAAAAAAAAA
            </AppWindow>
        </div>
        <SystemTaskbar />
    </div>
</template>

<script>
import SystemTaskbar from '@/components/SystemTaskbar.vue'
import AppWindow from '@/components/AppWindow.vue'

export default {
    name: 'App',
    components: {
        SystemTaskbar,
        AppWindow,
    },
}
</script>

<style scoped>
.desktop {
    background-image: url('assets/desktop_bg.jpg');
}

</style>
