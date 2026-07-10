
# Diagnostics And Repro Recorder

GridNexa Diagnostics helps developers debug complex grid states.

Data-grid issues are often hard to reproduce because they depend on a sequence of user actions such as filtering, sorting, resizing, editing, paging, and undoing changes.

GridNexa solves this with a diagnostics panel and one-click repro export.

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
    fileName: "gridnexa-repro.json"
  }}
/>
```

## What Gets Exported?

The repro JSON includes:

- package name
- generated timestamp
- browser information
- viewport size
- row counts
- column counts
- filter counts
- invalid cell counts
- columns
- sampled rows
- visible rows
- current grid state
- selected rows
- selected cell
- selected range
- change review entries
- recent diagnostic events
- generated React repro snippet

## Why It Matters

Without diagnostics, bug reports often sound like:

> The grid broke after I filtered, sorted, changed pages, edited a cell, and clicked undo.

With Repro Recorder, the user can export a JSON file that captures the grid state and recent actions.

This helps developers:

- reproduce bugs faster
- compare grid state between environments
- debug installed package behavior
- share issues with support
- create minimal examples

## Export From The UI

Open the Diagnostics panel and click:

```text
Export repro
```

## Export From API

```tsx
const apiRef = useRef<GridNexaApi<Row> | null>(null);

<GridNexa
  apiRef={apiRef}
  columns={columns}
  rows={rows}
  diagnostics={{ recorder: true, exportRepro: true }}
/>;

apiRef.current?.exportDiagnostics();
```

## Example Output

```json
{
  "schemaVersion": 1,
  "packageName": "@gridnexa/react",
  "generatedAt": "2026-07-10T10:30:00.000Z",
  "counts": {
    "rows": 100,
    "filteredRows": 25,
    "renderedRows": 10,
    "columns": 8,
    "visibleColumns": 6
  },
  "columns": [],
  "rows": [],
  "state": {},
  "events": [],
  "reactExample": "..."
}
```

## Can I Import A Repro JSON?

Currently, Repro Recorder is designed for export and debugging.

You can manually use:

```tsx
<GridNexa
  columns={repro.columns}
  rows={repro.rows}
/>
```

A future feature may add direct snapshot import:

```tsx
<GridNexa repro={snapshot} />
```

## Recommended Use

Enable diagnostics in development, staging, support builds, and complex internal tools.

```tsx
diagnostics={{
  recorder: true,
  exportRepro: true
}}
```
