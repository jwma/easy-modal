<style>
.em__mask {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background-color: rgba(0, 0, 0, .5);
    z-index: 9998;
}

.em__body {
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

.em__content {
    font-size: 16px;
}

.em__buttons {
    display: flex;
    margin-top: 15px;
}

.em__buttons button {
    font-size: 14px;
}

.em__buttons button+button {
    margin-left: 10px;
}
</style>
<template>
    <div class="em__container" v-show="show">
        <div class="em__mask" @click="clickMask" v-show="withMask" :style="maskStyle"></div>
        <template v-if="type === 1">
            <div class="em__body" :style="bodyStyle">
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
        }
    },
    methods: {
        clickMask() {
            this.$emit('click-mask')
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