# Diagnostics And Repro Snapshots

GridNexa diagnostics captures hard-to-reproduce grid states and recent user actions. Version 0.1.19 supports both exporting and importing repro JSON snapshots.

## Enable Diagnostics

```tsx
<GridNexa
  columns={columns}
  rows={rows}
  diagnostics={{
    recorder: true,
    exportRepro: true,
    rowSampleSize: 50,
    maxEvents: 40,
    fileName: "gridnexa-repro.json",
    showPanel: true,
  }}
/>
```

You can also pass `diagnostics` as a boolean to use the defaults.

## Snapshot Contents

A repro snapshot contains sanitized diagnostic data, including:

- schema and package information
- generation time, browser, and viewport information
- row, filtered-row, rendered-row, column, filter, invalid-cell, and event counts
- column definitions and sampled rows
- visible rows and current grid state
- selection and range state
- filters, sorting, pagination, grouping, pivot, and column state
- change-review entries and recent diagnostic events
- a generated React example

Functions and other values that cannot be represented safely in JSON are sanitized.

## Export From The API

```tsx
import { useRef } from "react";
import { GridNexa, type GridNexaApi } from "@gridnexa/react";

const apiRef = useRef<GridNexaApi<Employee> | null>(null);

<GridNexa
  apiRef={apiRef}
  columns={columns}
  rows={rows}
  diagnostics={{ recorder: true, exportRepro: true }}
/>;

apiRef.current?.exportDiagnostics();
```

The Diagnostics panel and command palette also expose **Export repro**.

## Import A Snapshot

Open Diagnostics and choose **Import repro**, or select **Import repro snapshot** from the command palette. GridNexa reads the JSON file, restores the supported snapshot state, resets the recorded event list, and records the import as a new diagnostics event.

Snapshot import is intended for debugging. Review snapshots before sharing them because sampled rows may contain application data.

## Recommended Use

Enable diagnostics in development, staging, support builds, and complex internal tools. Choose a conservative `rowSampleSize` and avoid including sensitive production data in shared reports.
