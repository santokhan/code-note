1. **Calling async functions inside normal functions without awaiting them:**
   - When you call an `async` function without `await` or `.then()`, the function will execute asynchronously without blocking the rest of the code. However, if you're not handling the result of the async function, this can lead to unintended behavior, especially in environments where proper data flow and synchronization are critical.

2. **Server components and async functions in Next.js:**
   - In Next.js, **Server Components** are intended to run on the server and are not supposed to include any client-side logic. You cannot call a `client`-side component (which is browser-specific) or use browser-specific APIs in a server component, including event listeners like `onClick`. Server components are rendered on the server and must be synchronous, so they can't directly handle client-side events.

3. **'use server' and browser events:**
   - The `'use server'` directive in Next.js is a way to mark certain functions that should run only on the server (like fetching data or handling server-side logic). However, because this runs on the server, it doesn't have access to the DOM or browser-specific events like `onClick`. Events like `onClick` are part of the client-side (browser), and they need to be handled in **Client Components**.
   
   If you want to mix server-side logic with client-side interactivity, you can:
   - Use **Client Components** to handle interactions like `onClick`.
   - Pass data or trigger actions via **API routes** or **Server Functions** to interact with the server.

To summarize:
- Server components are meant for rendering server-side logic and data fetching, and they shouldn't contain client-side event handlers or browser-specific logic.
- For browser events, keep them inside client components and use appropriate mechanisms to interact with the server.
