<template>
    <div class="modalContainer">
        <div class="bugModal modal-content">
            <div class="header">
                {{ bug.owner }}
                <div class="closeBtn" @click.stop="localClose">
                    <i class="material-icons">close</i>
                </div>
            </div>
            <div class="content">
                <div class="row">
                    <div class="input-field s12">
                        <input
                            value="`${bug.title}`"
                            id="`${bug.id}-bug-title`"
                            type="text"
                            class="validate"
                        />
                        <label for="${bug.id}-bug-title`">Title</label>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "BugEditor",
    props: ["bug", "onClose"],
    methods: {
        localClose() {
            this.onClose();
        },
    },
};
</script>

<style scoped>
.modalContainer {
    position: fixed;
    background-color: rgb(10, 10, 10, 0.1);
    display: block;
    height: 100vh;
    width: 100vw;
    z-index: 10;
    top: 0;
    left: 0;
}

.bugModal {
    opacity: 1;
    position: fixed;
    min-width: 500px;
    z-index: 100;
    background: #fff;
    border-radius: 4px;
    max-width: 600px;
    max-height: 280px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    padding: 30px 20px 10px 35px;
    overflow: auto;
}

.header {
    padding: 0px 0px 10px;
    border-bottom: 1px solid #ddd;
}
.closeBtn {
    float: right;
    cursor: default;
}
</style>
