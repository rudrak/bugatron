<template>
    <div class="container">
        <div class="row">
            <div class="col"><CreateBtn /></div>
            <div class="input-field col s3 search">
                <input type="text" placeholder="Search" />
            </div>
        </div>
        <div class="row">
            <BugList :bugs="bugs" :selected="selected" />
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
    data: () => {
        return {
            selected: null,
            bugs: [
                {
                    id: 1,
                    title: "UI Does not work",
                    details:
                        "UI work needs to be over. But it is not done yet.",
                    state: "__CLOSED__",
                    owner: "User1",
                },
                {
                    id: 2,
                    title: "Styles need some work",
                    details:
                        "UI work needs to be over. But it is not done yet.",
                    state: "__INPROGRESS__",
                    owner: "User2",
                },
                {
                    id: 3,
                    title: "Quick prototyping",
                    details:
                        "UI work needs to be over. But it is not done yet.",
                    state: "__OPEN__",
                    owner: "User1",
                },
            ],
        };
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
