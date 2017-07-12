# vue-editable
Editable component.
I use this component for online-editing of a SQLite database.

# Initial
Setup your project with vue-cli, for example using the webpack template.
Add this file to your components folder.

# Dependencies
Add the vue-focus component to your project.

npm install vue-focus --save

# Example usage
```
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
</table>```

