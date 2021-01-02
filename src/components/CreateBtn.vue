<template>
    <div>
        <a
            class="waves-effect waves-light btn-small createBtn"
            v-on:click="addTicket"
        >
            <i class="material-icons right">add</i>
            <b>Create</b>
        </a>
    </div>
</template>

<script>
export default {
    name: "CreateBtn",
    props: {
        msg: String,
    },
    methods: {
        addTicket: () => {
            console.log("blah");
        },
    },
};
</script>

<style scoped>
.createBtn {
    margin-top: 2rem;
}
</style>
