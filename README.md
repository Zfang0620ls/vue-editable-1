# vue-editable
Editable component.
I use this component for online-editing of a SQLite database.

# Initial
Setup your project with vue-cli, for example using the webpack template.
Add this file to your components folder.

# Dependencies
Add the vue-focus component to your project.

`npm install vue-focus --save`

# Example usage
This is an example setup of a VueJS single file component consisting of a table with editable cells.
For styling Bulma and Font Awesome are used.
```
<template>
<div>
<table class="table is-bordered is-striped is-narrow">
    <thead>
        <tr>
            <th>nl</th>
            <th>en</th>
            <th> <i class="fa fa-plus fa-lg fa-fw" @click="onAdd"></i> </th>
        </tr>
    </thead>
    <tbody>
        <tr v-for="(item, i) of rows">
            <td>
                <editable :item="item.nl" @updated="onUpdate(i,'nl',$event)"></editable>
            </td>
            <td>
                <editable :item="item.en" @updated="onUpdate(i,'en',$event)"></editable>
            </td>
            <td> <i class="fa fa-trash-o fa-lg fa-fw" @click="onDelete(i,$event)"></i> </td>
        </tr>
    </tbody>
</table>

</div>
</template>

<style>
</style>

<script>
import editable from './Editable';
import axios from 'axios';

export default {
    data: () => ({
        rows: [],
        errors: [],
    }),

    methods: {
        onUpdate: function(row, col, newValue) {
            console.log('update', row, this.rows[row][col], newValue);
            this.rows[row][col] = newValue;
            this.updated = true;
            // ... implement your update function
            // axios.post(url, this.rows[row], config) ...

        },
        onAdd: function() {
            console.log('add');

            var newRow = {
                nl: '',
                en: '',
            // ... implement your add function
            // axios.post(url, newRow) ...
        },
        onDelete: function(index, event) {
            // ... implement your delete function
        },
    },

    components: {
        editable
    },

    // Fetches rows when the component is created.
    created() {
        axios.get(...)
            .then(response => {
                // console.log(response.data);
                this.rows = response.data;
            })
            .catch(e => {
                this.errors.push(e)
            });
    }
}

</script>
```

