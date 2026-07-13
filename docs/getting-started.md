# Getting Started

GridNexa is an Excel-style data grid for React, Vue, Angular, and framework-free JavaScript. Version 0.1.19 includes editing, import/export, charts, Dashboard Generator, Data Health, Trust Mode, collaboration, accessibility, advanced styling, grouping, pivoting, saved views, validation, diagnostics, and repro snapshot import/export.

## Choose A Package

```bash
pnpm add @gridnexa/react
pnpm add @gridnexa/vue
pnpm add @gridnexa/angular
pnpm add @gridnexa/javascript
```

Install only the framework package you need. Install `@gridnexa/core` directly when building wrappers, backend contracts, server-side grid operations, AI action plans, or cross-framework tooling.

## React Quick Start

```tsx
import { GridNexa, type Column } from "@gridnexa/react";
import "@gridnexa/react/index.css";

type Employee = {
  id: number;
  name: string;
  department: string;
  score: number;
};

const columns: Column<Employee>[] = [
  { id: "name", field: "name", headerName: "Name", editable: true, filter: "text" },
  { id: "department", field: "department", headerName: "Department", filter: "set" },
  { id: "score", field: "score", headerName: "Score", editable: true, filter: "number" },
];

const rows: Employee[] = [
  { id: 1, name: "John Carter", department: "Operations", score: 92 },
  { id: 2, name: "Alice Moreau", department: "Product", score: 87 },
];

export default function App() {
  return (
    <GridNexa
      columns={columns}
      rows={rows}
      getRowId={(row) => row.id}
      rowNumbers
      checkboxSelection
      enableRangeSelection
      enableFillHandle
      enableUndoRedo
      pageSize={20}
    />
  );
}
```

Import the package CSS once in your application entry. It contains the shared header layout, drag/reorder indicators, pinned-column rules, popovers, scrollbars, and theme variables. Use `unstyled` only when your design system supplies every rule.

## Add Productivity Features

```tsx
<GridNexa
  columns={columns}
  rows={rows}
  preset="admin"
  toolbar={{
    importData: true,
    copyPaste: true,
    bulkEdit: true,
    findReplace: true,
    charts: true,
    dashboard: true,
    dataHealth: true,
    trustMode: true,
    exportCsv: true,
    exportExcel: true,
  }}
  views={{ key: "employees-grid-views" }}
  commandPalette
  changeReview
  validation={{ blockSave: true, rules: { name: { required: true } } }}
  diagnostics={{ recorder: true, exportRepro: true }}
  dataHealth
  trustMode
/>
```

Keep column IDs and row IDs stable. Use a unique `views.key` or `stateStorage.key` for each unrelated grid.

Built-in themes include `modern-light`, `modern-dark`, `compact`, `minimal`, `enterprise`, `high-contrast`, `light`, `dark`, and `system`. Use `styling` for typed theme tokens and slot styles, and column `headerStyle`, `cellStyle`, and `textDisplay` for local presentation rules.

## Framework Guides

- [React](./react.md)
- [Vue](./vue.md)
- [Angular](./angular.md)
- [JavaScript](./javascript.md)
- [Core](./core.md)
- [Diagnostics](./diagnostics.md)
- [Comparison](./comparison.md)
- [FAQ](./faq.md)
