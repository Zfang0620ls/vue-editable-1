<template>
<div>
    <div v-show="!editing" @dblclick="setEditing(true)">
        <label> {{item}} </label>
    </div>
    <!-- // @keyup.enter.prevent="setEditing(false)" -->
    <textarea v-focus="editing" class="input" v-show="editing" v-model="val" @blur='setEditing(false)'></textarea>
</div>
</template>

<style scoped>
label {
    width: 100%;
    border: 1px solid transparent;
    /* otherwise empty cell click event does not fire */
}

div {
    height: 100%;
    border: 1px solid transparent;
}
</style>

<script>
import {
    focus
} from 'vue-focus';

export default {
    data: () => ({
        val: '',
        editing: false
    }),

    props: ['item'],

    directives: {
        focus: focus
    },

    methods: {
        setEditing: function(e) {
            this.editing = e;
            if (e) {
                this.val = this.item;
            } else {
                this.update(this.val);
            }
        },

        update: function(e) {
            // console.log('update', e);
            this.$emit('updated', this.val);
        },
    }
}
</script>
