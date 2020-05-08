<template>
    <DraggableResizable :class-name="`${$options.name} absolute m-10 flex flex-col`">
        <div :class="`${$options.name}__header flex text-white`">
            <img
            :class="`${$options.name}__appIcon`"
            src="https://via.placeholder.com/15">
            <div>Title</div>
            <div class="ml-auto">icons</div>
        </div>
        <div :class="`${$options.name}__content bg-white  p-10`">BBBBBBBBB</div>
    </DraggableResizable>
</template>

<script>
import DraggableResizable from 'vue-draggable-resizable'

export default {
    name: 'AppWindow',
    components: {
        DraggableResizable,
    },
}
</script>

<style lang="scss" scoped>
.AppWindow {
    $root: &;
    &__header {
        border-top-left-radius: 7px;
        border-top-right-radius: 7px;
        user-select: none;
    }
    &__content {
        border: rgb(101, 130, 245) solid 3px;
        border-top: none;
        #{$root}.active &{
            border: #292ddf solid 3px;
            border-top: none;
        }
        &--borderless {
            border: none !important;
        }
    }
    &__header {
        background: rgba(0, 0, 0, 0) linear-gradient(rgb(118, 151, 231) 0%, rgb(126, 158, 227) 3%, rgb(148, 175, 232) 6%, rgb(151, 180, 233) 8%, rgb(130, 165, 228) 14%, rgb(124, 159, 226) 17%, rgb(121, 150, 222) 25%, rgb(123, 153, 225) 56%, rgb(130, 169, 233) 81%, rgb(128, 165, 231) 89%, rgb(123, 150, 225) 94%, rgb(122, 147, 223) 97%, rgb(171, 186, 227) 100%) repeat scroll 0% 0%;
        #{$root}.active & {
            background: rgba(0, 0, 0, 0) linear-gradient(rgb(0, 88, 238) 0%, rgb(53, 147, 255) 4%, rgb(40, 142, 255) 6%, rgb(18, 125, 255) 8%, rgb(3, 111, 252) 10%, rgb(2, 98, 238) 14%, rgb(0, 87, 229) 20%, rgb(0, 84, 227) 24%, rgb(0, 85, 235) 56%, rgb(0, 91, 245) 66%, rgb(2, 106, 254) 76%, rgb(0, 98, 239) 86%, rgb(0, 82, 214) 92%, rgb(0, 64, 171) 94%, rgb(0, 48, 146) 100%) repeat scroll 0% 0%
        }
    }
    &__appIcon {
        height: 15px;
        width: 15px;
        margin: 3px;
    }
}
</style>
