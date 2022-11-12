<template>
    <section>
        <span>บ้านนายดิน</span>
        <img src="https://upload.wikimedia.org/wikipedia/commons/6/6e/Harry_Potter_wordmark.svg" alt="">
        <span class="hide">บ้านนายดิน</span>
    </section>
</template>
<script>
export default {
    name: 'topBar'
}
</script>
<style scoped lang="scss">
section {
    width: auto;
    height: 50px;
    padding: 0 24px 0;
    background-color: rgb(33, 47, 90);
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: white;

    span {
        font-size: 1.2rem;
        cursor: default;
    }

    .hide {
        opacity: 0;
    }

    img {
        height: 50px;
        filter: drop-shadow(0 2px 2px rgba(255, 255, 255, 1));
    }
}
</style>