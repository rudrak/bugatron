<template>
    <div class="modalContainer">
        <div class="bugModal modal-content">
            <div class="header">
                Bug Editor
                <div class="closeBtn" @click.stop="localClose">
                    <i class="material-icons">close</i>
                </div>
            </div>
            <div class="content">
                <div class="row">
                    <div class="input-field s12">
                        <input
                            v-model="bug.title"
                            :id="bug.id - 'bug - title'"
                            type="text"
                        />
                        <label for="${bug.id}-bug-title`">Title</label>
                    </div>
                </div>
                <div class="row">
                    <div class="input-field row">
                        <select v-model="bug.state" class="statePicker col s6">
                            <option
                                :key="option.value"
                                v-for="option in options"
                                :value="option.value"
                                selected="option.value === bug.state"
                            >
                                {{ option.label }}
                            </option>
                        </select>
                    </div>
                </div>
                <div class="row">
                    <div class="input-field s12">
                        <textarea
                            :id="bug.id - 'bug - details'"
                            class="materialize-textarea"
                            v-model="bug.details"
                        ></textarea>
                        <label for="bug.id - 'bug - details'">Details</label>
                    </div>
                </div>
                <div class="row">
                    <div class="input-field s12">
                        <input
                            v-model="bug.owner"
                            :id="bug.id - 'bug-owner'"
                            type="text"
                        />
                        <label for="${bug.id}-bug-owner`">Owner</label>
                    </div>
                </div>

            </div>
        </div>
    </div>
</template>

<script>
import { StateLabelsMap } from "../constants/BugConstants";

const options = Object.keys(StateLabelsMap).map((_key) => {
    return {
        label: StateLabelsMap[_key],
        value: _key,
    };
});

export default {
    name: "BugEditor",
    props: ["bug", "onClose"],
    methods: {
        localClose() {
            this.onClose();
        },
    },
    data: () => {
        return {
            options,
            StateLabelsMap: Object.freeze(StateLabelsMap),
        };
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
    max-height: 400px;
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

.content {
    padding: 10px 0px;
}

.statePicker {
    display: block;
}
</style>
