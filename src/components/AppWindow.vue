<template>
    <DraggableResizable
    :class-name="`
        ${$options.name}
        ${!hasBorder ? 'borderless' : ''}
        ${hasHeader ? ' has-header' : ''}
        flex flex-col
    `"
    :w="400"
    :h="200"
    :x="startX"
    :y="startY"
    :min-width="200"
    :min-height="200"
    :disable-user-select="false"
    :drag-cancel="`${$options.name}__content`"
    :draggable="true"
    :resizable="true">
        <div
        v-if="hasHeader"
        :class="`${$options.name}__header text-white w-full flex items-center`">
            <div :class="`${$options.name}__header_bg`" />
            <img
            v-if="headerIcon"
            class="w-5 h-5 absolute mx-2"
            :src="headerIcon">
            <div
            class="absolute mx-2"
            v-text="title" />
            <div class="absolute mx-2 space-x-2 right-0">
                <button>-</button>
                <button>+</button>
                <button>x</button>
            </div>
        </div>
        <div :class="`${$options.name}__content bg-white w-full h-full`"><slot /></div>
    </DraggableResizable>
</template>

<script>
import DraggableResizable from 'vue-draggable-resizable'

export default {
    name: 'AppWindow',
    components: {
        DraggableResizable,
    },
    props: {
        title: {
            type: String,
            required: true,
        },
        headerIcon: {
            type: String,
            required: false,
            default: '',
        },
        hasHeader: {
            type: Boolean,
            required: false,
            default: true,
        },
        hasBorder: {
            type: Boolean,
            required: false,
            default: true,
        },
        minimizable: {
            type: Boolean,
            required: false,
            default: true,
        },
        startX: {
            type: Number,
            required: false,
            default: 100,
        },
        startY: {
            type: Number,
            required: false,
            default: 100,
        },
    },
}
</script>

<style lang="scss" scoped>
.AppWindow {
    $root: &;
    &__content {
        border: #7296dd solid 3px;
        #{$root}.active &{
            border: #005bd6 solid 3px;
        }
        #{$root}.has-header & {
            border-top: none !important;
        }
        #{$root}.borderless & {
            border: none !important;
        }
    }

    &__header_bg {
        position: relative;
        width: 100%;
        height: 28px;
        border-top-left-radius: 8px;
        border-top-right-radius: 8px;
        user-select: none;

        &::before,
        &::after {
            content: "";
            position: absolute;
            bottom: 0;
            width: 12px;
            height: 28px;
            opacity: 0.2;
        }
        &::before {
            left: 0;
            border-top-left-radius: 8px;
            background-image: linear-gradient(to right, rgb(22, 56, 230) 0%, rgba(0, 0, 0, 0) 100%);
        }
        &::after {
            right: 0;
            border-top-right-radius: 8px;
            background-image: linear-gradient(to left, rgb(22, 56, 230) 0%, rgba(0, 0, 0, 0) 100%);
        }

        background-image: linear-gradient(rgb(118, 151, 231) 0%, rgb(126, 158, 227) 3%, rgb(148, 175, 232) 6%, rgb(151, 180, 233) 8%, rgb(130, 165, 228) 14%, rgb(124, 159, 226) 17%, rgb(121, 150, 222) 25%, rgb(123, 153, 225) 56%, rgb(130, 169, 233) 81%, rgb(128, 165, 231) 89%, rgb(123, 150, 225) 94%, rgb(122, 147, 223) 97%, rgb(171, 186, 227) 100%);

        #{$root}.active & {
            background-image: linear-gradient(rgb(0, 88, 238) 0%, rgb(53, 147, 255) 4%, rgb(40, 142, 255) 6%, rgb(18, 125, 255) 8%, rgb(3, 111, 252) 10%, rgb(2, 98, 238) 14%, rgb(0, 87, 229) 20%, rgb(0, 84, 227) 24%, rgb(0, 85, 235) 56%, rgb(0, 91, 245) 66%, rgb(2, 106, 254) 76%, rgb(0, 98, 239) 86%, rgb(0, 82, 214) 92%, rgb(0, 64, 171) 94%, rgb(0, 48, 146) 100%);
            &::before,
            &::after {
                opacity: 1;
            }
        }
    }

    &__appIcon {
        height: 15px;
        width: 15px;
        margin: 3px;
    }
}
</style>
