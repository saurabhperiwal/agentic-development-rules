---
globs: ["apps/admin/**/*.tsx", "apps/admin/**/*.ts"]
---

# React/Next.js Frontend Standards

## Component Design
- One component per file
- Prefer functional components with hooks
- Extract reusable logic into custom hooks
- Keep components under 200 lines — split if larger
- Props interface defined for every component (no `any`)

## State Management
- Local state: `useState` for component-scoped
- Server state: React Query (`useQuery`, `useMutation`)
- Global state: Zustand (only when truly shared across distant components)
- URL state: search params for filters, pagination
- Avoid prop drilling > 2 levels deep — use context or composition

## Type Safety
- Define interfaces for all props, API responses, and state
- No `any` — use `unknown` and narrow with type guards if needed
- Type API responses from the backend (shared types in `packages/shared`)

## Performance
- Memoize expensive computations with `useMemo`
- Memoize callbacks passed to children with `useCallback`
- Lazy load routes and heavy components with `dynamic()`
- Use `loading="lazy"` on images
- Debounce search inputs and frequent state updates

## Error Handling
- Error boundaries for graceful failure recovery
- Handle loading, error, and empty states in every data-fetching component
- Show user-friendly error messages — never raw error strings
- Toast notifications for async operation results (success/failure)

## Forms
- Controlled inputs with proper validation before submit
- Disable submit button while mutation is in progress
- Show inline validation errors
- Clear form state on successful submit

## Accessibility
- Semantic HTML elements (`button`, `a`, `nav`, `main`)
- `aria-label` on icon-only buttons
- Keyboard navigable interactive elements
- Color contrast requirements met
