
# GridNexa JavaScript

GridNexa JavaScript provides a framework-free data grid for browser applications.

## Install

```bash
pnpm add @gridnexa/javascript
```

## Basic Example

```ts
import { createGridNexa } from "@gridnexa/javascript";
import "@gridnexa/javascript/index.css";

const columns = [
  { id: "name", field: "name", headerName: "Name", editable: true, filter: "text" },
  { id: "department", field: "department", headerName: "Department", filter: "set" },
  { id: "score", field: "score", headerName: "Score", editable: true, filter: "number" },
];

const rows = [
  { id: 1, name: "John Carter", department: "Operations", score: 92 },
  { id: 2, name: "Jane Smith", department: "Marketing", score: 85 },
];

createGridNexa(document.querySelector("#grid"), {
  columns,
  rows,
  theme: "dark",
  rowNumbers: true,
  checkboxSelection: true,
});
```

HTML:

```html
<div id="grid"></div>
```

## Feature Example

```ts
const apiRef = { current: null };

createGridNexa(document.querySelector("#grid"), {
  apiRef,
  columns,
  rows,
  theme: "dark",
  rowNumbers: true,
  checkboxSelection: true,
  enableUndoRedo: true,
  enableFillHandle: true,
  toolbar: {
    quickFilter: true,
    find: true,
    undoRedo: true,
    filters: true,
    columns: true,
    saveAll: true,
    exportCsv: true,
    exportExcel: true,
  },
  diagnostics: {
    recorder: true,
    exportRepro: true,
  },
});

apiRef.current?.exportDiagnostics();
```

## API

```ts
apiRef.current?.getRows();
apiRef.current?.setRows(nextRows);
apiRef.current?.addRow();
apiRef.current?.deleteRow(0);
apiRef.current?.deleteSelectedRows();
apiRef.current?.saveAll();
apiRef.current?.exportDiagnostics();
```

## Use Cases

- plain JavaScript apps
- embedded widgets
- dashboards
- internal tools
- non-framework admin screens
- CMS integrations
