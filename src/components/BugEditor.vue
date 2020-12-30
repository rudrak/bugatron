<template>
    <div class="modalContainer">
        <div class="modal"></div>
    </div>
</template>

<script>
export default {
    name: "BugEditor",
};
</script>

<style scoped>
.modalContainer {
    position: fixed;
    width: 100vw;
    height: 100vh;
    background: rgb(0, 0, 0, 0.1);
    z-index: 10;
    top: 0;
    left: 0;
}

.modal {
    min-width: 400px;
    min-height: 250px;
    background: #fff;
    z-index: 20;
}
</style>
