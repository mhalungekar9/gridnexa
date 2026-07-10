
```md
# GridNexa React
```
GridNexa React is the primary package for React applications.

## Install

```bash
pnpm add @gridnexa/react
```

Import
```jsx
import { GridNexa } from "@gridnexa/react";
import "@gridnexa/react/index.css";
```

Basic Example
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

export function EmployeesGrid() {
  return (
    <GridNexa
      columns={columns}
      rows={rows}
      getRowId={(row) => row.id}
      theme="dark"
      rowNumbers
      checkboxSelection
    />
  );
}
```

Full Feature Example
```jsx
<GridNexa
  columns={columns}
  rows={rows}
  getRowId={(row) => row.id}
  theme="dark"
  rowNumbers
  checkboxSelection
  enableUndoRedo
  enableFillHandle
  enableRowReorder
  toolbar={{
    quickFilter: true,
    find: true,
    undoRedo: true,
    fill: true,
    filters: true,
    advancedFilter: true,
    columns: true,
    addRow: true,
    deleteRow: true,
    saveAll: true,
    exportCsv: true,
    exportExcel: true
  }}
  changeReview
  diagnostics={{
    recorder: true,
    exportRepro: true
  }}
/>
```

API Ref
```tsx
import { useRef } from "react";
import { GridNexa, type GridNexaApi } from "@gridnexa/react";

const apiRef = useRef<GridNexaApi<Employee> | null>(null);

<GridNexa
  apiRef={apiRef}
  columns={columns}
  rows={rows}
/>;

apiRef.current?.addRow();
apiRef.current?.deleteSelectedRows();
apiRef.current?.exportDiagnostics();
```

Useful Props
| Prop | Purpose |
|---|---|
| `columns` | Column definitions |
| `rows` | Row data |
| `getRowId` | Stable row identity |
| `theme` | `light`, `dark`, or `system` |
| `rowNumbers` | Show row number column |
| `checkboxSelection` | Enable checkbox selection |
| `enableUndoRedo` | Enable undo and redo |
| `enableFillHandle` | Enable Excel-like fill |
| `toolbar` | Enable toolbar controls |
| `changeReview` | Track edits before save |
| `diagnostics` | Enable diagnostics and repro export |

Notes
Use getRowId whenever possible. Stable row IDs improve selection, editing, deletion, and controlled-row behavior.
