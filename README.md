# React Router — Master Notes

## Table of Contents

- [React Router — Introduction](#react-router-introduction)
  - [Definition](#definition)
  - [Core Terms (Route, Path, Element, Component)](#core-terms-route-path-element-component)
  - [Installation](#installation)
  - [Imports](#imports)
  - [Working of BrowserRouter, Routes, and Route](#working-of-browserrouter-routes-and-route)
  - [Simple Example](#simple-example)
  - [Line-by-Line Explanation](#line-by-line-explanation)
  - [What Happens When You Click a Link?](#what-happens-when-you-click-a-link)
  - [Quick Recap Table](#quick-recap-table)
- [Link and NavLink](#link-and-navlink)
  - [Definition](#definition-1)
  - [Core Terms](#core-terms)
  - [Imports](#imports-1)
  - [Working of Link](#working-of-link)
  - [Simple Example — Using `Link`](#simple-example-using-link)
  - [Line-by-Line Explanation](#line-by-line-explanation-1)
  - [Working of NavLink](#working-of-navlink)
  - [Simple Example — Using `NavLink`](#simple-example-using-navlink)
  - [Line-by-Line Explanation](#line-by-line-explanation-2)
  - [What Happens When You Click a NavLink?](#what-happens-when-you-click-a-navlink)
  - [Comparison Table: Link vs NavLink](#comparison-table-link-vs-navlink)
- [Dynamic Routes and useParams](#dynamic-routes-and-useparams)
  - [Definition](#definition-2)
  - [Core Terms](#core-terms-1)
  - [Imports](#imports-2)
  - [Working of Dynamic Routes and useParams](#working-of-dynamic-routes-and-useparams)
  - [Small Project: Product Details Page](#small-project-product-details-page)
  - [Line-by-Line Explanation](#line-by-line-explanation-3)
  - [What Happens When You Click a Product?](#what-happens-when-you-click-a-product)
  - [Quick Recap Table](#quick-recap-table-1)
- [Nested Routes, Index Route, and Outlet](#nested-routes-index-route-and-outlet)
  - [Definition](#definition-3)
  - [Core Terms](#core-terms-2)
  - [Imports](#imports-3)
  - [Working of Nested Routes, Index Route, and Outlet](#working-of-nested-routes-index-route-and-outlet)
  - [Small Project: Dashboard with Nested Routes](#small-project-dashboard-with-nested-routes)
  - [Line-by-Line Explanation](#line-by-line-explanation-4)
  - [What Happens When You Click "Profile"?](#what-happens-when-you-click-profile)
  - [Quick Recap Table](#quick-recap-table-2)
- [useNavigate and Navigate](#usenavigate-and-navigate)
  - [Definition](#definition-4)
  - [Core Terms](#core-terms-3)
  - [Imports](#imports-4)
  - [Working of useNavigate](#working-of-usenavigate)
  - [Working of Navigate](#working-of-navigate)
  - [Small Project: Login Page with Redirect and Protected Route](#small-project-login-page-with-redirect-and-protected-route)
  - [Line-by-Line Explanation](#line-by-line-explanation-5)
  - [What Happens When You Log In?](#what-happens-when-you-log-in)
  - [What Happens If Someone Visits `/dashboard` Directly Without Logging In?](#what-happens-if-someone-visits-dashboard-directly-without-logging-in)
  - [Quick Recap Table](#quick-recap-table-3)
- [Query Strings & React Router — Notes](#query-strings-react-router-notes)
  - [1. What is a Query String?](#1-what-is-a-query-string)
  - [2. Why Do We Need Query Strings? *(Main Concept)*](#2-why-do-we-need-query-strings-main-concept)
  - [3. Basic Query String Syntax](#3-basic-query-string-syntax)
  - [4. IMPORTANT: Parameter Names Are NOT Fixed/Special](#4-important-parameter-names-are-not-fixedspecial)
  - [5. Who Decides the Parameter Names? *(Big Topic — Highlighted)*](#5-who-decides-the-parameter-names-big-topic-highlighted)
  - [6. React Router: `useSearchParams()` Hook](#6-react-router-usesearchparams-hook)
  - [7. Reading Query Parameters](#7-reading-query-parameters)
  - [8. Changing Query Parameters](#8-changing-query-parameters)
  - [9. Quick Reference: `?` vs `&`](#9-quick-reference-vs)
  - [Summary](#summary)
- [useLocation](#uselocation)
  - [Definition](#definition-5)
  - [Core Terms](#core-terms-4)
  - [Imports](#imports-5)
  - [Working of useLocation](#working-of-uselocation)
  - [Detailed Look at Each Property](#detailed-look-at-each-property)
  - [Small Project: "Remember Where You Came From" Redirect](#small-project-remember-where-you-came-from-redirect)
  - [Line-by-Line Explanation](#line-by-line-explanation-6)
  - [What Happens Step by Step?](#what-happens-step-by-step)
  - [Quick Recap Table](#quick-recap-table-4)
  - [Comparison Table: useLocation vs useParams vs useNavigate](#comparison-table-uselocation-vs-useparams-vs-usenavigate)
- [useSearchParams](#usesearchparams)
  - [Definition](#definition-6)
  - [Core Terms](#core-terms-5)
  - [Imports](#imports-6)
  - [Working of useSearchParams](#working-of-usesearchparams)
  - [Detailed Look at Reading Values](#detailed-look-at-reading-values)
  - [Detailed Look at Updating Values](#detailed-look-at-updating-values)
  - [Pagination with useSearchParams](#pagination-with-usesearchparams)
  - [Small Project: Product Filter with URL-Synced Search Params](#small-project-product-filter-with-url-synced-search-params)
  - [Line-by-Line Explanation](#line-by-line-explanation-7)
  - [What Happens When You Change the Category Dropdown?](#what-happens-when-you-change-the-category-dropdown)
  - [Quick Recap Table](#quick-recap-table-5)
  - [Comparison Table: useSearchParams vs useLocation](#comparison-table-usesearchparams-vs-uselocation)
- [Protected Routes (React Router)](#protected-routes-react-router)
  - [Definition](#definition-7)
  - [Core Terms](#core-terms-6)
  - [Imports](#imports-7)
  - [How Protected Routes Work](#how-protected-routes-work)
  - [Small Project: Multi-Page App with Protected Routes](#small-project-multi-page-app-with-protected-routes)
  - [Line-by-Line Explanation](#line-by-line-explanation-8)
  - [What Happens Step by Step?](#what-happens-step-by-step-1)
  - [Extending the Pattern: Role-Based Protected Routes](#extending-the-pattern-role-based-protected-routes)
  - [Quick Recap Table](#quick-recap-table-6)
  - [Step 7 — Complete Protected Route Structure (Context-Based Auth)](#step-7-complete-protected-route-structure-context-based-auth)

---

## React Router — Introduction

### Definition

**React Router** is a JavaScript library used with React that allows you to build **Single Page Applications (SPAs)** with multiple "pages" or "views" — without actually reloading the browser.

- Normally, in a website, clicking a link loads a completely new HTML page from the server.
- In React apps, we don't want that — we want fast navigation without a full page reload.
- React Router solves this by **changing the URL** and **swapping which component is displayed**, all on the client side (in the browser), without contacting the server again.

> React Router lets you show different components based on the URL, while keeping the app feeling like a normal multi-page website.

### Core Terms (Route, Path, Element, Component)

| Term | Meaning |
|------|---------|
| **Route** | A single mapping between a URL path and the component that should be shown for that path. Think of it as one "rule": *"if the URL looks like this, show this component."* |
| **Path** | The actual URL pattern you want to match, e.g. `/`, `/about`, `/contact`, `/products/:id`. It's a string that tells React Router *when* a route should activate. |
| **Element** | The actual React component (in JSX form) that should be rendered when the path matches. Example: `<About />`. |
| **Component** | A normal React function (or class) that returns JSX — the actual UI you want to display, like `Home`, `About`, `Contact`. |

**Simple analogy:** Think of a route like a signboard at a junction:
- **Path** = the direction written on the signboard (e.g., "Turn left for Library")
- **Element/Component** = the actual place you reach (the Library itself)
- **Route** = the whole signboard rule connecting the direction to the destination

### Installation

React Router is not included in React by default — it is a **separate package** that must be installed.

**Step 1: Make sure you have a React project**

```bash
npm create vite@latest my-app
cd my-app
npm install
```

**Step 2: Install React Router**

```bash
npm install react-router-dom
```

> `react-router-dom` is used for **web applications** (browser-based). There is also `react-router-native` for React Native (mobile apps) — not covered here.

**Step 3: Verify installation** — check `package.json`:

```json
"dependencies": {
  "react-router-dom": "^6.x.x"
}
```

Every other topic in these notes builds on this same package — once installed here, no further installation is needed for `Link`, `NavLink`, `useParams`, nested routes, `useNavigate`, `Navigate`, `useLocation`, or `useSearchParams`.

### Imports

```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
```

| Import | Purpose |
|--------|---------|
| `BrowserRouter` | Wraps your entire app and enables routing using the browser's URL/history. It must be placed **once**, usually around your whole `App` component. |
| `Routes` | A container that holds all your individual `Route` elements. It looks at the current URL and decides which `Route` matches. |
| `Route` | Defines a single path-to-component mapping (path + element). |

Other commonly used imports (used later for navigation and dynamic routes):

```jsx
import { Link, NavLink, useParams, useNavigate } from "react-router-dom";
```

| Import | Purpose |
|--------|---------|
| `Link` | Used instead of `<a>` tags to navigate between routes without reloading the page. |
| `NavLink` | Same as `Link`, but automatically adds an "active" class/style when the link matches the current URL. |
| `useParams` | A hook to read dynamic values from the URL (e.g., an `id` in `/products/:id`). |
| `useNavigate` | A hook that lets you navigate programmatically (e.g., after form submission). |

*(We'll cover `Link` and `NavLink` properly in the **Link and NavLink** section right after this one, `useParams` in the **Dynamic Routes** section, and `useNavigate` in the **useNavigate and Navigate** section further below. For now, just know `Link`/`NavLink` are used for clickable navigation without a page reload, `useParams` reads values from the URL, and `useNavigate` lets you navigate from inside your code.)*

### Working of BrowserRouter, Routes, and Route

1. **`BrowserRouter`** — the outermost wrapper. It uses the browser's built-in history API to keep track of the URL. Without it, routing will not work at all.
2. **`Routes`** — acts like a `switch` statement. It looks at all the `Route` elements inside it and renders **only the one** whose `path` matches the current URL.
3. **`Route`** — Each `Route` defines:
   - `path` → the URL pattern to match
   - `element` → the component to show when that path matches

**Syntax:**

```jsx
<BrowserRouter>
  <Routes>
    <Route path="URL_PATH" element={<ComponentName />} />
  </Routes>
</BrowserRouter>
```

### Simple Example

**Step 1: Create simple page components**

```jsx
// Home.jsx
function Home() {
  return <h2>Welcome to the Home Page</h2>;
}
export default Home;
```

```jsx
// About.jsx
function About() {
  return <h2>This is the About Page</h2>;
}
export default About;
```

```jsx
// Contact.jsx
function Contact() {
  return <h2>Contact us at contact@example.com</h2>;
}
export default Contact;
```

**Step 2: Set up routing in `App.jsx`**

```jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";
import Home from "./Home";
import About from "./About";
import Contact from "./Contact";

function App() {
  return (
    <BrowserRouter>
      {/* Navigation links */}
      <nav>
        <Link to="/">Home</Link> | 
        <Link to="/about">About</Link> | 
        <Link to="/contact">Contact</Link>
      </nav>

      {/* Route definitions */}
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

### Line-by-Line Explanation

- `<BrowserRouter>` — wraps the whole app so routing works using the browser's URL.
- `<nav>...</nav>` — a normal navigation bar containing `Link` components.
- `<Link to="/">Home</Link>` — instead of `<a href="/">`, we use `Link` so the page does **not reload**. Clicking it just changes the URL and re-renders the matching route. *(We'll cover `Link` and `NavLink` properly in the Link and NavLink section right below — for now, just know `Link` replaces `<a>` tags for reload-free navigation.)*
- `<Routes>` — checks the current URL against all `Route` elements inside it.
- `<Route path="/" element={<Home />} />` — if the URL is exactly `/`, show the `Home` component.
- `<Route path="/about" element={<About />} />` — if the URL is `/about`, show the `About` component.
- `<Route path="/contact" element={<Contact />} />` — if the URL is `/contact`, show the `Contact` component.

### What Happens When You Click a Link?

1. User clicks `Link to="/about"`.
2. The browser's URL changes to `/about` **without reloading the page**.
3. `Routes` notices the URL has changed.
4. It checks each `Route`'s `path` one by one.
5. It finds `path="/about"` matches.
6. It renders the `element` for that route — in this case, `<About />`.

### Quick Recap Table

| Component | Role |
|-----------|------|
| `BrowserRouter` | Enables routing for the whole app (wraps everything) |
| `Routes` | Looks at the URL and picks the correct `Route` |
| `Route` | Defines one path → one component mapping |
| `Link` | Used to navigate between routes without page reload |

We already used `Link` briefly above to move between pages without a reload. Let's now look at `Link` — and its cousin `NavLink` — in full detail, including how to highlight the currently active page.

---

## Link and NavLink

### Definition

In a normal HTML website, we use the `<a>` tag to move between pages. But in React apps, using `<a>` causes the **entire page to reload**, which defeats the purpose of a Single Page Application (SPA). React Router provides two special components:

- **`Link`** — used to navigate between routes without reloading the page.
- **`NavLink`** — same as `Link`, but it can automatically detect and style the "active" link (the one matching the current URL).

> `Link` and `NavLink` are React Router's replacement for the `<a>` tag — they change the URL and swap components instantly, without a full page reload.

### Core Terms

| Term | Meaning |
|------|---------|
| **Link** | A component that renders a clickable navigation element (like an `<a>` tag) but only changes the route, without reloading the browser. |
| **NavLink** | A special version of `Link` that knows whether it is currently "active" (i.e., its `to` path matches the current URL) and lets you style it differently. |
| **`to` prop** | Used in both `Link` and `NavLink` to specify the destination path (similar to `href` in `<a>`). |
| **Active Link** | The link whose path matches the current URL — usually highlighted to show the user "you are here". |
| **`className` (as a function)** | In `NavLink`, `className` can accept a function that receives `{ isActive }` and returns the correct class name based on whether the link is active. |

**Simple analogy:** Think of a website's navigation bar like a set of tabs in a file folder:
- **`Link`** = a normal tab you can click to switch files
- **`NavLink`** = the same tab, but it automatically gets **highlighted** when it's the one currently open

### Imports

```jsx
import { Link, NavLink } from "react-router-dom";
```

| Import | Purpose |
|--------|---------|
| `Link` | Creates a clickable navigation element that changes the route without reloading the page. |
| `NavLink` | Same as `Link`, but also tells you (via `isActive`) whether the current link matches the active route, so you can style it. |

### Working of Link

1. `Link` renders an `<a>` tag behind the scenes, but it **intercepts the click**.
2. Instead of asking the browser to load a new page, it tells React Router to update the URL.
3. React Router's `Routes` then re-checks all `Route` elements and renders the one that matches the new URL.
4. The page **does not reload** — only the matching component changes.

**Syntax:**

```jsx
<Link to="/path">Link Text</Link>
```

### Simple Example — Using `Link`

```jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";
import Home from "./Home";
import About from "./About";

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link> | <Link to="/about">About</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

### Line-by-Line Explanation

- `<Link to="/">Home</Link>` and `<Link to="/about">About</Link>` — clicking either one changes the URL **without reloading the page**. *(As covered in the React Router — Introduction section above, this is how React Router avoids asking the server for a whole new page.)*
- `to="/"` and `to="/about"` work just like `href` in a normal `<a>` tag, but React Router handles the navigation internally.
- The `Routes` block automatically shows the correct component (`Home` or `About`) based on the new URL.

### Working of NavLink

1. `NavLink` behaves exactly like `Link` for navigation.
2. Additionally, React Router checks if the `to` path **matches the current URL**.
3. If it matches, `NavLink` marks itself as **active** — this can be used to apply a special class or style (like underlining or changing color).
4. This is very useful for building nav bars where you want to visually show the current page.

**Syntax:**

```jsx
<NavLink
  to="/path"
  className={({ isActive }) => (isActive ? "active-class" : "")}
>
  Link Text
</NavLink>
```

### Simple Example — Using `NavLink`

```jsx
import { BrowserRouter, Routes, Route, NavLink } from "react-router-dom";
import Home from "./Home";
import About from "./About";
import Contact from "./Contact";

function App() {
  return (
    <BrowserRouter>
      <nav>
        <NavLink
          to="/"
          className={({ isActive }) => (isActive ? "active-link" : "")}
        >
          Home
        </NavLink>
        {" | "}
        <NavLink
          to="/about"
          className={({ isActive }) => (isActive ? "active-link" : "")}
        >
          About
        </NavLink>
        {" | "}
        <NavLink
          to="/contact"
          className={({ isActive }) => (isActive ? "active-link" : "")}
        >
          Contact
        </NavLink>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

Add a small CSS rule to see the effect visually:

```css
.active-link {
  color: red;
  font-weight: bold;
  text-decoration: underline;
}
```

### Line-by-Line Explanation

- `to="/"` — the destination path, same as in `Link`.
- `className={({ isActive }) => (isActive ? "active-link" : "")}` — this is a function that React Router calls automatically.
  - `isActive` is `true` when the current URL matches this `NavLink`'s `to` path.
  - If `isActive` is `true`, the class `"active-link"` is applied.
  - If `isActive` is `false`, no special class is applied (empty string).
- Because of this, whichever page you are currently on will show its nav link highlighted in red and bold — thanks to the CSS class.

### What Happens When You Click a NavLink?

1. User clicks `NavLink to="/about"`.
2. URL changes to `/about` (no page reload).
3. React Router checks: does `/about` match this `NavLink`'s `to`? → Yes.
4. `isActive` becomes `true` for the "About" link, and `false` for the others.
5. The "About" link gets the `active-link` class; the other links lose it.
6. The matching `Route` (`About` component) is rendered on the screen.

### Comparison Table: Link vs NavLink

| Feature | `Link` | `NavLink` |
|---------|--------|-----------|
| Basic navigation (no page reload) | ✅ Yes | ✅ Yes |
| Knows if it is the "active" route | ❌ No | ✅ Yes |
| Can auto-apply active styling | ❌ No | ✅ Yes (via `isActive`) |
| Best used for | Simple links (buttons, "Go to page" links) | Navigation bars/menus where highlighting the current page matters |
| Common prop | `to` | `to`, `className` (function), `style` (function) |

Now that we can navigate between fixed pages like `/` and `/about`, let's look at how to handle pages that depend on dynamic data — like showing a different product for every product ID in the URL.

---

## Dynamic Routes and useParams

### Definition

So far, our routes have been **fixed (static)** — like `/about` or `/contact`. But in real apps, we often need routes that change based on data. For example:

- `/products/1`, `/products/2`, `/products/3` — one page for many different products
- `/users/aryan`, `/users/nayan` — one page for many different user profiles

Instead of writing a separate `Route` for every single product or user, React Router lets us create **one route with a placeholder** in the path. This is called a **Dynamic Route**.

> A Dynamic Route is a single route definition that can match many different URLs by using a placeholder (like `:id`) inside the path, and `useParams` is used to read that placeholder's value.

### Core Terms

| Term | Meaning |
|------|---------|
| **Dynamic Route** | A route whose path contains a variable part (placeholder) instead of a fixed value, e.g. `/products/:id`. |
| **URL Parameter (Param)** | The dynamic part of the URL. In `/products/:id`, `id` is the parameter name, and the actual value (like `5`) is filled in when the URL is visited. |
| **`:id` (Placeholder syntax)** | The colon (`:`) before a word in the `path` tells React Router: "this part of the URL can be anything — treat it as a variable named `id`." |
| **`useParams()`** | A React Router **hook** that lets you read the current URL's dynamic parameter values inside your component. |

**Simple analogy:** Think of a dynamic route like a hotel room number template: `"Room :number"`.
- The **template** is fixed (`Room`).
- The **number** part changes for every guest.
- `useParams()` is like asking the front desk, *"Which room number does this guest currently have?"*

### Imports

```jsx
import { BrowserRouter, Routes, Route, Link, useParams } from "react-router-dom";
```

| Import | Purpose |
|--------|---------|
| `useParams` | A hook used **inside the target component** to read the dynamic value from the URL. |

### Working of Dynamic Routes and useParams

1. Define a route with a colon (`:`) before the variable part of the path:
   ```jsx
   <Route path="/products/:id" element={<ProductDetails />} />
   ```
2. This single route now matches **any** URL like `/products/1`, `/products/2`, `/products/anything`.
3. Inside the `ProductDetails` component, call the `useParams()` hook:
   ```jsx
   const { id } = useParams();
   ```
4. `useParams()` returns an object containing the dynamic values from the URL. Since our placeholder was named `:id`, the object looks like `{ id: "2" }` (values are always strings).
5. You can now use this `id` to show specific data — e.g., fetch a product, find it in an array, or display it directly.

**Syntax:**

```jsx
// Defining a dynamic route
<Route path="/prefix/:paramName" element={<SomeComponent />} />
```

```jsx
// Reading the param inside the component
import { useParams } from "react-router-dom";

function SomeComponent() {
  const { paramName } = useParams();
  return <h2>Value: {paramName}</h2>;
}
```

### Small Project: Product Details Page

**Step 1: Create a data file**

```jsx
// productsData.js
const products = [
  { id: "1", name: "Laptop", price: "₹55,000" },
  { id: "2", name: "Headphones", price: "₹2,500" },
  { id: "3", name: "Keyboard", price: "₹1,200" },
];

export default products;
```

**Step 2: Create the Product List page**

```jsx
// ProductList.jsx
import { Link } from "react-router-dom";
import products from "./productsData";

function ProductList() {
  return (
    <div>
      <h2>Our Products</h2>
      <ul>
        {products.map((product) => (
          <li key={product.id}>
            <Link to={`/products/${product.id}`}>{product.name}</Link>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default ProductList;
```

**Step 3: Create the Product Details page**

```jsx
// ProductDetails.jsx
import { useParams } from "react-router-dom";
import products from "./productsData";

function ProductDetails() {
  const { id } = useParams();

  // Find the product whose id matches the URL param
  const product = products.find((p) => p.id === id);

  if (!product) {
    return <h2>Product not found</h2>;
  }

  return (
    <div>
      <h2>{product.name}</h2>
      <p>Price: {product.price}</p>
    </div>
  );
}

export default ProductDetails;
```

**Step 4: Set up routing in `App.jsx`**

```jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";
import ProductList from "./ProductList";
import ProductDetails from "./ProductDetails";

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link>
      </nav>

      <Routes>
        <Route path="/" element={<ProductList />} />
        <Route path="/products/:id" element={<ProductDetails />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

### Line-by-Line Explanation

- `productsData.js` — a simple array acting as fake "database" of products, each with a unique `id`.
- `ProductList.jsx`:
  - Loops through all products using `.map()`.
  - Each product name is wrapped in a `Link` pointing to `/products/<id>` — notice the **template literal** `` `/products/${product.id}` `` builds the dynamic URL.
- `ProductDetails.jsx`:
  - `useParams()` reads the `id` from the current URL.
  - `.find()` searches the `products` array for a product whose `id` matches the URL's `id`.
  - If no product matches, it shows "Product not found" — this handles invalid URLs gracefully.
- `App.jsx`:
  - `<Route path="/products/:id" element={<ProductDetails />} />` — **one single route** handles unlimited products, instead of writing a separate route for each one.

### What Happens When You Click a Product?

1. User is on `/` and sees the product list.
2. User clicks "Headphones" → `Link to="/products/2"`.
3. URL changes to `/products/2` (no reload).
4. `Routes` checks all routes and matches `/products/:id` because `2` fits the `:id` placeholder.
5. `ProductDetails` component renders.
6. Inside it, `useParams()` returns `{ id: "2" }`.
7. `.find()` locates the product with `id === "2"` → "Headphones".
8. The page displays "Headphones" and its price.

### Quick Recap Table

| Concept | Explanation |
|---------|-------------|
| Dynamic Route | A route path containing a placeholder like `:id` |
| `:id` | Tells React Router this part of the URL is variable |
| `useParams()` | Hook used to read the current dynamic value(s) from the URL |
| Param values | Always returned as **strings**, even if they look like numbers |
| Why use it | Avoids writing a separate route for every single item (product, user, post, etc.) |

So far, every route we've built stands completely on its own. But real apps often have pages that share a layout — like a dashboard with a sidebar that never changes while the middle content does. Let's look at how React Router handles that with nested routes.

---

## Nested Routes, Index Route, and Outlet

### Definition

So far, every route we defined rendered its component directly inside `Routes` — like separate, independent pages. But in real apps, many pages **share a common layout**. For example:

- A dashboard where the sidebar/header stays the same, but the middle content changes (Profile, Settings, Orders).
- A website where the navbar and footer stay fixed, but the main content area changes.

Instead of repeating the same layout code in every page, React Router lets us create **Nested Routes** — routes placed *inside* other routes, sharing a common parent layout.

> Nested Routes let a parent route render a shared layout, while child routes decide what content appears **inside** that layout, using `Outlet` as the placeholder for the child content.

### Core Terms

| Term | Meaning |
|------|---------|
| **Nested Route** | A `Route` defined **inside** another `Route`, so the child route's component renders inside the parent's layout instead of replacing the whole page. |
| **Parent Route** | The outer route that provides the shared layout (like a navbar/sidebar) common to all its child routes. |
| **Child Route** | A route nested inside a parent route; it only renders the specific content area, not the whole layout. |
| **`Outlet`** | A special component placed inside the parent's layout. It acts as a **placeholder** — React Router automatically renders the matching child route's component here. |
| **Index Route** | A special **default child route** (marked with the `index` prop) that renders automatically when the parent's path is visited directly, with no extra path segment. |

**Beginner analogy — an Instagram profile page:** Think about opening someone's profile on Instagram.
- The **profile header** (photo, name, bio, follower count) stays exactly the same no matter what.
- Below it there are **tabs** — Posts, Reels, Tagged. Clicking a tab does **not** reload the whole profile; only the grid of content below the header changes.
- The **header** is the **parent layout** — it's shared by every tab.
- Each **tab's content** is a **child route** — it only controls the part *inside* the shared layout.
- `Outlet` is simply the empty slot in the header layout where whichever tab's content is "plugged in."
- If you open the profile without tapping any tab, Instagram shows a **default tab** (usually Posts) automatically — that's exactly what an **Index Route** does.

**A second, more mechanical analogy:** Think of a TV with a fixed frame (the parent layout: buttons, stand, remote sensor) and a screen inside it (`Outlet`).
- The **frame** never changes — that's the parent layout.
- The **channel showing on the screen** changes — that's the child route's content.
- If you turn on the TV without pressing any channel button, it shows a **default channel** — that's the index route.

**Parent layout vs. child content — the key distinction:** Before looking at any code, make sure this difference is clear, because it's the whole idea behind nested routes:

| | Parent Route | Child Route |
|---|---|---|
| What it renders | The **shared layout/shell** — things like a sidebar, navbar, or page frame that should stay on screen no matter which sub-page is open | The **specific content** for one sub-page — only the part that changes |
| Where it renders | Directly inside `Routes`, matched by its own `path` | **Inside** the parent's `<Outlet />`, matched by its own (shorter) `path` |
| How many times it re-renders when you switch sub-pages | **Never** — it stays mounted, so the sidebar/navbar doesn't flicker or reset | **Every time** — it swaps out for whichever child matches the new URL |
| Example in the project below | `DashboardLayout` (renders the sidebar + `<Outlet />`) | `DashboardHome`, `Profile`, `Settings` (each renders only inside `<Outlet />`) |

### Imports

```jsx
import { BrowserRouter, Routes, Route, Link, Outlet } from "react-router-dom";
```

| Import | Purpose |
|--------|---------|
| `Route` | Defines a path-to-component mapping — can now be **nested** inside another `Route`. |
| `Outlet` | Placed inside the parent layout component — tells React Router **where** to render the matched child route. |

### Working of Nested Routes, Index Route, and Outlet

Here's the step-by-step flow, from writing the routes to seeing content appear on screen:

1. **Define the parent route** with its own `path` and a layout component as its `element` — but instead of self-closing it (`/>`), give it an opening and closing tag so child routes can go inside it:
   ```jsx
   <Route path="/dashboard" element={<DashboardLayout />}>
     <Route index element={<DashboardHome />} />
     <Route path="profile" element={<Profile />} />
     <Route path="settings" element={<Settings />} />
   </Route>
   ```
2. **Notice the child paths have no leading slash.** `profile` and `settings` are **not** written as `/profile` or `/settings` — React Router automatically joins them onto the parent's path, producing the full URLs `/dashboard/profile` and `/dashboard/settings`.
3. **Add `<Outlet />` inside the parent's layout component.** Wherever you place `<Outlet />` inside `DashboardLayout`'s JSX is exactly where the matched child's content will appear on the page.
4. **React Router matches in two steps when the URL is `/dashboard/profile`:**
   - First, it matches the **parent** route `/dashboard` and renders `DashboardLayout` (the shared shell).
   - Then, it looks at the remaining part of the URL (`profile`) and matches it against the **child** routes, finding `path="profile"`.
   - It renders `Profile` **inside** the `<Outlet />` that's sitting inside `DashboardLayout`.
5. **The `index` route is the "nothing after the parent path" case.** It has no `path` of its own (just the `index` prop) and renders automatically when the URL is exactly `/dashboard`, with no extra segment after it — like the default Instagram tab.
6. **Because the parent stays mounted while children swap,** the sidebar/header never flashes or re-renders when you move between `profile` and `settings` — only the `<Outlet />` content changes.

**Syntax:**

```jsx
// Parent route with nested children
<Route path="/parent" element={<ParentLayout />}>
  <Route index element={<DefaultChild />} />
  <Route path="child-one" element={<ChildOne />} />
  <Route path="child-two" element={<ChildTwo />} />
</Route>
```

```jsx
// Inside ParentLayout.jsx
import { Outlet } from "react-router-dom";

function ParentLayout() {
  return (
    <div>
      <h2>Shared Layout</h2>
      <Outlet /> {/* Child route renders here */}
    </div>
  );
}
```

### Small Project: Dashboard with Nested Routes

**Step 1: Create the child page components**

```jsx
// DashboardHome.jsx
function DashboardHome() {
  return <p>Welcome to your Dashboard! Select an option from the sidebar.</p>;
}
export default DashboardHome;
```

```jsx
// Profile.jsx
function Profile() {
  return <p>This is your Profile page.</p>;
}
export default Profile;
```

```jsx
// Settings.jsx
function Settings() {
  return <p>This is your Settings page.</p>;
}
export default Settings;
```

**Step 2: Create the shared layout with `Outlet`**

```jsx
// DashboardLayout.jsx
import { Outlet, Link } from "react-router-dom";

function DashboardLayout() {
  return (
    <div style={{ display: "flex" }}>
      <aside style={{ marginRight: "20px" }}>
        <h3>Dashboard Menu</h3>
        <ul>
          <li><Link to="/dashboard">Home</Link></li>
          <li><Link to="/dashboard/profile">Profile</Link></li>
          <li><Link to="/dashboard/settings">Settings</Link></li>
        </ul>
      </aside>

      <main>
        <Outlet />
      </main>
    </div>
  );
}

export default DashboardLayout;
```

**Step 3: Set up nested routing in `App.jsx`**

```jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";
import DashboardLayout from "./DashboardLayout";
import DashboardHome from "./DashboardHome";
import Profile from "./Profile";
import Settings from "./Settings";

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Main Site</Link> | <Link to="/dashboard">Dashboard</Link>
      </nav>

      <Routes>
        <Route path="/" element={<h2>Welcome to the Main Site</h2>} />

        <Route path="/dashboard" element={<DashboardLayout />}>
          <Route index element={<DashboardHome />} />
          <Route path="profile" element={<Profile />} />
          <Route path="settings" element={<Settings />} />
        </Route>
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

### Line-by-Line Explanation

- `<Route path="/dashboard" element={<DashboardLayout />}>` — this is the **parent route**. It renders `DashboardLayout` for any URL starting with `/dashboard`.
- `<Route index element={<DashboardHome />} />` — the **index route**. It has no `path`, so it only activates when the URL is exactly `/dashboard` (not `/dashboard/profile` etc.).
- `<Route path="profile" element={<Profile />} />` — a **child route**. Its full URL becomes `/dashboard/profile` (React Router automatically joins it with the parent path).
- `<Route path="settings" element={<Settings />} />` — similarly becomes `/dashboard/settings`.
- Inside `DashboardLayout.jsx`, `<Outlet />` is the exact spot where `DashboardHome`, `Profile`, or `Settings` will appear, depending on the URL.
- The sidebar (`<aside>`) stays exactly the same across all dashboard pages — only the `<main>` content (via `Outlet`) changes.

### What Happens When You Click "Profile"?

1. User is on `/dashboard`, seeing `DashboardHome` inside the `Outlet` (because of the `index` route).
2. User clicks `Link to="/dashboard/profile"`.
3. URL changes to `/dashboard/profile` (no reload).
4. `Routes` matches the parent route `/dashboard` → renders `DashboardLayout` (already rendered, so the sidebar doesn't re-render/flash).
5. It then checks the child routes and finds `path="profile"` matches.
6. `Profile` component renders inside the `<Outlet />`.
7. Sidebar stays exactly as it was — only the content area updates.

### Quick Recap Table

| Concept | Explanation |
|---------|-------------|
| Nested Route | A `Route` placed inside another `Route`, sharing the parent's layout |
| Parent Route | Provides the shared layout (`element` of the outer `Route`) |
| Child Route Path | Written **without** a leading `/` — automatically combined with the parent's path |
| `Outlet` | Placeholder inside the parent layout where the matched child route renders |
| Index Route | A child route with the `index` prop instead of a `path` — the default view for the parent's exact path |

Every navigation we've done so far has happened because the **user clicked** a `Link` or `NavLink`. But sometimes the app itself needs to change the route — for example, right after a form is submitted. Let's look at how to navigate from inside your own code.

---

## useNavigate and Navigate

### Definition

So far, we've navigated between routes only by the user **clicking** something — `Link` or `NavLink`. But sometimes we need to change the route **programmatically**, i.e., through JavaScript code, without the user clicking a link. For example:

- After a user submits a login form successfully, redirect them to `/dashboard`.
- After a timer runs out, automatically send the user to `/home`.
- If a user is not logged in, redirect them away from a protected page.

React Router provides two tools for this:

- **`useNavigate`** — a **hook** used to navigate programmatically from inside functions (like `onClick`, `onSubmit`, `useEffect`).
- **`Navigate`** — a **component** used to redirect **declaratively** while rendering JSX (commonly used for instant redirects or protecting routes).

> `useNavigate` lets you navigate in response to logic/events in your code, while `Navigate` lets you redirect simply by rendering it in JSX.

### Core Terms

| Term | Meaning |
|------|---------|
| **Programmatic Navigation** | Changing the route through JavaScript code (function calls), rather than the user clicking a `Link`. |
| **`useNavigate()`** | A React Router hook that returns a function you can call to navigate to a different path. |
| **`navigate()` function** | The function returned by `useNavigate()`. Calling `navigate("/somepath")` changes the URL to `/somepath`. |
| **`Navigate` component** | A JSX component that, when rendered, immediately redirects the user to the given path — used inside JSX instead of calling a function. |
| **`replace` option** | An option that replaces the current entry in browser history instead of adding a new one — so the "Back" button skips the redirected page. |

**Simple analogy:** Think of `useNavigate` like a **GPS command** you give manually ("take me to Home now") whenever you decide, based on some event (like reaching a destination or an error). `Navigate` is like a **road sign that automatically redirects traffic** the moment someone drives past it — no manual command needed, it happens as soon as it's rendered.

### Imports

```jsx
import { useNavigate, Navigate } from "react-router-dom";
```

| Import | Purpose |
|--------|---------|
| `useNavigate` | A hook — call it inside a component to get a `navigate` function you can use anywhere in that component (event handlers, effects, etc.). |
| `Navigate` | A component — render it directly in JSX to redirect immediately when that part of the JSX is displayed. |

### Working of useNavigate

1. Call the hook at the top of your component: `const navigate = useNavigate();`
2. This gives you a function called `navigate`.
3. Call `navigate("/path")` **inside any event handler or logic** (like a button click or after a form is submitted) to change the route.
4. React Router updates the URL and renders the matching component — same as clicking a `Link`, but triggered by code.

**Syntax:**

```jsx
import { useNavigate } from "react-router-dom";

function SomeComponent() {
  const navigate = useNavigate();

  function handleClick() {
    navigate("/target-path");
  }

  return <button onClick={handleClick}>Go</button>;
}
```

**Optional second argument:**

```jsx
navigate("/target-path", { replace: true }); // replaces current history entry
navigate(-1); // goes back one step, like clicking browser's Back button
navigate(1);  // goes forward one step
```

### Working of Navigate

1. `Navigate` is a component, not a function — you use it **inside JSX**, usually with a condition.
2. As soon as React renders `<Navigate to="/path" />`, it immediately redirects to that path.
3. It's most commonly used for **protecting routes** — if a condition (like "not logged in") is true, render `Navigate` instead of the actual page. *(We'll build this pattern properly, with a reusable wrapper component, in the Protected Routes section later — for now, the small project below shows the basic idea.)*

**Syntax:**

```jsx
import { Navigate } from "react-router-dom";

function SomeComponent() {
  const isLoggedIn = false;

  if (!isLoggedIn) {
    return <Navigate to="/login" />;
  }

  return <h2>Welcome to your account!</h2>;
}
```

### Small Project: Login Page with Redirect and Protected Route

**Step 1: Create the Login page (uses `useNavigate`)**

```jsx
// Login.jsx
import { useState } from "react";
import { useNavigate } from "react-router-dom";

function Login({ setIsLoggedIn }) {
  const [username, setUsername] = useState("");
  const navigate = useNavigate();

  function handleSubmit(e) {
    e.preventDefault();

    if (username.trim() !== "") {
      setIsLoggedIn(true);       // mark user as logged in
      navigate("/dashboard");    // programmatically redirect
    }
  }

  return (
    <form onSubmit={handleSubmit}>
      <h2>Login</h2>
      <input
        type="text"
        placeholder="Enter username"
        value={username}
        onChange={(e) => setUsername(e.target.value)}
      />
      <button type="submit">Login</button>
    </form>
  );
}

export default Login;
```

**Step 2: Create the Dashboard page**

```jsx
// Dashboard.jsx
function Dashboard() {
  return <h2>Welcome to your Dashboard!</h2>;
}

export default Dashboard;
```

**Step 3: Create a Protected Route wrapper (uses `Navigate`)**

```jsx
// ProtectedRoute.jsx
import { Navigate } from "react-router-dom";

function ProtectedRoute({ isLoggedIn, children }) {
  if (!isLoggedIn) {
    return <Navigate to="/login" replace />;
  }
  return children;
}

export default ProtectedRoute;
```

*(This is a basic version of the pattern. Later, once we've covered `useLocation`, we'll upgrade `ProtectedRoute` to also remember which page the user was trying to visit — see the Protected Routes section below.)*

**Step 4: Set up routing in `App.jsx`**

```jsx
import { useState } from "react";
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Login from "./Login";
import Dashboard from "./Dashboard";
import ProtectedRoute from "./ProtectedRoute";

function App() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  return (
    <BrowserRouter>
      <Routes>
        <Route path="/login" element={<Login setIsLoggedIn={setIsLoggedIn} />} />

        <Route
          path="/dashboard"
          element={
            <ProtectedRoute isLoggedIn={isLoggedIn}>
              <Dashboard />
            </ProtectedRoute>
          }
        />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

### Line-by-Line Explanation

- `const navigate = useNavigate();` in `Login.jsx` — gives us a function to redirect programmatically.
- `handleSubmit` — runs when the form is submitted; it prevents the default page reload, marks the user as logged in, then calls `navigate("/dashboard")` to move to the dashboard **without the user clicking any link**.
- `ProtectedRoute.jsx` — a wrapper component:
  - If `isLoggedIn` is `false`, it renders `<Navigate to="/login" replace />`, which **immediately redirects** to the login page.
  - `replace` is used so this redirect doesn't create an extra "back button" step — the user can't go "back" into a broken protected page.
  - If `isLoggedIn` is `true`, it simply renders `children` — in this case, `<Dashboard />`.
- In `App.jsx`, the `/dashboard` route is wrapped with `ProtectedRoute`, so it's only shown if the user is actually logged in.

### What Happens When You Log In?

1. User is on `/login`, types a username, and submits the form.
2. `handleSubmit` runs → sets `isLoggedIn` to `true` → calls `navigate("/dashboard")`.
3. URL changes to `/dashboard` (no page reload).
4. `Routes` matches `/dashboard`, which renders `ProtectedRoute`.
5. Since `isLoggedIn` is now `true`, `ProtectedRoute` renders its `children` → `Dashboard` is shown.

### What Happens If Someone Visits `/dashboard` Directly Without Logging In?

1. `Routes` matches `/dashboard` → renders `ProtectedRoute`.
2. `isLoggedIn` is `false` → `ProtectedRoute` returns `<Navigate to="/login" replace />`.
3. React Router immediately redirects to `/login`, without showing the `Dashboard` content at all.

### Quick Recap Table

| Feature | `useNavigate` | `Navigate` |
|---------|--------------|------------|
| Type | Hook (returns a function) | Component (used in JSX) |
| When it runs | Only when you call `navigate(...)` inside your code | Immediately, as soon as it is rendered |
| Best used for | Redirecting after an event (form submit, button click, timer) | Redirecting based on a condition while rendering (like protected routes) |
| Example | `navigate("/dashboard")` | `<Navigate to="/login" />` |
| Can go back/forward | Yes — `navigate(-1)` / `navigate(1)` | No |

So far, all the extra information in our URLs has come from path segments, like `:id` in `/products/:id`. There's another way to attach extra info to a URL — through query strings — which is especially useful for filters, search, and pagination.

---

## Query Strings & React Router — Notes

### 1. What is a Query String?

> **Definition:** The part of a URL that comes **after `?`**, used to send extra info to a page without changing its main path.

**Example:**
```
/products?category=electronics
```

| Part | Meaning |
|---|---|
| `/products` | Path |
| `?category=electronics` | Query String |

```
https://example.com/products?category=electronics
                    │       │
                    │       └── Query String
                    └── Path
```

---

### 2. Why Do We Need Query Strings? *(Main Concept)*

Instead of creating a separate page/route for every filter (e.g. `/products/electronics`), a query string lets the **same page** (`/products`) show different data based on a condition.

> "Show products where `category = electronics`" — without changing the route itself.

**Use case:** filtering, searching, sorting, pagination — all on one base path.

---

### 3. Basic Query String Syntax

```
/path?key=value
```

| Symbol | Meaning |
|---|---|
| `?` | Starts the query string |
| `key` | Parameter name |
| `=` | Separates key and value |
| `value` | Parameter value |
| `&` | Separates multiple parameters |

**Multiple parameters example:**
```
/products?category=electronics&sort=price&page=2
```
→ `category = electronics`, `sort = price`, `page = 2`

---

### 4. IMPORTANT: Parameter Names Are NOT Fixed/Special

- There is **no universal rule** that params must be named `category`, `sort`, `page`, etc.
- **The developer decides** the names when designing the app.

**Same idea, different valid names:**
```
/products?category=books
/products?type=books
/products?cat=books
```
All are equally valid — React/React Router does **not** enforce any naming.

---

### 5. Who Decides the Parameter Names? *(Big Topic — Highlighted)*

#### 👉 **YOU (the developer)** decide — not React or React Router.

**Design flow:**
```
YOU DESIGN → category → URL (/products?category=electronics)
   → React reads → searchParams.get("category") → "electronics"
```

#### How a parameter is actually created:
It's created when you call `setSearchParams()`, e.g. on a button click:

```jsx
<button onClick={() => setSearchParams({ category: "electronics" })}>
  Electronics
</button>
```
Clicking it → URL becomes `/products?category=electronics`.

#### You could rename it freely:
```js
setSearchParams({ type: "electronics" });   // → /products?type=electronics
setSearchParams({ product: "electronics" }); // → /products?product=electronics
```
Then read it back with the **same name** you chose:
```js
searchParams.get("type");
searchParams.get("product");
```

#### Common naming conventions (by purpose):
| Purpose | Example |
|---|---|
| Filtering | `/products?category=electronics` |
| Searching | `/products?search=iphone` |
| Sorting | `/products?sort=price` |
| Pagination | `/products?page=2` |
| Price range | `/products?minPrice=500&maxPrice=2000` |

*(We'll build a working pagination example with `useSearchParams` in the useSearchParams section below — for now, just know that a `page` query parameter is the standard way to track "which page of results" the user is on.)*

---

### 6. React Router: `useSearchParams()` Hook

```jsx
import { useSearchParams } from "react-router-dom";

const [searchParams, setSearchParams] = useSearchParams();
```

| Value | Purpose |
|---|---|
| `searchParams` | **Read** query parameters |
| `setSearchParams` | **Change/Set** query parameters |

*(This is the quick version. We'll go much deeper into `useSearchParams` — including `.has()`, `.getAll()`, updating one param without losing the others, and a full filtering project — in the dedicated useSearchParams section further below.)*

---

### 7. Reading Query Parameters

Given URL: `/products?category=electronics`

```js
const category = searchParams.get("category"); // "electronics"
```

**Multiple parameters:**
```js
const category = searchParams.get("category");
const sort = searchParams.get("sort");
const page = searchParams.get("page");
```

> ⚠️ **Note:** All values from the URL are **strings** by default.
> `page` → `"2"` (string), not `2` (number).
> Convert manually if needed: `Number(searchParams.get("page"))`

---

### 8. Changing Query Parameters

```js
setSearchParams({ category: "electronics" });
// URL → /products?category=electronics

setSearchParams({ category: "books" });
// URL → /products?category=books
```

**Setting multiple at once:**
```js
setSearchParams({
  category: "electronics",
  sort: "price",
  page: "2"
});
// URL → /products?category=electronics&sort=price&page=2
```

---

### 9. Quick Reference: `?` vs `&`

| Symbol | Role |
|---|---|
| `?` | Starts the query parameters |
| `&` | Separates additional parameters |

```
/products?category=books&sort=price&page=2
          └──────────┘ └────────┘ └──────┘
             param       param      param
```

---

### Summary
- Query strings = extra info passed via URL after `?`.
- Parameter **names are arbitrary** — chosen by the developer, not enforced by React/React Router.
- `useSearchParams()` → `searchParams.get(name)` to **read**, `setSearchParams({...})` to **write**.
- URL values are always **strings** — convert types manually when needed.

Query strings are just one piece of the current URL. Next, let's look at `useLocation`, a hook that gives you the *entire* picture of where you are — path, query string, hash, and even hidden data passed during navigation.

---

## useLocation

### Definition

Every time the URL changes in a React Router app, React Router keeps track of detailed information about that URL — not just the path, but also things like query strings, hash values, and any extra data passed along during navigation.

**`useLocation`** is a hook that gives you access to this information — the **current location object** — from inside any component. It tells you exactly "where you are" in the app at any given moment.

Common real-world uses:

- Highlighting the active tab/link based on the current path (an alternative to `NavLink`'s built-in behavior).
- Reading **query parameters** from the URL (e.g., `?search=shoes`).
- Sending analytics/tracking data whenever the route changes.
- Reading extra data passed during navigation (via `navigate("/path", { state: {...} })`).
- Remembering "where the user came from" so you can redirect them back after an action (like login).

> `useLocation` is a hook that returns an object describing the current URL in detail — path, search query, hash, and any state passed during navigation.

### Core Terms

| Term | Meaning |
|------|---------|
| **Location Object** | An object returned by `useLocation()` that describes the current URL in detail. |
| **`pathname`** | The path part of the URL, e.g., `/products/5` (does not include query string or hash). |
| **`search`** | The **query string** part of the URL, starting with `?`, e.g., `?category=shoes&sort=price`. |
| **`hash`** | The part of the URL after `#`, often used for jumping to a section on a page, e.g., `#reviews`. |
| **`state`** | Extra data attached to a navigation, not visible in the URL itself — passed using `navigate("/path", { state: {...} })` or `<Link state={{...}}>`. |
| **`key`** | A unique string React Router generates for each location — useful for detecting whether the location is genuinely new. |
| **Query Parameters** | Key-value pairs found in the `search` string (e.g., `category=shoes`), usually read using the `URLSearchParams` API. |

**Simple analogy:** If the URL is like a full postal address, then:
- `pathname` = the street address (`/products/5`)
- `search` = extra delivery instructions attached publicly (`?gift=true`)
- `hash` = a specific room number inside the building (`#reviews`)
- `state` = a private note inside the envelope that only the receiver (your app) can see, not written on the envelope itself (URL)

### Imports

```jsx
import { useLocation } from "react-router-dom";
```

| Import | Purpose |
|--------|---------|
| `useLocation` | A hook that returns the current location object, describing the URL and any navigation state. |

### Working of useLocation

1. Call the hook inside any component: `const location = useLocation();`
2. This returns an object with the following shape:
   ```js
   {
     pathname: "/products/5",
     search: "?category=shoes",
     hash: "#reviews",
     state: { from: "/cart" },
     key: "ac3df4"
   }
   ```
3. Every time the URL changes (via `Link`, `NavLink`, `navigate`, or the browser's back/forward buttons), the component **re-renders**, and `useLocation()` returns the **updated** location object.
4. You can then use any part of this object — `pathname` to know the current page, `search` to read filters/queries, or `state` to read data passed silently during navigation.

**Syntax:**

```jsx
import { useLocation } from "react-router-dom";

function SomeComponent() {
  const location = useLocation();

  console.log(location.pathname); // e.g. "/products/5"
  console.log(location.search);   // e.g. "?category=shoes"
  console.log(location.hash);     // e.g. "#reviews"
  console.log(location.state);    // e.g. { from: "/cart" }

  return <div>Current path: {location.pathname}</div>;
}
```

### Detailed Look at Each Property

**1. `pathname`** — represents the actual route path, **without** query strings or hash. Commonly used to check "which page am I on right now."

```jsx
function Header() {
  const location = useLocation();
  const isHome = location.pathname === "/";

  return <h1>{isHome ? "Welcome Home" : "Another Page"}</h1>;
}
```

**2. `search` (Reading Query Parameters)** — `search` gives you the **raw string**, like `"?category=shoes&sort=price"`. To actually read individual values, use the built-in `URLSearchParams` API:

```jsx
import { useLocation } from "react-router-dom";

function ProductFilter() {
  const location = useLocation();
  const queryParams = new URLSearchParams(location.search);

  const category = queryParams.get("category"); // "shoes"
  const sort = queryParams.get("sort");          // "price"

  return (
    <div>
      <p>Category: {category}</p>
      <p>Sort by: {sort}</p>
    </div>
  );
}
```

> **Tip:** React Router also provides a dedicated hook called `useSearchParams()` (covered earlier) which does this more conveniently, but `useLocation().search` shows you what's happening underneath.

**3. `hash`** — represents the part of the URL after `#`, often used to scroll to a specific section. Example: visiting `/article#comments` gives `location.hash === "#comments"`.

```jsx
function Article() {
  const location = useLocation();

  return (
    <div>
      <p>Current hash: {location.hash}</p>
      {/* You could use this to scroll to a specific section */}
    </div>
  );
}
```

**4. `state` (Passing Hidden Data During Navigation)** — unlike `search`, `state` data is **not visible in the URL** — it travels privately with the navigation. You set it using `navigate()` or `Link`, and read it using `useLocation().state`.

```jsx
// Sending state during navigation
navigate("/dashboard", { state: { from: "/login" } });
```

```jsx
// or using Link
<Link to="/dashboard" state={{ from: "/login" }}>Go to Dashboard</Link>
```

```jsx
// Reading state on the receiving page
function Dashboard() {
  const location = useLocation();
  const cameFrom = location.state?.from; // "/login"

  return <p>You came from: {cameFrom}</p>;
}
```

> **Important:** `state` is `undefined` if the page is opened directly (e.g., typed URL or refreshed), since no navigation with state happened. Always use optional chaining (`?.`) or check for `undefined` to avoid errors.

**5. `key`** — a unique identifier React Router assigns to each location entry. Rarely used directly by beginners, but useful for advanced cases like triggering animations only when the location truly changes.

### Small Project: "Remember Where You Came From" Redirect

A very common real-world use of `useLocation` + `state`: redirecting a user back to the page they originally wanted, after they log in.

**Step 1: Create a Protected Route that remembers the origin**

```jsx
// ProtectedRoute.jsx
import { Navigate, useLocation } from "react-router-dom";

function ProtectedRoute({ isLoggedIn, children }) {
  const location = useLocation();

  if (!isLoggedIn) {
    // Save the page the user was trying to visit
    return <Navigate to="/login" state={{ from: location.pathname }} replace />;
  }

  return children;
}

export default ProtectedRoute;
```

**Step 2: Create the Login page that reads the saved location**

```jsx
// Login.jsx
import { useState } from "react";
import { useNavigate, useLocation } from "react-router-dom";

function Login({ setIsLoggedIn }) {
  const [username, setUsername] = useState("");
  const navigate = useNavigate();
  const location = useLocation();

  // Where should we send the user after login? Default to "/dashboard"
  const redirectTo = location.state?.from || "/dashboard";

  function handleSubmit(e) {
    e.preventDefault();
    if (username.trim() !== "") {
      setIsLoggedIn(true);
      navigate(redirectTo); // send user back to where they originally wanted to go
    }
  }

  return (
    <form onSubmit={handleSubmit}>
      <h2>Login</h2>
      <input
        type="text"
        placeholder="Enter username"
        value={username}
        onChange={(e) => setUsername(e.target.value)}
      />
      <button type="submit">Login</button>
    </form>
  );
}

export default Login;
```

**Step 3: Set up routing in `App.jsx`**

```jsx
import { useState } from "react";
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Login from "./Login";
import Dashboard from "./Dashboard";
import Settings from "./Settings";
import ProtectedRoute from "./ProtectedRoute";

function App() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  return (
    <BrowserRouter>
      <Routes>
        <Route path="/login" element={<Login setIsLoggedIn={setIsLoggedIn} />} />

        <Route
          path="/dashboard"
          element={
            <ProtectedRoute isLoggedIn={isLoggedIn}>
              <Dashboard />
            </ProtectedRoute>
          }
        />

        <Route
          path="/settings"
          element={
            <ProtectedRoute isLoggedIn={isLoggedIn}>
              <Settings />
            </ProtectedRoute>
          }
        />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

### Line-by-Line Explanation

- In `ProtectedRoute.jsx`, `useLocation()` gives us `location.pathname` — the page the user was **trying to visit** (e.g., `/settings`).
- `<Navigate to="/login" state={{ from: location.pathname }} replace />` redirects to `/login`, but **secretly attaches** the original path using `state`.
- In `Login.jsx`, `location.state?.from` reads that saved path back. The `?.` (optional chaining) prevents an error if `state` is `undefined` (e.g., if the user visited `/login` directly).
- After a successful login, `navigate(redirectTo)` sends the user to wherever they originally wanted to go — `/settings` if that's where they came from, or `/dashboard` by default.

### What Happens Step by Step?

1. User (not logged in) tries to visit `/settings` directly.
2. `ProtectedRoute` checks `isLoggedIn` → `false`.
3. It reads the current path using `useLocation().pathname` → `/settings`.
4. It redirects to `/login`, attaching `state: { from: "/settings" }`.
5. On the `Login` page, `useLocation().state?.from` reads `/settings`.
6. User logs in → `navigate("/settings")` is called (instead of always going to `/dashboard`).
7. User lands exactly back where they originally intended to go.

### Quick Recap Table

| Property | What It Contains | Example Value |
|----------|-------------------|----------------|
| `pathname` | The route path (no query/hash) | `/products/5` |
| `search` | Raw query string | `?category=shoes` |
| `hash` | Section identifier after `#` | `#reviews` |
| `state` | Hidden data passed during navigation | `{ from: "/cart" }` |
| `key` | Unique id for the current location entry | `"ac3df4"` |

### Comparison Table: useLocation vs useParams vs useNavigate

| Hook | Purpose |
|------|---------|
| `useParams()` | Reads **dynamic segments** from the URL path, defined using `:param` in the route (e.g., `id` from `/products/:id`). |
| `useLocation()` | Reads **the full current location** — path, query string, hash, and any hidden navigation state. |
| `useNavigate()` | **Changes** the route programmatically — it doesn't read anything, it performs navigation. |

We already touched query strings twice now — briefly in the Query Strings notes, and again as `location.search` above. Let's now look at the dedicated hook React Router gives us for working with query strings the easy way.

---

## useSearchParams

### Definition

In the `useLocation` notes, we saw that the `search` property gives us the raw query string (like `"?category=shoes&sort=price"`), and we had to manually use `URLSearchParams` to read individual values from it.

React Router provides a **dedicated hook** to make this much easier: **`useSearchParams`**.

It works similarly to React's `useState` — it gives you the current query parameters **and** a function to update them, and it automatically keeps the URL and your component in sync.

Common real-world uses:

- Filters on an e-commerce site: `/products?category=shoes&sort=price`
- Search pages: `/search?q=react+router`
- Pagination: `/blog?page=2`
- Tabs stored in the URL so they survive a page refresh: `/settings?tab=security`

> `useSearchParams` is a hook that lets you **read** and **update** the query string part of the URL (the part after `?`), keeping your UI and the URL in sync automatically.

### Core Terms

| Term | Meaning |
|------|---------|
| **Query String** | The part of the URL after `?`, made up of key-value pairs, e.g., `?category=shoes&sort=price`. |
| **Query Parameter** | A single key-value pair inside the query string, e.g., `category=shoes`. |
| **`searchParams`** | An object (technically a `URLSearchParams` instance) returned by the hook, used to **read** current query parameter values. |
| **`setSearchParams`** | A function returned by the hook, used to **update** the query parameters (which also updates the URL). |
| **`.get(key)`** | A method on `searchParams` used to read the value of a specific query parameter. |
| **`.get(key)` returning `null`** | If a query parameter doesn't exist in the URL, `.get()` returns `null` (not `undefined`). |

**Simple analogy:** Think of the query string like the **settings written on a form's title bar** — `?category=shoes&sort=price` is like a sticky note attached to the top of a form saying "show shoes, sorted by price."
- `searchParams.get("category")` = reading what's written on the sticky note.
- `setSearchParams({...})` = writing a new sticky note (replacing the old one).

### Imports

```jsx
import { useSearchParams } from "react-router-dom";
```

| Import | Purpose |
|--------|---------|
| `useSearchParams` | A hook that returns `[searchParams, setSearchParams]` — used to read and update the URL's query string. |

### Working of useSearchParams

1. Call the hook inside a component:
   ```jsx
   const [searchParams, setSearchParams] = useSearchParams();
   ```
2. This works like array destructuring from `useState`:
   - `searchParams` → an object you can **read** query values from.
   - `setSearchParams` → a function you call to **update** the query string.
3. To read a value: `searchParams.get("category")` → returns the value as a **string**, or `null` if it's not present in the URL.
4. To update values: call `setSearchParams({ category: "shoes" })` — this **updates the URL** to `?category=shoes` and re-renders the component with the new `searchParams`.
5. Just like `useState`, updating search params causes the component to re-render, so your UI can react to filter/search/pagination changes.

**Syntax:**

```jsx
import { useSearchParams } from "react-router-dom";

function SomeComponent() {
  const [searchParams, setSearchParams] = useSearchParams();

  const category = searchParams.get("category"); // read a value

  function updateCategory() {
    setSearchParams({ category: "electronics" }); // update the URL
  }

  return (
    <div>
      <p>Current category: {category}</p>
      <button onClick={updateCategory}>Show Electronics</button>
    </div>
  );
}
```

### Detailed Look at Reading Values

```jsx
const [searchParams] = useSearchParams();
const sort = searchParams.get("sort"); // "price" or null if not in URL
```

```jsx
// Reading multiple parameters
const category = searchParams.get("category");
const sort = searchParams.get("sort");
const page = searchParams.get("page");
```

```jsx
// Checking if a parameter exists
if (searchParams.has("category")) {
  console.log("A category filter is applied");
}
```

If the URL is `?tag=react&tag=router`, a single key can appear more than once:

```jsx
const tags = searchParams.getAll("tag"); // ["react", "router"]
```

### Detailed Look at Updating Values

**Setting query params (replaces all existing ones):**

```jsx
setSearchParams({ category: "shoes", sort: "price" });
// URL becomes: ?category=shoes&sort=price
```

> **Important:** Calling `setSearchParams({...})` like this **replaces the entire query string** with the new object — any params not included are removed.

**Updating just one param while keeping others:**

Since `setSearchParams` replaces everything, if you want to **update one param and keep the rest**, you should build from the existing `searchParams`:

```jsx
function updateSortOnly(newSort) {
  const params = new URLSearchParams(searchParams); // copy existing params
  params.set("sort", newSort);                      // update just "sort"
  setSearchParams(params);                           // apply the merged result
}
```

**Removing a parameter:**

```jsx
function clearCategory() {
  const params = new URLSearchParams(searchParams);
  params.delete("category");
  setSearchParams(params);
}
```

### Pagination with useSearchParams

**What is pagination, in easy words?**

Imagine a list of 100 products. Showing all 100 on one page would be slow and messy. So instead, we break the list into small chunks — "pages" — and show one chunk at a time, like:

- Page 1 → items 1 to 10
- Page 2 → items 11 to 20
- Page 3 → items 21 to 30

...and so on. This chunking is called **pagination**. You've seen it on Google search results, Amazon product listings, blog archives — the "1 2 3 ... Next" buttons at the bottom of a list.

**Why `useSearchParams` is perfect for this**

The current page number is exactly the kind of thing that should live in the URL — not just in component state — because:

- It lets people **bookmark or share** a link straight to "page 3".
- The browser's **Back/Forward buttons** work correctly (going back takes you to the previous page).
- **Refreshing** the browser keeps you on the same page instead of resetting to page 1.

So instead of `useState` for the page number, we keep it as a query param like `?page=3`.

**Reading the current page**

```jsx
const [searchParams, setSearchParams] = useSearchParams();

// Read the page number from the URL; default to page 1 if it's not there
const currentPage = Number(searchParams.get("page")) || 1;
```

- `searchParams.get("page")` reads the value as a **string** (or `null` if missing), so we wrap it in `Number(...)` to turn it into an actual number.
- `|| 1` means: "if there's no `page` param yet (or it's `0`/invalid), just default to page 1."

**Going to the next / previous page**

```jsx
function goToNextPage() {
  setSearchParams({ page: currentPage + 1 });
}

function goToPrevPage() {
  if (currentPage > 1) {
    setSearchParams({ page: currentPage - 1 });
  }
}
```

Each click simply updates the `page` value in the URL. React Router re-renders the component with the new `searchParams`, so `currentPage` updates automatically — no manual state syncing needed.

**Putting it together — a simple paginated list**

```jsx
function ProductList({ allProducts }) {
  const [searchParams, setSearchParams] = useSearchParams();
  const currentPage = Number(searchParams.get("page")) || 1;

  const itemsPerPage = 10;
  const startIndex = (currentPage - 1) * itemsPerPage;
  const visibleProducts = allProducts.slice(startIndex, startIndex + itemsPerPage);

  const totalPages = Math.ceil(allProducts.length / itemsPerPage);

  return (
    <div>
      {visibleProducts.map((product) => (
        <p key={product.id}>{product.name}</p>
      ))}

      <button onClick={() => setSearchParams({ page: currentPage - 1 })} disabled={currentPage === 1}>
        Prev
      </button>

      <span> Page {currentPage} of {totalPages} </span>

      <button onClick={() => setSearchParams({ page: currentPage + 1 })} disabled={currentPage === totalPages}>
        Next
      </button>
    </div>
  );
}
```

**How it works, step by step:**

1. `currentPage` is read straight from the URL's `page` param.
2. `startIndex` and `.slice()` figure out **which 10 items** to show for that page.
3. Clicking **Next**/**Prev** just calls `setSearchParams` with an updated `page` value — this changes the URL (e.g. `?page=2`), which re-renders the component with the new slice of products.
4. The `disabled` checks stop the user from going below page 1 or past the last page.

> **Easy takeaway:** Pagination is just "show a small slice of a big list, and remember which slice via a `page` number." `useSearchParams` is the natural place to store that number, because it makes the current page shareable, bookmarkable, and back-button-friendly.

### Small Project: Product Filter with URL-Synced Search Params

**Step 1: Create the data file**

```jsx
// productsData.js
const products = [
  { id: 1, name: "Running Shoes", category: "shoes", price: 2000 },
  { id: 2, name: "Formal Shoes", category: "shoes", price: 3500 },
  { id: 3, name: "Headphones", category: "electronics", price: 1500 },
  { id: 4, name: "Smartwatch", category: "electronics", price: 4000 },
];

export default products;
```

**Step 2: Create the Product Filter page**

```jsx
// ProductFilter.jsx
import { useSearchParams } from "react-router-dom";
import products from "./productsData";

function ProductFilter() {
  const [searchParams, setSearchParams] = useSearchParams();

  const category = searchParams.get("category") || "all";
  const sort = searchParams.get("sort") || "none";

  // Filter products based on the current category
  let filteredProducts =
    category === "all"
      ? products
      : products.filter((p) => p.category === category);

  // Sort products based on the current sort option
  if (sort === "price") {
    filteredProducts = [...filteredProducts].sort((a, b) => a.price - b.price);
  }

  function handleCategoryChange(e) {
    const params = new URLSearchParams(searchParams);
    params.set("category", e.target.value);
    setSearchParams(params);
  }

  function handleSortChange(e) {
    const params = new URLSearchParams(searchParams);
    params.set("sort", e.target.value);
    setSearchParams(params);
  }

  return (
    <div>
      <h2>Products</h2>

      <label>
        Category:{" "}
        <select value={category} onChange={handleCategoryChange}>
          <option value="all">All</option>
          <option value="shoes">Shoes</option>
          <option value="electronics">Electronics</option>
        </select>
      </label>

      <label style={{ marginLeft: "10px" }}>
        Sort by:{" "}
        <select value={sort} onChange={handleSortChange}>
          <option value="none">None</option>
          <option value="price">Price (Low to High)</option>
        </select>
      </label>

      <ul>
        {filteredProducts.map((p) => (
          <li key={p.id}>
            {p.name} - ₹{p.price}
          </li>
        ))}
      </ul>
    </div>
  );
}

export default ProductFilter;
```

**Step 3: Set up routing in `App.jsx`**

```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
import ProductFilter from "./ProductFilter";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<ProductFilter />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

### Line-by-Line Explanation

- `const [searchParams, setSearchParams] = useSearchParams();` — gives us access to read and update the query string.
- `searchParams.get("category") || "all"` — reads the `category` param; if it doesn't exist in the URL yet, defaults to `"all"`.
- `filteredProducts` — filters the `products` array based on the current `category` value.
- `sort === "price"` — if the `sort` param is `"price"`, the list is sorted by price using `.sort()`.
- `handleCategoryChange` and `handleSortChange`:
  - Copy the existing params using `new URLSearchParams(searchParams)` so we don't lose the other filter.
  - Update just the relevant key using `.set()`.
  - Call `setSearchParams(params)` to apply the change — this updates the URL **and** re-renders the component with the new filtered/sorted list.
- Because everything is stored in the URL, refreshing the page or sharing the link (e.g., `/?category=shoes&sort=price`) preserves the exact same filtered view.

### What Happens When You Change the Category Dropdown?

1. User selects "Electronics" from the category dropdown.
2. `handleCategoryChange` runs, copies existing params, sets `category` to `"electronics"`.
3. `setSearchParams(params)` updates the URL to `?category=electronics` (keeping `sort` if it was already set).
4. Component re-renders; `searchParams.get("category")` now returns `"electronics"`.
5. `filteredProducts` recalculates, showing only electronics items.
6. The dropdown's `value={category}` also updates to reflect the new URL state.

### Quick Recap Table

| Action | Code |
|--------|------|
| Get the hook | `const [searchParams, setSearchParams] = useSearchParams();` |
| Read a value | `searchParams.get("key")` → returns string or `null` |
| Check if a key exists | `searchParams.has("key")` |
| Read repeated keys | `searchParams.getAll("key")` |
| Replace all params | `setSearchParams({ key: "value" })` |
| Update one param, keep others | Copy with `new URLSearchParams(searchParams)`, then `.set()`, then `setSearchParams(params)` |
| Remove a param | `params.delete("key")` then `setSearchParams(params)` |

### Comparison Table: useSearchParams vs useLocation

| Feature | `useLocation().search` | `useSearchParams()` |
|---------|--------------------------|------------------------|
| What it gives | Raw query string (e.g., `"?category=shoes"`) | Ready-to-use `URLSearchParams` object + updater function |
| Reading values | Requires manually creating `new URLSearchParams(location.search)` | Built-in `.get()`, `.has()`, `.getAll()` |
| Updating the URL | Not possible directly — need `navigate()` | Built-in `setSearchParams()` |
| Best used for | Reading full location details (path, hash, state) | Specifically working with query parameters (read + write) |

---

## Protected Routes (React Router)

### Definition

In many real apps, some pages should only be visible to **logged-in users** — like a **Dashboard**, **Profile**, or **Settings** page. If a user is not logged in, visiting these pages directly (by typing the URL) should redirect them to the **Login** page instead.

A **Protected Route** (also called a **Private Route**) is a pattern used to guard certain routes — it checks a condition (usually "is the user logged in?") before allowing access, and redirects elsewhere if that condition fails.

> React Router does **not** provide a built-in `ProtectedRoute` component. We build it ourselves using things we already know — `Navigate`, conditional rendering, and sometimes `useLocation`.

A Protected Route is a custom **wrapper component** that checks a condition (like login status) before showing its children — if the condition fails, it redirects the user elsewhere instead.

**Analogy:** Think of a Protected Route like a bouncer at a club entrance.
- The bouncer (`ProtectedRoute`) checks your ID (`isLoggedIn`) before letting you in.
- If you have valid ID, you're let inside to enjoy the club (`children` — the actual page).
- If not, you're redirected to the queue outside (`Navigate to="/login"`).

### Core Terms

| Term | Meaning |
|---|---|
| Protected Route / Private Route | A route that is only accessible under certain conditions (usually being logged in). |
| Authentication (Auth) | The process of verifying who a user is (e.g., logging in with a username/password). |
| Authentication State | A piece of state (e.g., `isLoggedIn`, `user`) that tracks whether/who is currently logged in. |
| Route Guard | A general term for any logic that "guards" access to a route based on a condition. |
| `children` prop | In React, whatever is placed between a component's opening and closing tags — used here to pass the actual page component into the guard. |
| `Navigate` | The React Router component used to redirect immediately when a condition fails. |

### Imports

```jsx
import { Navigate, useLocation } from "react-router-dom";
```

| Import | Purpose |
|---|---|
| `Navigate` | Used inside the guard component to redirect immediately if the condition (e.g., not logged in) fails. |
| `useLocation` | (Optional but recommended) Used to remember which page the user was trying to visit, so we can send them back there after logging in. |

### How Protected Routes Work

1. Create a reusable wrapper component (commonly named `ProtectedRoute`).
2. This component receives:
   - A **condition**, like `isLoggedIn` (passed as a prop).
   - The **actual page** to render, passed as `children`.
3. Inside `ProtectedRoute`:
   - If the condition is `false` (not logged in) → render `<Navigate to="/login" />` to redirect.
   - If the condition is `true` (logged in) → render `children` (the actual protected page).
4. Wrap any route that needs protection with this component, instead of putting the real page component directly.

#### Basic Syntax

```jsx
// ProtectedRoute.jsx
import { Navigate } from "react-router-dom";

function ProtectedRoute({ isLoggedIn, children }) {
  if (!isLoggedIn) {
    return <Navigate to="/login" replace />;
  }
  return children;
}

export default ProtectedRoute;
```

```jsx
// Usage inside routing
<Route
  path="/dashboard"
  element={
    <ProtectedRoute isLoggedIn={isLoggedIn}>
      <Dashboard />
    </ProtectedRoute>
  }
/>
```

> `replace` is used so the redirect **replaces** the current history entry — this way, pressing the browser's Back button doesn't take the user back into the protected (blocked) page.

### Small Project: Multi-Page App with Protected Routes

Goal: build an app with a **public Home page**, a **Login page**, and two **protected pages** (Dashboard and Settings) — and also remember where the user was trying to go, so they land there right after logging in.

#### Step 1 — Create the Page Components

```jsx
// Home.jsx
function Home() {
  return <h2>Welcome! This page is public.</h2>;
}
export default Home;
```

```jsx
// Dashboard.jsx
function Dashboard() {
  return <h2>Dashboard — only visible to logged-in users.</h2>;
}
export default Dashboard;
```

```jsx
// Settings.jsx
function Settings() {
  return <h2>Settings — only visible to logged-in users.</h2>;
}
export default Settings;
```

#### Step 2 — Create the Protected Route Wrapper (remembers origin using `useLocation`)

```jsx
// ProtectedRoute.jsx
import { Navigate, useLocation } from "react-router-dom";

function ProtectedRoute({ isLoggedIn, children }) {
  const location = useLocation();

  if (!isLoggedIn) {
    // Remember where the user was trying to go
    return <Navigate to="/login" state={{ from: location.pathname }} replace />;
  }

  return children;
}

export default ProtectedRoute;
```

#### Step 3 — Create the Login Page (redirects back to the original page)

```jsx
// Login.jsx
import { useState } from "react";
import { useNavigate, useLocation } from "react-router-dom";

function Login({ setIsLoggedIn }) {
  const [username, setUsername] = useState("");
  const navigate = useNavigate();
  const location = useLocation();

  const redirectTo = location.state?.from || "/dashboard";

  function handleSubmit(e) {
    e.preventDefault();
    if (username.trim() !== "") {
      setIsLoggedIn(true);
      navigate(redirectTo, { replace: true });
    }
  }

  return (
    <form onSubmit={handleSubmit}>
      <h2>Login</h2>
      <input
        type="text"
        placeholder="Enter username"
        value={username}
        onChange={(e) => setUsername(e.target.value)}
      />
      <button type="submit">Login</button>
    </form>
  );
}

export default Login;
```

#### Step 4 — Set Up Routing in `App.jsx`

```jsx
// App.jsx
import { useState } from "react";
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";
import Home from "./Home";
import Login from "./Login";
import Dashboard from "./Dashboard";
import Settings from "./Settings";
import ProtectedRoute from "./ProtectedRoute";

function App() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link> |{" "}
        <Link to="/dashboard">Dashboard</Link> |{" "}
        <Link to="/settings">Settings</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/login" element={<Login setIsLoggedIn={setIsLoggedIn} />} />

        <Route
          path="/dashboard"
          element={
            <ProtectedRoute isLoggedIn={isLoggedIn}>
              <Dashboard />
            </ProtectedRoute>
          }
        />

        <Route
          path="/settings"
          element={
            <ProtectedRoute isLoggedIn={isLoggedIn}>
              <Settings />
            </ProtectedRoute>
          }
        />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

### Line-by-Line Explanation

- `ProtectedRoute` receives `isLoggedIn` (a boolean) and `children` (the actual page component, like `<Dashboard />`).
- If `isLoggedIn` is `false`, it renders `<Navigate to="/login" state={{ from: location.pathname }} replace />`:
  - `location.pathname` captures exactly which page the user was trying to reach (e.g., `/settings`).
  - This is attached as `state`, so it travels invisibly to the Login page.
- If `isLoggedIn` is `true`, it simply returns `children` — the real page renders normally.
- In `Login.jsx`, `location.state?.from` reads back that saved path. `?.` prevents errors if the user visited `/login` directly (no state present).
- After login, `navigate(redirectTo, { replace: true })` sends the user to wherever they originally wanted to go, and `replace: true` avoids leaving the login page in the browser history.
- In `App.jsx`, `/dashboard` and `/settings` are both wrapped in `ProtectedRoute` — `/` and `/login` remain public.

### What Happens Step by Step?

#### Scenario A: User is not logged in, clicks "Settings" from the nav bar

1. URL changes to `/settings`.
2. `Routes` matches `/settings` → renders `ProtectedRoute`.
3. `isLoggedIn` is `false` → `ProtectedRoute` returns `<Navigate to="/login" state={{ from: "/settings" }} replace />`.
4. Browser redirects to `/login`; `Settings` component is never actually rendered.
5. User logs in → `navigate("/settings", { replace: true })` sends them straight to Settings.

#### Scenario B: User is already logged in, clicks "Dashboard"

1. URL changes to `/dashboard`.
2. `Routes` matches `/dashboard` → renders `ProtectedRoute`.
3. `isLoggedIn` is `true` → `ProtectedRoute` simply renders `children` → Dashboard shows immediately.

### Extending the Pattern: Role-Based Protected Routes

The same idea can be extended beyond simple login checks — for example, only allowing `"admin"` users into certain pages:

```jsx
function AdminRoute({ user, children }) {
  if (!user) {
    return <Navigate to="/login" replace />;
  }
  if (user.role !== "admin") {
    return <Navigate to="/unauthorized" replace />;
  }
  return children;
}
```

This shows how the same core pattern — **check a condition, render children or redirect** — can be reused for any kind of access control, not just "logged in or not."

### Quick Recap Table

| Step | What Happens |
|---|---|
| 1 | User tries to visit a protected path (e.g., `/dashboard`) |
| 2 | `ProtectedRoute` checks a condition (e.g., `isLoggedIn`) |
| 3 | If condition is `false` → `<Navigate to="/login" />` redirects immediately |
| 4 | If condition is `true` → `children` (the real page) is rendered |
| 5 | (Optional) `state={{ from: location.pathname }}` remembers where to send the user back after logging in |

### Step 7 — Complete Protected Route Structure (Context-Based Auth)

The earlier example passed `isLoggedIn` down as a prop. In a real app, that gets messy fast — every component between `App` and `ProtectedRoute` would need to pass it along. A cleaner, more scalable pattern is to store auth state in **React Context** instead, so any component can read it directly with a hook.

We'll build this out of five pieces:

1. **`AuthContext`** → stores login state
2. **`Login`** → logs the user in
3. **`ProtectedRoute`** → checks authentication
4. **`Dashboard`** → protected page
5. **`Logout`** → logs the user out

#### 1️⃣ `AuthContext.jsx` — Manage Authentication

```jsx
import { createContext, useContext, useState } from "react";

const AuthContext = createContext();

export function AuthProvider({ children }) {
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  const login = () => {
    setIsLoggedIn(true);
  };

  const logout = () => {
    setIsLoggedIn(false);
  };

  return (
    <AuthContext.Provider
      value={{
        isLoggedIn,
        login,
        logout
      }}
    >
      {children}
    </AuthContext.Provider>
  );
}

export function useAuth() {
  return useContext(AuthContext);
}
```

The context provides:

```
AuthContext
    │
    ├── isLoggedIn
    ├── login()
    └── logout()
```

#### 2️⃣ `ProtectedRoute.jsx` — The Gatekeeper

```jsx
import { Navigate } from "react-router-dom";
import { useAuth } from "./AuthContext";

function ProtectedRoute({ children }) {
  const { isLoggedIn } = useAuth();

  if (!isLoggedIn) {
    return <Navigate to="/login" replace />;
  }

  return children;
}

export default ProtectedRoute;
```

This is the most important part:

```jsx
if (!isLoggedIn) {
  return <Navigate to="/login" replace />;
}
```
> Means: "If the user isn't logged in, don't show the protected page. Send them to `/login`."

```jsx
return children;
```
> Means: "If they are logged in, allow the protected component to render."

#### 3️⃣ `Login.jsx` — The Login Page

```jsx
import { useAuth } from "./AuthContext";
import { useNavigate } from "react-router-dom";

function Login() {
  const { login } = useAuth();
  const navigate = useNavigate();

  const handleLogin = () => {
    login();
    navigate("/dashboard");
  };

  return (
    <div>
      <h1>Login Page</h1>
      <button onClick={handleLogin}>Login</button>
    </div>
  );
}

export default Login;
```

When the user clicks Login:

```
Click Login
    ↓
  login()
    ↓
isLoggedIn = true
    ↓
navigate("/dashboard")
    ↓
  Dashboard
```

#### 4️⃣ `Dashboard.jsx` — The Protected Page

```jsx
import { useAuth } from "./AuthContext";
import { useNavigate } from "react-router-dom";

function Dashboard() {
  const { logout } = useAuth();
  const navigate = useNavigate();

  const handleLogout = () => {
    logout();
    navigate("/login");
  };

  return (
    <div>
      <h1>Dashboard</h1>
      <p>Welcome to your private dashboard.</p>
      <button onClick={handleLogout}>Logout</button>
    </div>
  );
}

export default Dashboard;
```

#### 5️⃣ Configure the Routes — `App.jsx`

```jsx
import { Routes, Route } from "react-router-dom";

import Login from "./Login";
import Dashboard from "./Dashboard";
import ProtectedRoute from "./ProtectedRoute";

function App() {
  return (
    <Routes>
      <Route path="/login" element={<Login />} />

      <Route
        path="/dashboard"
        element={
          <ProtectedRoute>
            <Dashboard />
          </ProtectedRoute>
        }
      />
    </Routes>
  );
}

export default App;
```

Notice this part:

```jsx
<ProtectedRoute>
  <Dashboard />
</ProtectedRoute>
```

> We're saying: Dashboard is behind the authentication gate.

#### 6️⃣ Wrap Everything with `AuthProvider` — `main.jsx`

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import { BrowserRouter } from "react-router-dom";

import App from "./App";
import { AuthProvider } from "./AuthContext";

ReactDOM.createRoot(document.getElementById("root")).render(
  <BrowserRouter>
    <AuthProvider>
      <App />
    </AuthProvider>
  </BrowserRouter>
);
```

Now the structure is:

```
BrowserRouter
      ↓
AuthProvider
      ↓
     App
      ↓
   Routes
   ↙    ↘
Login   Dashboard
          ↓
   ProtectedRoute
          ↓
     Authentication
        Check
```

> **Why this is better than the prop-based version:** `isLoggedIn`, `login`, and `logout` no longer need to be threaded through `App` as props. Any component — `ProtectedRoute`, `Login`, `Dashboard`, a `Navbar`, anywhere — can just call `useAuth()` and get what it needs directly from context.

---
```
