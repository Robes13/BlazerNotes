# What is Blazor?
Blazor is a component-based Single Page Application (SPA) framework developed by Microsoft.

It allows developers to build interactive web UIs using C# instead of JavaScript.

Blazor apps are made up of Razor components, which are reusable UI pieces written in .razor files using a mix of HTML and C#.

### Typical SPA Flow
- User interacts with the Browser ->
- The browser sends a request to the Web Server ->
- The server returns the root view/component ->
- The browser renders a component tree, which can include nested components ->
After initial load, further interactivity is handled on the client side without full page reloads

### How Blazor Achieves Interactivity
##### Blazor Server (Server-side rendering + SignalR)
- Initial page is rendered on the server, then sent to the browser as static HTML ->
- A SignalR connection is established between client and server 


##### When the user interacts with the page:

- Events are sent to the server via SignalR ->
- The server updates the component state and sends back UI diffs (render tree deltas) ->
- A small JavaScript interop layer on the browser applies those diffs to the DOM ->

##### Pros 
- Thin client
- fast load time
- all C# on the server

##### Cons 
- Requires continuous connection (more server resources)

### Blazor WebAssembly (WASM)

- App is downloaded into the browser, including the .NET runtime (via WebAssembly) and app DLLs
- The app runs entirely in the browser
- No ongoing server communication is required after the initial load (except for API calls, etc)
- Interactivity is handled on the client, just like a traditional JS SPA, but using C#

### Blazor SSR (Static Server-Side Rendering)
- This is a newer capability in .NET 8 where the initial render is done on the server and sent to the client as static HTML.
- No interactivity is included unless the app is later “hydrated” (turned interactive via Blazor Server or WASM).
- Good for SEO and performance, especially when combined with interactivity later.
