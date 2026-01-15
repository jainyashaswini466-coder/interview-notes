#### ⚛️ React Fundamentals

1. [What is React?](#q1-what-is-react)
2. [What is a Single Page Application (SPA)?](#q2-what-is-a-single-page-application-spa)
3. [What are components in React and how are they useful?](#q3-what-are-components-in-react-and-how-are-they-useful)
4. [What is JSX and why is it used in React?](#q4-what-is-jsx-and-why-is-it-used-in-react)
5. [What are props and state? (Difference)](#q5-what-are-props-and-state-difference)

---

## Part 1: Read-Aloud Interview Questions

### Q1: What is React?

- **JavaScript library** used to build **fast, scalable user interfaces**
- Primarily used for **single-page applications**
- Maintained by **Facebook (Meta)** and focuses on the **View layer of MVC**
- Follows **component-based architecture** for **reusability and separation of concerns**
- Uses **Virtual DOM** with **efficient diffing** for optimized **performance**
- Implements **declarative UI** and **unidirectional data flow** for **predictable state management**

---

### Q2: What is a Single Page Application (SPA)?

- Web application that loads a **single HTML page once**
- UI updates happen via **JavaScript without full page reload**
- Uses **client-side rendering** and **asynchronous API calls**
- Enables **smooth navigation** and **better user experience**
- Reduces **server load** and provides **app-like behavior**

Initial Load → index.html
↓
JavaScript Bundle
↓
Component Rendering
↓
API Calls + UI Updates

---

### Q3: What are components in React and how are they useful?

- **Independent and reusable UI building blocks**
- Encapsulate **logic, state, and presentation** in a single unit
- Support **modular and scalable application architecture**
- Can be **nested, reused, and composed**
- Improve **code readability, testing, and maintainability**

Root Component
↓
Parent Component
↓
Child Components

### Q4: What is JSX and why is it used in React?

- **JSX (JavaScript XML)** allows writing **HTML-like syntax inside JavaScript**
- Improves **readability and maintainability** of UI code
- Transpiled by **Babel** into standard JavaScript
- Encourages **declarative UI development**
- Enables **compile-time error checking**

JSX Syntax
↓ (Babel)
JavaScript Code
↓
Virtual DOM
↓
Real DOM

---

### Q5: What are props and state? (Difference)

- **Props** are **read-only data** passed from **parent to child components**
- Props support **unidirectional data flow** and **component reusability**
- **State** represents **mutable internal data** managed within a component
- State changes trigger **re-rendering** of the UI
- Props are **externally controlled**, while state is **internally managed**

Parent Component
↓ (Props)
Child Component
↓
Internal State

### Q6: What is the difference between class components and functional components?

## Key Differences

| Aspect         | Class Components                                       | Functional Components           |
| -------------- | ------------------------------------------------------ | ------------------------------- |
| Definition     | ES6 classes extending `React.Component`                | Simple JavaScript functions     |
| JSX Return     | Uses `render()` method                                 | Returns JSX directly            |
| State          | `this.state`, `this.setState()`                        | Hooks like `useState()`         |
| Lifecycle      | Separate lifecycle methods (`componentDidMount`, etc.) | `useEffect()` handles lifecycle |
| `this` keyword | Required                                               | Not used                        |
| Code Size      | More boilerplate                                       | Less, cleaner                   |
| Performance    | Slightly heavier                                       | Better & optimized              |
| Reusability    | Harder                                                 | Easier with hooks               |
| Testing        | Slightly complex                                       | Easier                          |
| Current Use    | Legacy / older code                                    | Modern & recommended            |

### Q7: What are React Hooks?

**React Hooks** are special functions that let you use **state**, **lifecycle features**, and **other React features** inside **functional components**, without writing class components.
Introduced in **React 16.8**.

---

## Why Hooks?

Before Hooks:

- State & lifecycle logic required **class components**
- Code was harder to reuse and manage

With Hooks:

- Use state in functional components
- Reuse logic easily
- Cleaner and simpler code


### Q8. Explain useState, useEffect, useLayoutEffect, useMemo, useCallback, useRef?

### commonly Used React Hooks :

#### 1. `usestate`

- used to manage state in a functional component.

#### 2. `useEffect`

- used to handle side effects
- work like lifecycle methods :
  - componetDidMount
  - componetDidUpdate
  - componetWillUnmount

#### 3. `useLayoutEffect`

- Works like `useEffect` but runs **synchronously**
- Executes **after DOM updates but before browser paint**
- Blocks visual rendering until finished

**Used for:** DOM measurements, layout changes
### 4. `useMemo`

- Used to optimize performance
- Memoizes expensive calculations

## 5. useCallback
- Used to **memoize functions**
- Prevents function re-creation on each render

**Used for:** passing callbacks to child components
## Quick Comparison Table

| Hook | Purpose | Causes Re-render |
|-----|--------|----------------|
| useState | Manage state | Yes |
| useEffect | Side effects | Depends |
| useLayoutEffect | DOM-related side effects | Yes |
| useMemo | Memoize values | No |
| useCallback | Memoize functions | No |
| useRef | Store mutable value / DOM | No |

### Q9. What are custom hooks and when to use them?
**Custom Hooks** are **user-defined functions** in React that allow you to **reuse stateful logic** across multiple components.

- They are normal JavaScript functions
- Their name **must start with `use`**
- They can use other React Hooks inside them

## Why Custom Hooks?
Without custom hooks:
- Logic is duplicated across components
- Components become large and hard to manage

With custom hooks:
- Logic becomes reusable
- Components stay clean and readable
- Easier maintenance

### Q10. Explain React.memo and how it helps in optimization?
`React.memo` is used to **prevent unnecessary re-renders** of functional components.

## How it works?
- Re-renders component **only if props change**
- Uses **shallow comparison** of props
## Why use it?
- Parent re-render ≠ Child re-render
- Improves performance

## Use when
- Component is heavy
- Props stay same most of the time

### Q11. Explain React.memo and how it helps in optimization?

Context API is used to **share data globally** in a React app **without prop drilling**.

## Why use it?
- Avoid passing props manually at every level
- Clean and centralized state sharing

## How to integrate (Steps)
1. **Create Context** using `createContext()`
2. **Provide data** using `<Context.Provider>`
3. **Consume data** using `useContext()`

## When to use
- Global data like auth, theme, language, user info

### Q12. What is prop drilling and how to avoid it?
Prop drilling is the process of **passing data through multiple component levels** even when intermediate components don’t need it.
## Why is it a problem?
- Makes code messy
- Hard to maintain
- Reduces readability
## How to avoid it?
- **Context API**
- **State management libraries** (Redux, Zustand)
- **Component composition**

### Q13. What is prop drilling and how to avoid it?
# Lazy Loading (React)

## When to use Lazy Loading?
- Large applications
- Heavy components or pages
- Routes not needed at initial load

## Why use it?
- Reduces initial bundle size
- Faster page load
- Better performance

## How to use Lazy Loading?
- Use `React.lazy()` to load components dynamically
- Wrap with `<Suspense>` for fallback UI

## Common use case
- Route-based code splittingy

### Q14. What is prop drilling and how to avoid it?
Virtual DOM is a **lightweight copy of the real DOM** stored in memory by React.

## Why Virtual DOM?
- Real DOM updates are slow
- Virtual DOM makes updates faster and efficient

## How it works?
- React updates Virtual DOM first
- Compares with previous Virtual DOM (diffing)
- Updates only changed parts in real DOM

## Benefit
- Faster rendering
- Better performance

### Q15. What is reconciliation in React (how React updates DOM)?
Reconciliation is the process by which **React updates the real DOM efficiently** when state or props change.

## How React updates DOM?
1. State/props change
2. New Virtual DOM is created
3. React compares old & new Virtual DOM (diffing)
4. Only changed elements are updated in real DOM

## Why it matters?
- Minimizes DOM operations
- Improves performance

### Q16. How to route between pages in React?
Routing allows **navigating between different pages/components** in a React app without reloading the page.

## How to implement?
1. **Install React Router**
```bash
npm install react-router-dom
```
### Q17. What are error boundaries in React?
Error Boundaries are **React components that catch JavaScript errors** in their child component tree and **prevent the entire app from crashing**.

- Catch errors in **render, lifecycle methods, and constructors** of child components
- Show **fallback UI** instead of broken components

## How to create?
```jsx
class ErrorBoundary extends React.Component {
    constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    console.log(error, info);
  }

  render() {
      if (this.state.hasError) {
          return <h2>Something went wrong.</h2>;
    }
    return this.props.children;
  }
}
```

##### Usage : 
```
<ErrorBoundary>
  <MyComponent />
</ErrorBoundary>
``` 
#### Limitations 
- Only class components can be error boundaries (functional components cannot, unless using libraries like react-error-boundary)
- Does not catch errors in event handlers

### Q18. What are controlled and uncontrolled components?


## Controlled Components
- Form inputs **controlled by React state**
- Value of input comes from `state`
- Updates via `onChange` handler

**Example:**
```jsx
const [name, setName] = useState("");
<input value={name} onChange={(e) => setName(e.target.value)} />
```
## Uncontrolled Components
- Form inputs managed by DOM, not React state
- Access value using ref

```
const nameRef = useRef();
<input ref={nameRef} />
```
### Q19. What are keys in lists and why are they important?
Keys are **unique identifiers** assigned to elements in a list when rendering with `.map()`.

**Example:**
```jsx
const items = ['A', 'B', 'C'];
<ul>
  {items.map((item, index) => (
      <li key={index}>{item}</li>
  ))}
</ul>
```
### Q20.What is React Fragment and why is it used?
`React.Fragment` is a wrapper that lets you **group multiple elements** without adding extra nodes to the DOM.

**Example:**
```jsx
<React.Fragment>
  <h1>Title</h1>
  <p>Paragraph</p>
</React.Fragment>
