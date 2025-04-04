1. CLI Tools (Build tool for Web) -
1. npx create-react-app my-app
2. Vite is build tool that has dev server, and build command to bundle using Rollup.
npm create vite@latest

2. Components are building blocks, which split UI into independent, reusable pieces. Name starts with Capital. JSX is JavaScript XML where return statement inside function returns component. Use Fragment(<>) to avoid div.
CSS can be inline, embedded, built tools, frameworks.
React Hooks introduced state and side-effects to Functional Components.
React Server Components allow developers to execute components on server.
Instances are components rendered as an element of another component.
Children is pseudo HTML attribute.

Functional Components - Return value is the JSX code to render to the DOM tree. 

Props(Properties) and state are JS Objects. Props (React props destructuring) are passed between components, while state is managed within component.
Conditional Rendering using Ternary or AND operator.
Composition is nesting and reusing smaller components inside larger ones. Can also pass using children.

3. Rendering - Declarative approach to render. Developer specifies how component should look, and React renders it to screen. Unlike imperative (Vanilla JS) where code used to manually manipulate DOM to update UI.
Virtual DOM is lightweight in-memory representation of DOM to optimise rendering. Calculate DOM updates needed to sync actual DOM with new VDOM. Called as Reconociliation.

Component Life Cycle - Mount, Update on interaction, Unmount.
useEffect is componentDidMount, componentDidUnmount, and componentDidUpdate when there is dependencies.
Effect describes how to synchronize external system to current state and props.
Lists and Keys - <li key > to match up.  
Render Props - Contents nested inside JSX tag will be stored in children prop, and to modify child, we re-render it with new props.
Ref - Access DOM Nodes created in render. Secret pocket of component that is mutable to escape React one-way data flow. Both state and ref are retained between re-renders, but ref doesn't re-render the component.
Event handler - Pass function, not call it as a prop to event handler(onClick). This ensures to remember it and call only when event occurs.
Event Propogation - From children of components bubble/propogate up the tree
High Order Components - Advanced React technique to reuse components. A pattern from React's compositional nature that takes a React component as parameter to return new component. Pure function that doesn't modify input component nor use inheritance.

4. Hooks -
1. useState
2. useEffect - Synchronise component with external system, i.e., side effects in React such as operations that interact with outside world.
3. useCallback - Return memoized version of callback function to avoid re-renders. React.memo ensures component re-renders only if props/state change.
4. useRef - Mutable reference that persists across re-renders, and read/write inside useEffect or outside render.
5. useReducer - Accepts reducer of state, action; and initialValue for the state. This depends on previous state and multiple related state values.
6. useMemo - Optimise calculations to prevent recalculations if state value changes. Cache results.
7. useContext - Pass data between components without passing props throwgh every level of tree. createContext where you have to call Provider with value={}
Helps manage components state and perform effects.
Custom Hooks - Build own hooks by reusing built-in hooks.
Hooks Best Practices - 
1. Call Hooks at top level.
2. Only call Hooks from React Functions.
3. Optimize useEffect with dependency Array.
4. Encapsulate Logic in Custom Hooks.
5. Use Effect cleanup

5. Routers - 
1. Browser URL path-pased routing, memory routing, URL-hash routing done by React Routers to switch components.

6. State Management - Maintain knowledge of applications inputs across multiple related data flows that form a transaction.
eg - Context avoids prop drilling, Redux has createStore(reducer). store.dispatch({type: 'Increment'}). MobX, Zustand

7. Writing CSS - CSS in CSS (Sass), CSS in JS (Styled), Utility-First-CSS (Tailwind using atomic CSSc classes)

8. Component/Libraries - Pre-built reusable components provided by libraries.
MaterialUI is props customizable CSS-in-JS, and Bootstrap is mentioned in <Link> and has utility classes. ShadCN, Chakra, Mantine.

9. Headless Component Libraries - Powerful state, logic and data management tools without enforcing UI structure. Basically UNSTYLED, so we have control. Eg - Headless UI(by Tailwind), Radix UI(@radix-ui/themes)

10. API Calls - Businesses can exchange data and save time, money using AJAX(Asynchronous Javscript and XML using Fetch API without reloading)
1. Axios - Promise based Client HTTP API library based on XMLHttpRequest interface
2. react-query - Data fetching and server caching library. Allows infinite scrolling, pagination.
  const { data, error, isLoading } = useQuery('posts', () =>
    axios.get('https://jsonplaceholder.typicode.com/posts').then(res => res.data)
  );
3. Apollo - graphQL client(@apollo/client graphql). It has Provider which needs client acccesing API custom hook. Then can use useQuery which requests gql obtained query values)

11. Testing - Run as part of dev process, such as in continuous integration, it helps prevent regressions in code.
1. Vitest - Vite native unit test framework
2. Jest - Has an extensive ecosystem

12. SSR Frameworks - Content rendered on server and sent to browser as fully functional HTML Page.
eg - Next.js(@nextjs/react - pages) - Built on top of Node.js, 
Remix(@remix-run/react - app/routes) - Nested automatically and prefetches.

13. Forms - To manage forms without state and props, use React Hook Form - Opensource form library.

14. Types and Validations - Typescript helps avoid mistakes during development. Zod helps EVEN validate form input, local storage, API contracts from client.

15. Animation - CSS smooth Transitions using framer-motion, react-spring, GSAP libraries by toggling classes.

16. Error Boundaries - Components that catch JS errors in child component tree, log them and display fallback UI.

17. Server API's - Render React components to HTML on server.

18. Suspense - Helps "suspend" rendering of components such as data fecthing or image loading. Rather render a fallback. Wrapped component throws a promise, caught by Suspense component that renders fallback. Once promise is resolved, wrapped component is rendered.

19. Portals - Render children into a DOM node that exists outside DOM hierarchy. Helps avoid CSS conflicts, Parent overflows, and yet maintain event bubbling. eg - createPortal(children, domNode)
