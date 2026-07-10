# GridNexa

A developer-first Excel-like data grid for React, Vue, Angular, and JavaScript.

GridNexa helps developers ship polished data-heavy apps faster with built-in editing, filtering, undo/redo, export, saved views, change review, validation, diagnostics, and one-click repro export.

> GridNexa is distributed through public npm packages. The source repository is private while the project is in active development.

## Install

### React

```bash
pnpm add @gridnexa/react
```
```ts
import { GridNexa } from "@gridnexa/react";
import "@gridnexa/react/index.css";

export function App() {
  return (
    <GridNexa
      columns={columns}
      rows={rows}
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
Packages
1. React: @gridnexa/react
2. Vue: @gridnexa/vue
3. Angular: @gridnexa/angular
4. JavaScript: @gridnexa/javascript
5. Core: @gridnexa/core

Features
- React, Vue, Angular, and vanilla JavaScript support
- Built-in dark and light themes
- Sorting and filtering
- Quick filter and advanced filters
- Editable cells
- Undo and redo
- Fill handle
- Copy and paste
- Row numbers
- Checkbox selection
- Row reorder
- Column resize, reorder, hide, pin, and auto-size
- Saved views
- Command palette
- Change review before save
- Validation and save blocking
- CSV and Excel export
- Pagination
- Grouping and pivot-style workflows
- Tree data patterns
- Diagnostics panel
- One-click repro export

Repro Recorder
GridNexa includes diagnostics and repro export for debugging complex grid issues.

```tsx
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

The exported JSON includes:
- columns
- sampled rows
- visible rows
- current grid state
- filter/sort/page/column state
- recent user actions
- change review entries
- browser info
- generated React repro snippet
This makes grid bugs easier to report, share, and reproduce.

Why GridNexa?
Most grids give you rows and columns. Real applications need more:
- users need saved views
- admins need validation
- operators need change review
- developers need diagnostics
- support teams need reproducible bug reports
GridNexa includes these workflows as first-class features.

Comparison
| Feature | GridNexa | AG Grid | MUI X Data Grid | TanStack Table | Handsontable |
|---|---:|---:|---:|---:|---:|
| React support | Yes | Yes | Yes | Yes | Yes |
| Vue support | Yes | Yes | No main Vue grid | Headless/community | Yes |
| Angular support | Yes | Yes | No | Headless/community | Yes |
| Vanilla JavaScript support | Yes | Yes | No | Core/headless | Yes |
| Styled UI included | Yes | Yes | Yes | No | Yes |
| Excel-like editing | Yes | Yes | Yes | Build yourself | Yes |
| Undo/redo | Yes | Yes | Yes | Build yourself | Yes |
| Fill handle | Yes | Yes | Limited/varies | Build yourself | Yes |
| Saved views | Yes | Custom/state APIs | Custom/state APIs | Build yourself | Custom |
| Change review | Yes | Custom | Custom | Build yourself | Custom |
| Command palette | Yes | Custom | Custom | Build yourself | Custom |
| Repro export | Yes | Custom | Custom | Build yourself | Custom |

Use Cases
GridNexa is useful for:
- SaaS dashboards
- admin panels
- CRM screens
- finance tools
- operations tools
- internal tools
- editable business tables
- spreadsheet-like web apps
- data review workflows

Links
- npm React package: https://www.npmjs.com/package/@gridnexa/react
- npm Vue package: https://www.npmjs.com/package/@gridnexa/vue
- npm Angular package: https://www.npmjs.com/package/@gridnexa/angular
- npm JavaScript package: https://www.npmjs.com/package/@gridnexa/javascript
- Demo: coming soon
- Docs: https://www.gridnexa.in/docs

Status
GridNexa is in active development. APIs may evolve as the package improves.

Feedback
Use GitHub Issues in this public repo for:
- bug reports
- feature requests
- documentation feedback
- integration questions
