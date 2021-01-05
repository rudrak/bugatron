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
                <span class="state">{{
                    StateLabelsMap[StateTypes[bug.state]]
                }}</span>
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
import { StateTypes, StateLabelsMap } from "../constants/BugConstants";

export default {
    name: "BugList",
    components: {
        BugEditor,
    },
    props: ["bugs", "selected"],
    methods: {
        onSelectBug(bugId) {
            this.selected = bugId;
        },

        onClose() {
            this.selected = null;
        },
    },
    data: () => {
        return {
            StateLabelsMap: Object.freeze(StateLabelsMap),
            StateTypes: Object.freeze(StateTypes),
        };
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
    text-transform: uppercase;
}

.title {
    font-size: 14px;
}
</style>
