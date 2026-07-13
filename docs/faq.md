# FAQ

## What is GridNexa?

GridNexa is an Excel-style data grid for React, Vue, Angular, and JavaScript. It includes editing, import/export, charts, generated dashboards, filtering, grouping, pivoting, Data Health, Trust Mode, collaboration, saved views, validation, accessibility, advanced styling, diagnostics, and repro snapshot import/export.

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

Built-in theme values are `modern-light`, `modern-dark`, `compact`, `minimal`, `enterprise`, `high-contrast`, `light`, `dark`, and `system`. Density controls, typed styling tokens, slot overrides, CSS variables, stable class names, custom icons, class callbacks, and `unstyled` mode support deeper customization.

## Can I style individual columns and control long text?

Yes. Columns accept `headerStyle` and `cellStyle`, including callback-based cell styles. Use `textDisplay` globally or per column for `ellipsis`, `clip`, or `wrap`, optional native tooltips, and line clamping.

## Which files can GridNexa import?

The import toolbar accepts Excel `.xlsx`/`.xls`, CSV, TSV, TXT, and JSON. Excel imports the first worksheet. Delimited text uses the first row as headers. JSON accepts an array of objects or `{ rows: [...] }`.

## Does GridNexa support charts?

Yes. Enable `toolbar={{ charts: true }}` or use the `charts` prop. Implemented types include bar, line, area, pie, donut, scatter, bubble, radar, radial bar, histogram, box plot, treemap, gauge, funnel, and combo charts. Charts can be downloaded as PNG.

## What is Data Health?

Data Health profiles visible columns for missing values, duplicates, validation failures, numeric outliers, top values, completeness, and quality scores. Selecting an issue filters to affected rows and focuses the first matching cell.

## What is Trust Mode?

Trust Mode explains the active value by showing its source, validation status, Data Health evidence, likely downstream impact, recent edit history, and a rollback action for the latest tracked edit.

## What does Dashboard Generator create?

Dashboard Generator analyzes visible rows and columns to create KPI cards, inferred summaries, configured dashboard charts, and insight notes. Configured charts support bar, line, area, pie, and donut types and update as visible data changes.

## Does GridNexa support realtime collaboration?

Yes. The `collaboration` prop accepts an application-owned provider and user identity. It supports cell-change events, presence badges, cell locks, and conflict modes, so applications can connect Socket.IO, WebSocket, Supabase Realtime, Firebase, Yjs, or an internal event bus.

## Is GridNexa keyboard accessible?

GridNexa supplies grid, row-group, and grid-cell semantics, active-cell announcements, and roving focus. It supports arrow and range navigation, Home/End, Ctrl/Cmd+Home/End, Page Up/Down, Enter/F2 editing, Escape cancellation, and Ctrl/Cmd+C copying.

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
