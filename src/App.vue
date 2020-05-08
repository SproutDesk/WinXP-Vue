<template>
    <div class="h-screen flex flex-col">
        <div class="desktop h-full w-full overflow-hidden relative bg-cover">
            <div class="absolute bg-blue-500 m-10 Window has-border flex flex-col">
                <div class="Window__header row">Title</div>
                <div class="Window__content p-5">BBBBBBBBB</div>
            </div>
        </div>
        <Taskbar />
    </div>
</template>

<script>
import Taskbar from '@/components/Taskbar.vue'

export default {
    name: 'App',
    components: {
        Taskbar,
    },
}
</script>

<style scoped>
.desktop {
    background-image: url('assets/desktop_bg.jpg');
}
.Window {

}
.Window.has-border {
    border: #292ddf solid 2px;
    border-top: none;
    border-top-left-radius: 7px;
    border-top-right-radius: 7px;
}
.Window__header {
    background: rgba(0, 0, 0, 0) linear-gradient(rgb(0, 88, 238) 0%, rgb(53, 147, 255) 4%, rgb(40, 142, 255) 6%, rgb(18, 125, 255) 8%, rgb(3, 111, 252) 10%, rgb(2, 98, 238) 14%, rgb(0, 87, 229) 20%, rgb(0, 84, 227) 24%, rgb(0, 85, 235) 56%, rgb(0, 91, 245) 66%, rgb(2, 106, 254) 76%, rgb(0, 98, 239) 86%, rgb(0, 82, 214) 92%, rgb(0, 64, 171) 94%, rgb(0, 48, 146) 100%) repeat scroll 0% 0%;
}
</style>
