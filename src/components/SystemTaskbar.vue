<template>
    <div :class="`${$options.name} w-full flex text-white font-tahoma`">
        <div :class="`${$options.name}__start`">
            <img
            src="@/assets/start.png"
            alt="Start">
        </div>
        <div class="flex overflow-hidden py-1 text-xs">Active Windows</div>
        <div :class="`${$options.name}__tray flex ml-auto max-w-xs overflow-hidden py-2 justify-between`">
            <div class="mx-2">Tray Items</div>
            <div class="mx-2">{{ time }}</div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SystemTaskbar',
    data() {
        return {
            time: this.getTime(),
        }
    },
    mounted() {
        setInterval(() => { this.time = this.getTime() }, 5000)
    },
    methods: {
        getTime() {
            const date = new Date()
            let hour = date.getHours()
            if (hour < 10) {
                hour = `0${hour}`
            }
            let minute = date.getMinutes()
            if (minute < 10) {
                minute = `0${minute}`
            }
            return `${hour}:${minute}`
        },
    },
}
</script>

<style lang="scss" scoped>
.SystemTaskbar {
    $root: &;
    $height: 30px;
    height: $height;
    background: rgba(0, 0, 0, 0) linear-gradient(rgb(31, 47, 134) 0px, rgb(49, 101, 196) 3%, rgb(54, 130, 229) 6%, rgb(68, 144, 230) 10%, rgb(56, 131, 229) 12%, rgb(43, 113, 224) 15%, rgb(38, 99, 218) 18%, rgb(35, 91, 214) 20%, rgb(34, 88, 213) 23%, rgb(33, 87, 214) 38%, rgb(36, 93, 219) 54%, rgb(37, 98, 223) 86%, rgb(36, 95, 220) 89%, rgb(33, 88, 212) 92%, rgb(29, 78, 192) 95%, rgb(25, 65, 165) 98%) repeat scroll 0% 0%;

    &__start {
        margin-right: 10px;
        & > img {
            height: $height;
            &:hover {
                filter: brightness(105%);
            }
        }
    }

    &__tray {
        background: rgba(0, 0, 0, 0) linear-gradient(rgb(12, 89, 185) 1%, rgb(19, 158, 233) 6%, rgb(24, 181, 242) 10%, rgb(19, 155, 235) 14%, rgb(18, 144, 232) 19%, rgb(13, 141, 234) 63%, rgb(13, 159, 241) 81%, rgb(15, 158, 237) 88%, rgb(17, 155, 233) 91%, rgb(19, 146, 226) 94%, rgb(19, 126, 215) 97%, rgb(9, 91, 201) 100%) repeat scroll 0% 0%;
        border-left: 1px solid rgb(16, 66, 175);
        font-size: 11px;
    }
}
</style>
