<style lang="scss">
.em {
    &__mask {
        position: fixed;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background-color: rgba(0, 0, 0, .5);
        z-index: 9998;
    }

    &__header {
        position: relative;
        margin-bottom: 15px;
    }

    &__title {
        font-size: 20px;
    }

    &__times {
        position: absolute;
        top: 0;
        right: 0;
        font-size: 20px;
        cursor: pointer;
    }

    &__body {
        position: absolute;
        z-index: 9999;
        top: 20%;
        left: 0;
        right: 0;
        background-color: #fff;
        padding: 20px;
        margin: 0 auto;
        max-width: 350px;
    }

    &__content {
        font-size: 16px;
    }

    &__buttons {
        display: flex;
        margin-top: 15px;

        button {
            font-size: 14px;
        }

        button+button {
            margin-left: 10px;
        }
    }
}
</style>
<template>
    <div class="em__container" v-show="show">
        <div class="em__mask" @click="clickMask" v-show="withMask" :style="maskStyle"></div>
        <template v-if="type === 1">
            <div class="em__body" :style="bodyStyle">
                <div class="em__header">
                    <div class="em__title">
                        <slot name="title">Default title</slot>
                    </div>
                    <a class="em__times" v-show="withTimes" @click="times">&times;</a>
                </div>
                <div class="em__content">
                    <slot name="content">Easy modal: type 1</slot>
                </div>
                <div class="em__buttons" v-show="withCancel && withYes">
                    <button v-show="withCancel" @click="cancel">{{ cancelText }}</button>
                    <button v-show="withYes" @click="yes">{{ yesText }}</button>
                </div>
            </div>
        </template>
        <template v-else>
            <slot name="body">Easy modal: type 2</slot>
        </template>
    </div>
</template>
<script>
export default {
    name: 'EasyModal',
    props: {
        type: {
            type: Number,
            required: false,
            default: 1
        },
        show: {
            type: Boolean,
            required: true
        },
        withTimes: {
            type: Boolean,
            required: false,
            default: true
        },
        bodyStyle: {
            type: Object,
            required: false,
            default() {
                return {}
            }
        },
        withMask: {
            type: Boolean,
            required: false,
            default: true
        },
        maskStyle: {
            type: Object,
            required: false,
            default() {
                return {}
            }
        },
        withCancel: {
            type: Boolean,
            required: false,
            default: true
        },
        cancelText: {
            type: String,
            required: false,
            default: 'Cancel'
        },
        withYes: {
            type: Boolean,
            required: false,
            default: true
        },
        yesText: {
            type: String,
            required: false,
            default: 'Yes'
        }
    },
    methods: {
        clickMask() {
            this.$emit('click-mask')
        },
        times() {
            this.$emit('times')
        },
        cancel() {
            this.$emit('cancel')
        },
        yes() {
            this.$emit('yes')
        }
    }
}
</script>