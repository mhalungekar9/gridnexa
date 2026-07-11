# FAQ

## What is GridNexa?

GridNexa is an Excel-style data grid for React, Vue, Angular, and JavaScript. It includes editing, import/export, charts, filtering, grouping, pivoting, Data Health, saved views, validation, diagnostics, and repro snapshot import/export.

## Which package should I install?

- React: `pnpm add @gridnexa/react`
- Vue: `pnpm add @gridnexa/vue`
- Angular: `pnpm add @gridnexa/angular`
- JavaScript: `pnpm add @gridnexa/javascript`
- Shared contracts/tooling: `pnpm add @gridnexa/core`

## Do I need to import CSS?

Yes, import the framework package CSS once in your app entry:

```ts
import "@gridnexa/react/index.css";
```

The React package also injects runtime styles, but the CSS export keeps installed applications consistent with the playground. Use `unstyled` only when your design system owns every rule.

## Which themes are supported?

Use `theme="light"`, `theme="dark"`, or `theme="system"`. Density controls, CSS variables, stable class names, custom icons, and class callbacks support deeper customization.

## Which files can GridNexa import?

The import toolbar accepts Excel `.xlsx`/`.xls`, CSV, TSV, TXT, and JSON. Excel imports the first worksheet. Delimited text uses the first row as headers. JSON accepts an array of objects or `{ rows: [...] }`.

## Does GridNexa support charts?

Yes. Enable `toolbar={{ charts: true }}` or use the `charts` prop. Implemented types include bar, line, area, pie, donut, scatter, bubble, radar, radial bar, histogram, box plot, treemap, gauge, funnel, and combo charts. Charts can be downloaded as PNG.

## What is Data Health?

Data Health profiles visible columns for missing values, duplicates, validation failures, numeric outliers, top values, completeness, and quality scores. Selecting an issue filters to affected rows and focuses the first matching cell.

## Does GridNexa support undo, fill, and clipboard operations?

Yes. Use `enableUndoRedo`, `enableFillHandle`, and `enableRangeSelection`. Toolbar actions support copying, Excel-compatible range paste, bulk editing, and find and replace.

## What is Change Review?

`changeReview` tracks edits, additions, and deletions before Save All. Combine it with validation and `blockSave` for review-oriented workflows.

## Can GridNexa persist state?

Yes. `stateStorage` persists selected UI-state slices such as columns, filters, sort, pagination, and side-panel state. It does not persist row data. Saved views use a unique `views.key` and include a Default View.

## Can I export and import a repro snapshot?

Yes. Enable `diagnostics={{ recorder: true, exportRepro: true }}`. Export through the Diagnostics panel or `apiRef.current?.exportDiagnostics()`; import through the panel or command palette.

Snapshots may include sampled application rows, so review them before sharing.

## Is AI support tied to a provider?

No. The browser sends grid state to your configured server endpoint and receives a safe GridNexa action plan. Keep OpenAI, Azure OpenAI, Anthropic, Gemini, gateway, or local-model credentials on the server.

## Is GridNexa open source?

The packages are publicly distributed through npm. The implementation repository may remain private during active development. This repository provides public documentation, issue tracking, roadmap, and package information.

## How do I report a bug?

Open a GitHub issue with the package and version, framework version, browser, reproduction steps, screenshots, and a reviewed diagnostics snapshot when possible.
