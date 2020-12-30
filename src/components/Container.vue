<template>
    <div class="container">
        <div class="row">
            <div class="col"><CreateBtn /></div>
            <div class="input-field col s3 search">
                <input type="text" placeholder="Search" />

            </div>
        </div>
        <div class="row">
            <BugList />
        </div>
    </div>
</template>

<script>
import CreateBtn from "./CreateBtn.vue";
import BugList from "./BugList.vue";
export default {
    name: "Container",
    components: {
        CreateBtn,
        BugList,
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.search {
    float: right;
}

.container {
    margin-top: 10px;
}

.row {
    padding: 10px;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}
</style>
