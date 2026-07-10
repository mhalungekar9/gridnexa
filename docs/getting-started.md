
# Getting Started

GridNexa is a developer-first Excel-like data grid for React, Vue, Angular, and JavaScript.

It includes editing, filtering, undo/redo, fill handle, export, saved views, change review, validation, diagnostics, and one-click repro export.

## Packages

```bash
pnpm add @gridnexa/react
pnpm add @gridnexa/vue
pnpm add @gridnexa/angular
pnpm add @gridnexa/javascript
```

Install only the package for your framework.

```jsx
import { GridNexa } from "@gridnexa/react";
import "@gridnexa/react/index.css";

const columns = [
  { id: "name", field: "name", headerName: "Name", editable: true, filter: "text" },
  { id: "department", field: "department", headerName: "Department", filter: "set" },
  { id: "score", field: "score", headerName: "Score", editable: true, filter: "number" },
];

const rows = [
  { id: 1, name: "John Carter", department: "Operations", score: 92 },
  { id: 2, name: "Jane Smith", department: "Marketing", score: 85 },
];

export default function App() {
  return (
    <GridNexa
      columns={columns}
      rows={rows}
      getRowId={(row) => row.id}
      theme="dark"
      rowNumbers
      checkboxSelection
      enableUndoRedo
      enableFillHandle
      toolbar={{
        quickFilter: true,
        find: true,
        undoRedo: true,
        filters: true,
        columns: true,
        saveAll: true,
        exportCsv: true,
        exportExcel: true
      }}
      diagnostics={{
        recorder: true,
        exportRepro: true
      }}
    />
  );
}
```

Core Concepts
GridNexa works with two main inputs:
- columns: describes fields, headers, filters, editors, widths, and tools.
- rows: your data array.

```jsx
<GridNexa columns={columns} rows={rows} />
```

Recommended Features To Enable
```jsx
<GridNexa
  columns={columns}
  rows={rows}
  rowNumbers
  checkboxSelection
  enableUndoRedo
  enableFillHandle
  toolbar={{
    quickFilter: true,
    find: true,
    undoRedo: true,
    filters: true,
    columns: true,
    exportCsv: true,
    exportExcel: true
  }}
/>
```

Diagnostics And Repro Export
```jsx
<GridNexa
  columns={columns}
  rows={rows}
  diagnostics={{
    recorder: true,
    exportRepro: true,
    rowSampleSize: 50
  }}
/>
```

Diagnostics can export a JSON snapshot containing:
- columns
- sampled rows
- visible rows
- current grid state
- filters and sorting
- recent user actions
- change review entries
- generated React repro snippet


Framework Guides
- [React](./react.md)
- [Vue](./vue.md)
- [Angular](./angular.md)
- [JavaScript](./javascript.md)
- [Diagnostics](./diagnostics.md)
- [Comparison](./comparison.md)
[FAQ](./faq.md)

```

