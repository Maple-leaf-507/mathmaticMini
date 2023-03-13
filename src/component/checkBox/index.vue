<template>
    <view class="checkbox"></view>
</template>

<script setup lang="ts">

</script>

<style scoped>
    .checkbox {
        -webkit-appearance: none;
        -moz-appearance: none;
        border: 2px solid #E64440;
        width: 18px;
        height: 18px;
        border-radius: 50%;
        vertical-align: sub;
        float: right;
        position: relative;
    }
    .checkbox:checked {
        background-color: #E64440;
    }
    .checkbox:checked::after {
        content: '';
        position: absolute;
        left: 3px;
        top: 3px;
        height: 6px;
        width: 10px;
        border: 2px solid #fff;
        border-top: none;
        border-right: none;
        transform: rotate(-45deg);
    }
</style>
