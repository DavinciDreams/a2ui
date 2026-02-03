# @deepagents/a2ui

Pre-approved React components for Agent-to-User Interface protocol.

## Overview

This package provides a collection of 13 pre-approved React components designed for use with the Microsoft A2UI (Agent-to-User Interface) protocol. These components are safe for agent-generated UI rendering and follow a declarative, component-based approach.

## Installation

```bash
npm install @deepagents/a2ui
```

## Peer Dependencies

This package requires `react@^18.0.0 || ^19.0.0` and `react-dom@^18.0.0 || ^19.0.0` as peer dependencies. You must have React installed in your project:

```bash
npm install react react-dom @deepagents/a2ui
```

## Usage

### Basic Usage

```typescript
import { Button, Card, Text } from "@deepagents/a2ui";

function MyComponent() {
  return (
    <Card title="Welcome" subtitle="Agent Interface">
      <Text content="Hello from the agent!" variant="body" />
      <Button 
        label="Click Me" 
        variant="primary" 
        action="handleClick"
      />
    </Card>
  );
}
```

### Importing Styles

```typescript
// Import the CSS file in your application entry point
import "@deepagents/a2ui/styles";
```

## Component Catalog

### Display Components

| Component | Props | Description |
|-----------|-------|-------------|
| `Button` | `label`, `variant`, `disabled`, `action`, `onEvent` | Interactive button with variants (primary, secondary, text) |
| `Card` | `title`, `subtitle`, `variant`, `children` | Container with optional header and variants (default, elevated, outlined) |
| `Code` | `language`, `content`, `filename` | Syntax-highlighted code block |
| `Container` | `maxWidth`, `padding`, `children` | Responsive container for layout |
| `Divider` | `variant`, `thickness` | Visual separator |
| `Text` | `content`, `variant`, `color` | Text display with variants (heading, body, caption) |

### Input Components

| Component | Props | Description |
|-----------|-------|-------------|
| `Input` | `label`, `value`, `onChange`, `type` | Form input field |

### Data Components

| Component | Props | Description |
|-----------|-------|-------------|
| `List` | `items`, `variant`, `ordered` | List component (ordered or unordered) |
| `Table` | `columns`, `rows`, `variant` | Data table with customizable styling |

### Feedback Components

| Component | Props | Description |
|-----------|-------|-------------|
| `Markdown` | `content`, `className` | Markdown renderer |
| `Progress` | `value`, `max`, `variant` | Progress indicator |
| `Spinner` | `size`, `color` | Loading spinner |
| `Status` | `status`, `message` | Status indicator (success, warning, error, info) |

### Special Components

| Component | Props | Description |
|-----------|-------|-------------|
| `A2UIRenderer` | `components`, `onEvent` | Renders A2UI component trees |

## Component Props

### Button

```typescript
interface ButtonProps {
  label: string;
  variant?: "primary" | "secondary" | "text";
  disabled?: boolean;
  action?: string;
  onEvent?: (eventId: string, data: unknown) => void;
  children?: React.ReactNode;
}
```

### Card

```typescript
interface CardProps {
  title?: string;
  subtitle?: string;
  variant?: "default" | "elevated" | "outlined";
  children?: React.ReactNode;
}
```

### Code

```typescript
interface CodeProps {
  language: string;
  content: string;
  filename?: string;
}
```

### Container

```typescript
interface ContainerProps {
  maxWidth?: "sm" | "md" | "lg" | "xl" | "full";
  padding?: "none" | "sm" | "md" | "lg";
  children?: React.ReactNode;
}
```

### Divider

```typescript
interface DividerProps {
  variant?: "horizontal" | "vertical";
  thickness?: "thin" | "medium" | "thick";
}
```

### Input

```typescript
interface InputProps {
  label?: string;
  value?: string;
  onChange?: (value: string) => void;
  type?: "text" | "email" | "password" | "number";
  placeholder?: string;
}
```

### List

```typescript
interface ListProps {
  items: string[];
  variant?: "bullet" | "numbered" | "none";
  ordered?: boolean;
}
```

### Markdown

```typescript
interface MarkdownProps {
  content: string;
  className?: string;
}
```

### Progress

```typescript
interface ProgressProps {
  value: number;
  max?: number;
  variant?: "bar" | "circular" | "dots";
}
```

### Spinner

```typescript
interface SpinnerProps {
  size?: "sm" | "md" | "lg";
  color?: "primary" | "secondary" | "white";
}
```

### Status

```typescript
interface StatusProps {
  status: "success" | "warning" | "error" | "info";
  message?: string;
}
```

### Table

```typescript
interface TableProps {
  columns: Array<{ key: string; label: string }>;
  rows: Array<Record<string, unknown>>;
  variant?: "default" | "striped" | "bordered";
}
```

### Text

```typescript
interface TextProps {
  content: string;
  variant?: "heading" | "subheading" | "body" | "caption";
  color?: "primary" | "secondary" | "muted";
}
```

### A2UIRenderer

```typescript
interface A2UIRendererProps {
  components: A2UIComponent[];
  onEvent?: (eventId: string, data: unknown) => void;
}
```

## Styling

Components use Tailwind CSS for styling. Import the styles in your application:

```typescript
import "@deepagents/a2ui/styles";
```

Or customize by extending the Tailwind configuration:

```javascript
// tailwind.config.js
module.exports = {
  content: [
    "./node_modules/@deepagents/a2ui/dist/**/*.{js,ts,jsx,tsx}",
  ],
  // ... your config
};
```

## Examples

### Simple Card with Button

```typescript
import { Card, Button, Text } from "@deepagents/a2ui";

function WelcomeCard() {
  return (
    <Card title="Welcome" subtitle="Agent Interface">
      <Text content="Hello from the agent!" variant="body" />
      <Button 
        label="Get Started" 
        variant="primary" 
        action="start"
      />
    </Card>
  );
}
```

### Code Display

```typescript
import { Card, Code } from "@deepagents/a2ui";

function CodeExample() {
  const code = `
    function hello() {
      console.log("Hello, World!");
    }
  `;

  return (
    <Card title="Generated Code">
      <Code 
        language="javascript" 
        content={code} 
        filename="example.js" 
      />
    </Card>
  );
}
```

### Status Indicator

```typescript
import { Status, Card } from "@deepagents/a2ui";

function StatusExample() {
  return (
    <Card>
      <Status 
        status="success" 
        message="Agent completed successfully" 
      />
    </Card>
  );
}
```

## License

MIT

## Repository

[https://github.com/DavinciDreams/a2ui](https://github.com/DavinciDreams/a2ui)
