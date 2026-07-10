# GridNexa Vue

GridNexa Vue provides the GridNexa data grid for Vue 3 applications.

## Install

```bash
pnpm add @gridnexa/vue
```

## Basic Example

```vue
<script setup lang="ts">
import { GridNexaVue } from "@gridnexa/vue";
import "@gridnexa/vue/index.css";

const columns = [
  { id: "name", field: "name", headerName: "Name", editable: true, filter: "text" },
  { id: "department", field: "department", headerName: "Department", filter: "set" },
  { id: "score", field: "score", headerName: "Score", editable: true, filter: "number" },
];

const rows = [
  { id: 1, name: "John Carter", department: "Operations", score: 92 },
  { id: 2, name: "Jane Smith", department: "Marketing", score: 85 },
];
</script>

<template>
  <GridNexaVue
    :columns="columns"
    :rows="rows"
    theme="dark"
    row-numbers
    checkbox-selection
  />
</template>
```

## Feature Example

```vue
<template>
  <GridNexaVue
    :columns="columns"
    :rows="rows"
    theme="dark"
    row-numbers
    checkbox-selection
    enable-undo-redo
    enable-fill-handle
    :toolbar="{
      quickFilter: true,
      find: true,
      undoRedo: true,
      filters: true,
      columns: true,
      saveAll: true,
      exportCsv: true,
      exportExcel: true
    }"
    :diagnostics="{
      recorder: true,
      exportRepro: true
    }"
  />
</template>
```

## Events

```vue
<GridNexaVue
  :columns="columns"
  :rows="rows"
  @data-change="handleDataChange"
  @save-all="handleSaveAll"
/>
```

```ts
function handleDataChange(event) {
  console.log("Rows changed", event);
}

function handleSaveAll(event) {
  console.log("Save all", event.rows);
}
```

## When To Use

Use GridNexa Vue when building:

- admin panels
- data dashboards
- internal tools
- CRM screens
- editable business tables
- operations tools

## Notes

For best behavior, keep column IDs stable and use stable row IDs in your data.
