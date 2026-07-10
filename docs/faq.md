
# FAQ

## What is GridNexa?

GridNexa is a developer-first Excel-like data grid for React, Vue, Angular, and JavaScript.

It includes editing, filtering, undo/redo, fill handle, export, saved views, change review, validation, diagnostics, and repro export.

## Is GridNexa open source?

GridNexa packages are distributed through npm. The source repository may be private while the project is in active development.

This public repository is used for documentation, feedback, issues, roadmap, and package information.

## Which frameworks are supported?

GridNexa supports:

- React
- Vue
- Angular
- vanilla JavaScript

## Which package should I install?

React:

```bash
pnpm add @gridnexa/react
```

Vue:

```bash
pnpm add @gridnexa/vue
```

Angular:

```bash
pnpm add @gridnexa/angular
```

JavaScript:

```bash
pnpm add @gridnexa/javascript
```

## Do I need to import CSS?

Recommended:

```ts
import "@gridnexa/react/index.css";
```

React also includes runtime style injection for core layout behavior, but importing CSS is still recommended for predictable production styling.

## Does GridNexa support dark mode?

Yes.

```tsx
<GridNexa theme="dark" />
```

Supported themes:

- `light`
- `dark`
- `system`

## Does GridNexa support undo and redo?

Yes.

```tsx
<GridNexa enableUndoRedo toolbar={{ undoRedo: true }} />
```

## Does GridNexa support Excel-like fill handle?

Yes.

```tsx
<GridNexa enableFillHandle toolbar={{ fill: true }} />
```

## Does GridNexa support export?

Yes.

```tsx
<GridNexa
  toolbar={{
    exportCsv: true,
    exportExcel: true
  }}
/>
```

## What is Change Review?

Change Review tracks edits, row additions, and row deletions before Save All.

```tsx
<GridNexa changeReview />
```

It is useful for admin tools, review workflows, finance tools, and business operations screens.

## What is Repro Recorder?

Repro Recorder exports a JSON snapshot of the current grid state.

```tsx
<GridNexa
  diagnostics={{
    recorder: true,
    exportRepro: true
  }}
/>
```

It helps developers reproduce bugs faster.

## Can I import a repro JSON?

Not directly yet.

You can manually use:

```tsx
<GridNexa
  columns={repro.columns}
  rows={repro.rows}
/>
```

Direct repro import may be added later.

## Is GridNexa good for internal tools?

Yes. GridNexa is especially useful for:

- admin panels
- dashboards
- internal tools
- CRM screens
- finance review tools
- editable business tables

## Is GridNexa a replacement for AG Grid?

GridNexa is an alternative for teams that want a simpler, app-focused, multi-framework grid with built-in productivity and diagnostics features.

AG Grid is very mature and has a broad enterprise feature set. GridNexa focuses on developer experience and common app workflows.

## Is GridNexa a replacement for TanStack Table?

GridNexa is different.

TanStack Table is headless. GridNexa includes the UI and grid workflows out of the box.

Use TanStack Table if you want full control and want to build the UI yourself.

Use GridNexa if you want a ready-to-use app grid.

## How do I report a bug?

Open a GitHub issue and include:

- package name
- package version
- framework version
- browser
- steps to reproduce
- screenshots
- diagnostics repro JSON if possible

## What should I include in feature requests?

Please include:

- the problem
- expected behavior
- framework
- example use case
- screenshots or mockups if available
