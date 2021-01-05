<template>
    <div>
        <a
            class="waves-effect waves-light btn-small createBtn"
            v-on:click="onCreate"
        >
            <i class="material-icons right">add</i>
            <b>Create</b>
        </a>
    </div>
</template>

<script>
export default {
    name: "CreateBtn",
    props: ["onCreate"],
};
</script>

<style scoped>
.createBtn {
    margin-top: 2rem;
}
</style>
