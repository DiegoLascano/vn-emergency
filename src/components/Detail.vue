<template>
    <view class="detail-container">
        <text>detail screen</text>
        <button title="Go to detail screen" @press="navigate"></button>
    </view>
</template>

<script>
export default {
    props: {
        navigation: {
        type: Object
        }
    },
    methods: {
        navigate() {
        this.navigation.navigate("Home");
        }
    }
}
</script>

<style>
    .detail-container{
        flex: 1;
        justify-content: center;
        align-content: center;
    }
</style>
