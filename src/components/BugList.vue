<template>
    <div class="bugList">
        <div
            v-for="bug in bugs"
            :key="bug.id"
            class="bug"
            @click="onSelectBug(bug.id)"
        >
            <div class="row">
                <input type="checkbox" />
                <span class="title">{{ bug.title }}</span>
                <span class="state">{{ bug.state }}</span>
            </div>
            <div class="row">
                <span
                    ><span class="owner">Owner:&nbsp;</span
                    >{{ bug.owner }}</span
                >
            </div>
            <div v-show="selected === bug.id">
                <BugEditor :bug="bug" :onClose="onClose.bind(this)" />
            </div>
        </div>
    </div>
</template>

<script>
import BugEditor from "./BugEditor.vue";

export default {
    name: "BugList",
    components: {
        BugEditor,
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
                    state: "CLOSED",
                    owner: "User1",
                },
                {
                    id: 2,
                    title: "Styles need some work",
                    details:
                        "UI work needs to be over. But it is not done yet.",
                    state: "IN-PROGRESS",
                    owner: "User2",
                },
                {
                    id: 3,
                    title: "Quick prototyping",
                    details:
                        "UI work needs to be over. But it is not done yet.",
                    state: "OPEN",
                    owner: "User1",
                },
            ],
        };
    },
    methods: {
        onSelectBug(bugId) {
            this.selected = bugId;
        },

        onClose() {
            this.selected = null;
        },
    },
};
</script>

<style scoped>
.bugList {
    border-radius: 4px;
}

.bug {
    border-top: 1px solid #dadada;
    min-height: 100px;
    padding: 10px;
}

.bug:hover {
    background-color: #fafafa;
}

.owner {
    color: #3a3a3a;
}

.state {
    padding: 2px 6px;
    height: 20px;
    font-size: 13px;
    border-radius: 4px;
    background: red;
    color: #fff;
    line-height: 22px;
    margin-left: 5px;
}

.title {
    font-size: 14px;
}
</style>
