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

.em__body {
    position: absolute;
    z-index: 9999;
    top: 20%;
    left: 0; right: 0;
    background-color: #fff;
    border-radius: 10px;
    width: 360px;
    padding: 20px 0;
    margin: 0 auto;
    text-align: center;
}
</style>
<template>
    <div class="em__container" v-show="show">
        <div class="em__mask" @click="clickMask"></div>
        <div class="em__body">
            <slot name="body">Easy modal</slot>
        </div>
    </div>
</template>
<script>
export default {
    name: 'EasyModal',
    props: {
        show: {
            type: Boolean,
            required: true,
            default: false
        }
    },
    methods: {
        clickMask: function() {
            this.$emit('click-mask')
        }
    }
}
</script>