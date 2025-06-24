# GitHub Copilot Instructions

## Project Overview

This is a Next.js + Tauri 2.0 template for building modern cross-platform desktop applications. Follow these instructions when generating code suggestions and completions.

## Core Technology Stack

Always use these specific versions and libraries:

- **Next.js 15** with App Router and Turbopack
- **React 19** with functional components and hooks
- **TypeScript 5** with strict mode enabled
- **Tauri 2.0** for desktop backend functionality
- **shadcn/ui** (New York style) for UI components
- **Tailwind CSS 4** for styling
- **Lucide React** for icons
- **Bun** as the preferred package manager (fallback to npm if needed)

## Code Generation Guidelines

### TypeScript Standards

- Always use strict TypeScript with explicit type annotations
- Prefer `interface` over `type` for object shapes
- Use `export type` for type-only exports
- Include JSDoc comments for complex functions
- Example:
```typescript
interface ComponentProps {
  title: string;
  onAction?: () => void;
}

export function Component({ title, onAction }: ComponentProps) {
  // Implementation
}
```

### React Component Patterns

- Use functional components with hooks exclusively
- Follow this component structure:
```typescript
interface ComponentNameProps {
  // Props definition
}

export function ComponentName({ ...props }: ComponentNameProps) {
  // 1. Hooks (useState, useEffect, etc.)
  // 2. Event handlers (handleClick, handleSubmit)
  // 3. Render logic
  return (
    // JSX
  );
}
```

- Event handler naming: `handle` + action (e.g., `handleClick`, `handleSubmit`)
- Use `React.memo` for performance optimization when appropriate
- Leverage `useMemo` and `useCallback` for expensive computations

### Project Structure and Imports

Use these path aliases consistently:
- `@/components/` for reusable components
- `@/components/ui/` for shadcn/ui components
- `@/lib/` for utilities and configurations
- `@/types/` for type definitions
- `@/hooks/` for custom hooks
- `@/app/` for Next.js App Router pages

Example imports:
```typescript
import { Button } from "@/components/ui/button";
import { cn } from "@/lib/utils";
import type { UserData } from "@/types/user";
```

### UI and Styling Guidelines

#### shadcn/ui Components
- Always use shadcn/ui components from `@/components/ui/`
- Follow New York style conventions
- Use the `cn()` function for className merging:
```typescript
import { cn } from "@/lib/utils";

<div className={cn("base-styles", "conditional-styles", className)} />
```

#### Tailwind CSS
- Use Tailwind utility classes exclusively
- Follow mobile-first responsive design
- Support both light and dark themes
- Use CSS variables for theme customization
- Example:
```typescript
<div className="flex items-center justify-between p-4 bg-background text-foreground dark:bg-dark-background">
```

#### Icons
- Use Lucide React icons exclusively
- Import icons individually:
```typescript
import { Home, Settings, User } from "lucide-react";
```

### Tauri Integration

#### Frontend API Calls
- Use `@tauri-apps/api` for backend communication
- Always handle errors properly:
```typescript
import { invoke } from "@tauri-apps/api/tauri";

try {
  const result = await invoke<string>("greet", { name: "User" });
  // Handle success
} catch (error) {
  console.error("Tauri command failed:", error);
  // Handle error
}
```

#### Rust Backend Commands
- Use `#[tauri::command]` for command definitions
- Return `Result<T, String>` for error handling
- Follow Rust naming conventions (snake_case)
- Example:
```rust
#[tauri::command]
async fn process_data(input: String) -> Result<String, String> {
    // Implementation
    Ok(result)
}
```

### Performance and Optimization

- Use Next.js `Image` component for images
- Implement proper loading states and error boundaries
- Use `loading.tsx` and `error.tsx` in App Router
- Leverage Server Components where appropriate
- Implement code splitting with dynamic imports

### Development Scripts

Generate code that works with these commands:
- `bun run dev` or `npm run dev` - Next.js development
- `cargo tauri dev` - Full desktop app development  
- `cargo tauri build` - Production build
- `bun run lint` or `npm run lint` - Code linting

### Error Handling and User Experience

- Always include proper error boundaries
- Provide user-friendly error messages
- Implement loading states for async operations
- Use proper TypeScript error types
- Example:
```typescript
const [loading, setLoading] = useState(false);
const [error, setError] = useState<string | null>(null);

const handleAction = async () => {
  setLoading(true);
  setError(null);
  try {
    await someAsyncOperation();
  } catch (err) {
    setError(err instanceof Error ? err.message : 'An error occurred');
  } finally {
    setLoading(false);
  }
};
```

### Security and Best Practices

- Validate all user inputs
- Use proper TypeScript types for API responses
- Follow Tauri security guidelines for capabilities
- Implement proper access controls for sensitive operations
- Never expose sensitive data in frontend code

### Accessibility

- Use semantic HTML elements
- Include proper ARIA labels and roles
- Ensure keyboard navigation support
- Maintain proper color contrast ratios
- Support screen readers

## Code Quality Standards

- Write self-documenting code with clear variable names
- Add comments for complex business logic
- Maintain consistent formatting (ESLint will handle this)
- Follow the principle of least privilege for Tauri capabilities
- Prioritize type safety and runtime safety

## File Naming Conventions

- Components: `PascalCase.tsx`
- Utilities: `kebab-case.ts`
- Pages: App Router structure (`page.tsx`, `layout.tsx`)
- Types: `kebab-case.types.ts`

When generating code, always consider these guidelines to ensure consistency with the project's architecture and maintainability standards.