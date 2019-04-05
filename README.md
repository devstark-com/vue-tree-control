# vue-tree-control

Powerful and flexible tree-view component for Vue

Сomponent is designed to work with data outside of it and doesn't mutate any data inside.
It only emits various events you should handle by yourself in a parent component so you're free to implement any logic you need e.g. asynchronously mutate your data in your backend and update tree on success or handle errors the way you want.

## Basic usage

- Readonly usage
- Default HTML out of the box

```html
<template>
  <div>
  
    <VueTreeControl
      :data="treeData"
    />
  
  </div>
</template>
```
```js
<script>
import VueTreeControl from 'vue-tree-control'
export default {
  components: {
    VueTreeControl
  },
  data () {
    return {
      treeData: [
        {id: 1, name: 'node 1', parent: null},
        {id: 2, name: 'node 1.1', parent: 1},
        {id: 3, name: 'node 2', parent: null},
        {id: 4, name: 'node 2.1', parent: 3},
        {id: 5, name: 'node 2.1.1', parent: 4},
        {id: 6, name: 'node 3', parent: null},
        {id: 7, name: 'node 3.1', parent: 6},
      ]
    }
  }
}
</script>
```

## Custom node template

You can customize tree node template using default slot

```html
<template>
  <div>
  
    <VueTreeControl
      :data="treeData"
      :expandedKeys.sync="expandedKeys"
    >
      <template slot-scope="{node}">
        <div class="node">
          <div>
            <i :class="iconClass(node)"></i>
            {{ node.name }}
          </div>
        </div>
      </template>
    </VueTreeControl>
  
  </div>
</template>
```

```js
import VueTreeControl from 'vue-tree-control'
export default {
  components: {
    VueTreeControl
  },
  data () {
    return {
      treeData: [
        {id: 1, name: 'node 1', parent: null},
        {id: 2, name: 'node 1.1', parent: 1},
        {id: 3, name: 'node 2', parent: null},
        {id: 4, name: 'node 2.1', parent: 3},
        {id: 5, name: 'node 2.1.1', parent: 4},
        {id: 6, name: 'node 3', parent: null},
        {id: 7, name: 'node 3.1', parent: 6},
      ],
      expandedKeys: []
    }
  },
  methods: {
    iconClass (node) {
      return this.expandedKeys.includes(node.id) ? 'icon-expanded' : 'icon-collapsed'
    }
  }
}
```

## Custom nodes sorting inside parent

You can use custom function to sort nodes at each level

```html
```

```js
```

## Define which nodes should be expandable and which ones shouldn't

You can use your custom logic to decide conditionally which tree nodes should be expandable and which ones are shouldn't e.g. if you use this component for representation of folder and files tree and you want to allow to expand empty folders (which are the leaves without child folders and files), but you need to restrict this behavior for files which are the leaves too.

```html
```

```js
```

## Default expanded nodes / preserve expanded nodes

You can affect which tree nodes should be expanded by default. Also, you're able to track the list of expanded nodes keys, store it anywhere you want and preserve tree state e.g. restore it after page reload.

```html
```

```js
```

## Adding new nodes

```html
```

```js
```

## Renaming nodes

```html
```

```js
```

## Removing nodes

```html
```

```js
```

## Customize node adding using `new` named slot

```html
```

```js
```

## Customize node editing using `edit` named slot

```html
```

```js
```

## Moving nodes using Drag-n-Drop


```html
```

```js
```

## Full featured example

This example covers the most of customization abilities.

The example illustrates how to use `vue-tree-control` to implement the editable folders and files tree according to the following requirements:

- tree data should be stored at the backend
- tree state should be preserved (which nodes are expanded and which ones are not)
- ability to add a new folder (custom template)
- ability to add a new file (custom template)
- ability to remove file/folder
- ability to rename file/folder
- validate file/folder name for uniqueness at adding/renaming
- loading state icon should be applied while adding is in progress
- files shouldn't be expandable since they can't have children by definition
- folders should be expandable even they have not any child folders or files
- sort nodes alphabetically placing folders above files
- ability to drag and drop single folder/file into any folder
- disallow to drag and drop files/folders into particular folders
- disallow to drag particular files/folders

```html
```

```js
```

```css
```
