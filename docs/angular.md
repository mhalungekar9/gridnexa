
# GridNexa Angular

GridNexa Angular provides the GridNexa data grid for Angular applications.

## Install

```bash
pnpm add @gridnexa/angular
```

## Basic Example

```ts
import { Component } from "@angular/core";
import { GridNexaAngularComponent } from "@gridnexa/angular";
import "@gridnexa/angular/index.css";

@Component({
  selector: "app-employees-grid",
  standalone: true,
  imports: [GridNexaAngularComponent],
  template: `
    <gridnexa-angular
      [columns]="columns"
      [rows]="rows"
      theme="dark"
      [rowNumbers]="true"
      [checkboxSelection]="true"
    />
  `,
})
export class EmployeesGridComponent {
  columns = [
    { id: "name", field: "name", headerName: "Name", editable: true, filter: "text" },
    { id: "department", field: "department", headerName: "Department", filter: "set" },
    { id: "score", field: "score", headerName: "Score", editable: true, filter: "number" },
  ];

  rows = [
    { id: 1, name: "John Carter", department: "Operations", score: 92 },
    { id: 2, name: "Jane Smith", department: "Marketing", score: 85 },
  ];
}
```

## Feature Example

```html
<gridnexa-angular
  [columns]="columns"
  [rows]="rows"
  theme="dark"
  [rowNumbers]="true"
  [checkboxSelection]="true"
  [enableUndoRedo]="true"
  [enableFillHandle]="true"
  [toolbar]="{
    quickFilter: true,
    find: true,
    undoRedo: true,
    filters: true,
    columns: true,
    saveAll: true,
    exportCsv: true,
    exportExcel: true
  }"
  [diagnostics]="{
    recorder: true,
    exportRepro: true
  }"
  (dataChange)="onDataChange($event)"
  (saveAll)="onSaveAll($event)"
/>
```

## Events

```ts
onDataChange(event: any) {
  console.log("Rows changed", event);
}

onSaveAll(event: any) {
  console.log("Save all", event.rows);
}
```

## Useful Features

- sorting
- filtering
- editing
- row selection
- undo/redo
- export
- validation
- diagnostics
- repro export

## Notes

Use GridNexa Angular for admin panels, internal tools, dashboards, and data-heavy Angular applications.
