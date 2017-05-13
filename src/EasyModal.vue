<style>
.em__mask {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background-color: rgba(0, 0, 0, .7);
    z-index: 9998;
}

.em__main {
    position: absolute;
    z-index: 9999;
    top: 20%;
    left: 0;
    right: 0;
}

.em__body {
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

.em__buttons button + button {
    margin-left: 10px;
}
</style>
<template>
    <div class="em__container" v-show="show">
        <div class="em__mask" @click="clickMask"></div>
        <div class="em__main">
            <template v-if="type === 1">
                <div class="em__body">
                    <div class="em__content">
                        <slot name="content">Easy modal: type 1</slot>
                    </div>
                    <div class="em__buttons" v-show="withCancel && withYes">
                        <button v-show="withCancel" @click="cancel">Cancel</button>
                        <button v-show="withYes" @click="yes">Yes</button>
                    </div>
                </div>
            </template>
            <template v-else>
                <slot name="body">Easy modal: type 2</slot>
            </template>
        </div>
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
        withYes: {
            type: Boolean,
            required: false,
            default: true
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