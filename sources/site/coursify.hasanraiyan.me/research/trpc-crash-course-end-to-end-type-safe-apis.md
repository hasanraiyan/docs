# Source: https://coursify.hasanraiyan.me/research/trpc-crash-course-end-to-end-type-safe-apis

tRPC Crash Course: End-to-End Type Safe APIs

# 

tRPC Crash Course: End-to-End Type Safe APIs

Verified Sources

Jun 15, 2026

## AI Summary

#### Learn tRPC In 45 Minutes — Full Crash Course

tRPC (**TypeScript Remote Procedure Call**) is a framework that enables end-to-end type safety between your frontend and backend — with zero code generation and zero runtime overhead. Unlike REST or GraphQL, tRPC lets you call server functions directly from the client as if they were local, with full TypeScript autocomplete and type checking on both sides [2]().

The core philosophy is simple: **your API is just a collection of TypeScript functions**. tRPC handles the serialization, routing, and network transport automatically, so you never write an API schema, never generate types, and never manually sync frontend types with backend types.

tRPC was created by **Alexandra "KATT" Schaller** and has rapidly become one of the most popular tools in the TypeScript ecosystem, especially within the T3 Stack. It's used in production by companies handling **2.4M+ requests/day with 99.97% uptime** .

## Footnotes

1. [tRPC Official Site](https://trpc.io) - Official tRPC documentation and quickstart guide [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [tRPC Quickstart](https://trpc.io/docs/quickstart) - Official quickstart: Your first tRPC API step by step [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 
3. [Building Production-Ready tRPC APIs - InfoQ](https://www.infoq.com/articles/building-trpc-api-typescript) - Production migration story: 2.4M requests/day, 99.97% uptime, error formatting, and middleware patterns [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 

### 

tRPC Evolution & Ecosystem

#### tRPC Born

2020

Initial release as an experimental TypeScript RPC framework. Focused on Next.js integration and proving end-to-end type safety was viable without GraphQL-style schemas."

#### v9 Breakthrough

2021

Major adoption wave. Added React Query integration, Zod validation, middleware support, and the create-t3-app scaffold. Community skyrocketed."

#### v10 Rewrite

2022

Complete rewrite with a builder-pattern API. Introduced .input()/.query()/.mutation() chaining, standalone middleware, and improved TypeScript inference."

#### Production Maturity

2023

Major companies adopt tRPC. Blog posts and case studies validate production usage at scale. Integration with Next.js App Router (RSC) begins."

#### v11 and Beyond

2024–25

tRPC v11 stabilizes with improved Next.js App Router support, experimental standalone middleware, .concat() patterns, and refined developer experience."

### Core Concepts: The Building Blocks of tRPC

tRPC has a small, composable set of primitives. Understanding these is the foundation for everything else :

| Concept | Description |
| --- | --- |
| Procedure | A function exposed to the client (query, mutation, or subscription) |
| Query | A read-only procedure for fetching data |
| Mutation | A procedure for writing/modifying data |
| Subscription | A persistent connection for real-time event streams |
| Router | Groups procedures (and sub-routers) under a namespace |
| Context | Data available to every procedure (session, DB, etc.) |
| Middleware | Runs before/after procedures; can modify context or throw errors |

The **builder pattern** is central to how tRPC works. Procedures are chained like this:

``1const publicProcedure = t.procedure; 2 3publicProcedure 4  .input(z.object({ name: z.string() }))  // 1. Validate input 5  .use(loggingMiddleware)                  // 2. Apply middleware 6  .query(async ({ input, ctx }) => {       // 3. Execute 7    return { greeting: `Hello, ${input.name}` }; 8  });``

This immutability means you can create **reusable base procedures** — for example, an `authenticatedProcedure` that automatically checks authorization, then use it across your entire app .

## Footnotes

1.  [tRPC Concepts](https://trpc.io/docs/concepts) - Official glossary of tRPC primitives: procedures, routers, context, middleware, validation [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
    
2.  [tRPC Define Procedures](https://trpc.io/docs/server/procedures) - Official docs on building procedures with the builder pattern and reusable base procedures [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
    

### 

API Paradigm Comparison

REST vs GraphQL vs tRPC across key dimensions

tRPC

RESTGraphQL

``1// Server: define procedure 2export const appRouter = router({ 3  greeting: publicProcedure 4    .input(z.object({ name: z.string() })) 5    .query(({ input }) => `Hello ${input.name}`), 6}); 7 8// Client: call it with full autocomplete 9const result = await trpc.greeting.query({ name: 'World' }); 10// result: string  ← fully inferred!``

### Building Your First tRPC API — From Scratch

1.  1
    
    Step 1
    
    Initialize the Server
    
    Create a new project and install the core dependencies:
    
    `1mkdir trpc-app && cd trpc-app 2npm init -y 3npm install @trpc/server @trpc/client zod superjson 4npm install -D typescript @types/node 5npx tsc --init`
    
    Create the recommended folder structure:
    
    .
    ├── server/
    │   ├── trpc.ts        # tRPC instance & setup
    │   ├── context.ts     # Context factory
    │   ├── appRouter.ts   # Main router + type export
    │   └── index.ts       # HTTP server entry point
    └── client/
        └── index.ts        # tRPC client
    
2.  2
    
    Step 2
    
    Create the tRPC Instance
    
    In `server/trpc.ts`, initialize tRPC with your context shape:
    
    `1import { initTRPC } from '@trpc/server'; 2import type { Context } from './context'; 3import superjson from 'superjson'; 4 5const t = initTRPC.context<Context>().create({ 6 transformer: superjson, // Enables Date, Map, Set, etc. 7}); 8 9export const router = t.router; 10export const publicProcedure = t.procedure; 11// Export reusable base procedures here`
    
    The `superjson` transformer allows tRPC to transmit types that plain JSON cannot handle .
    
    ## Footnotes
    
    1.  [tRPC Quickstart](https://trpc.io/docs/quickstart) - Official quickstart: Your first tRPC API step by step [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
        
    
3.  3
    
    Step 3
    
    Define Context
    
    In `server/context.ts`, define what data every procedure can access:
    
    `1import type { NextApiRequest, NextApiResponse } from 'next'; 2 3export function createContext({ 4 req, res, 5}: { 6 req: NextApiRequest; 7 res: NextApiResponse; 8}) { 9 return { 10 req, 11 res, 12 // Add: prisma, session, userId, etc. 13 }; 14} 15 16export type Context = ReturnType<typeof createContext>;`
    
    Context is how you inject **dependencies** — database connections, authentication state, request/response objects — into every procedure .
    
    ## Footnotes
    
    1.  [tRPC Define Procedures](https://trpc.io/docs/server/procedures) - Official docs on building procedures with the builder pattern and reusable base procedures [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
        
    
4.  4
    
    Step 4
    
    Build Your Router with Procedures
    
    In `server/appRouter.ts`, define your actual API:
    
    `1import { z } from 'zod'; 2import { router, publicProcedure } from './trpc'; 3 4let users = [ 5 { id: '1', name: 'Alice' }, 6 { id: '2', name: 'Bob' }, 7]; 8 9export const appRouter = router({ 10 // Query — read data 11 userList: publicProcedure.query(() => users), 12 13 // Query with input validation 14 userById: publicProcedure 15 .input(z.object({ id: z.string() })) 16 .query(({ input }) => users.find(u => u.id === input.id)), 17 18 // Mutation — write data 19 userCreate: publicProcedure 20 .input(z.object({ name: z.string().min(2) })) 21 .mutation(({ input }) => { 22 const user = { id: String(users.length + 1), name: input.name }; 23 users.push(user); 24 return user; 25 }), 26}); 27 28// CRITICAL: Export the TYPE so the client can infer it 29export type AppRouter = typeof appRouter;`
    
    The `AppRouter` type export is what makes the magic work — the client imports this **type-only** (no runtime code) to get full autocomplete [2]().
    
    ## Footnotes
    
    1.  [tRPC Quickstart](https://trpc.io/docs/quickstart) - Official quickstart: Your first tRPC API step by step [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
        
    2.  [tRPC Concepts](https://trpc.io/docs/concepts) - Official glossary of tRPC primitives: procedures, routers, context, middleware, validation [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
        
    
5.  5
    
    Step 5
    
    Serve Over HTTP
    
    In `server/index.ts`, attach your router to an HTTP server:
    
    `1import { createHTTPServer } from '@trpc/server/adapters/standalone'; 2import { appRouter } from './appRouter'; 3import { createContext } from './context'; 4 5const { listen } = createHTTPServer({ 6 router: appRouter, 7 createContext, 8}); 9 10listen(3000, () => { 11 console.log('tRPC server running on http://localhost:3000'); 12});`
    
6.  6
    
    Step 6
    
    Create the Type-Safe Client
    
    In `client/index.ts`, connect the client with full type inference:
    
    `1import { createTRPCClient, httpBatchLink } from '@trpc/client'; 2import type { AppRouter } from '../server/appRouter'; 3import superjson from 'superjson'; 4 5const client = createTRPCClient<AppRouter>({ 6 links: [ 7 httpBatchLink({ 8 url: 'http://localhost:3000', 9 transformer: superjson, 10 }), 11 ], 12}); 13 14// Full autocomplete + type checking! 15const users = await client.userList.query(); // User[] 16const user = await client.userById.query({ id: '1' }); // User | undefined 17const new = await client.userCreate.mutate({ name: 'Carol' }); // User 18 19// TypeScript error: missing required field 20await client.userCreate.mutate({ name: 42 }); // ❌ Type error!`
    
    No code generation. No schema file. The types flow from server to client **automatically** .
    
    ## Footnotes
    
    1.  [tRPC Quickstart](https://trpc.io/docs/quickstart) - Official quickstart: Your first tRPC API step by step [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
        
    

#### Pro Tip: The AppRouter Type Export

The single most important line in your tRPC server is `export type AppRouter = typeof appRouter;`. This type-only export is what enables end-to-end type safety. The client imports this type (zero runtime cost) and gets **full autocomplete, input validation errors, and return type inference** — all without a code generation step. If this export is missing or incorrect, the client falls back to `unknown` types for everything.

more...

### Middleware & Protected Procedures

Middleware is tRPC's mechanism for cross-cutting concerns like **authentication, logging, rate-limiting, and input sanitization**. Middleware runs before (and optionally after) a procedure and can modify the context or throw errors to abort execution .

The recommended pattern is to create **reusable base procedures** — different "flavors" of `t.procedure` that carry different middleware chains:

`1// server/trpc.ts 2import { initTRPC, TRPCError } from '@trpc/server'; 3import type { Context } from './context'; 4 5const t = initTRPC.context<Context>().create(); 6 7// Public procedure — no auth required 8export const publicProcedure = t.procedure; 9 10// Protected procedure — requires authentication 11const isAuthed = t.middleware(async ({ ctx, next }) => { 12 if (!ctx.session?.user) { 13 throw new TRPCError({ code: 'UNAUTHORIZED' }); 14 } 15 // Extend context with user info for downstream procedures 16 return next({ 17 ctx: { ...ctx, userId: ctx.session.user.id }, 18 }); 19}); 20 21export const protectedProcedure = t.procedure.use(isAuthed);`

Now any route built with `protectedProcedure` automatically requires auth, and the handler gets `ctx.userId` with a guaranteed TypeScript type:

``1export const appRouter = router({ 2  // 👈 Anyone can call 3  publicData: publicProcedure.query(() => 'public'), 4 5  // 🔒 Auth required — ctx.userId is typed as string, not string | undefined 6  mySecret: protectedProcedure.query(({ ctx }) => { 7    return `Hello user ${ctx.userId}`; 8  }), 9});``

## Footnotes

1.  [tRPC Middlewares](https://trpc.io/docs/server/middlewares) - Official middleware documentation: context narrowing, standalone middleware, .concat() pattern [↩](https://coursify.hasanraiyan.me/#user-content-fnref-6)
    

#### Warning: Context Narrowing is TypeScript-Only

When middleware extends the context (e.g., adding `userId`), the narrowing happens at the **TypeScript type level**, not at runtime. If a malicious client calls a protected endpoint directly, your middleware will throw a `TRPCError` — but you must always validate at the server. Never assume context fields exist without checking the middleware chain was actually executed.

more...

### tRPC with Next.js: The Full-Stack Sweet Spot

tRPC's strongest integration is with **Next.js**, where the client and server coexist in a single codebase, making type sharing trivial. The recommended setup uses `@trpc/react-query` which wraps **TanStack Query** (React Query) to give you caching, optimistic updates, and loading states out of the box .

**Recommended file structure for Next.js (App Router, v11):**

.
├── src/
│   ├── app/
│   │   ├── layout.tsx          # Wrap with TRPCProvider
│   │   ├── api/trpc/\[trpc\]/
│   │   │   └── route.ts        # tRPC HTTP handler
│   │   └── page.tsx
│   ├── server/
│   │   ├── trpc.ts             # tRPC instance
│   │   ├── context.ts          # Context factory
│   │   ├── routers/
│   │   │   ├── \_app.ts         # Root router (merges all)
│   │   │   ├── user.ts         # User sub-router
│   │   │   └── post.ts         # Post sub-router
│   │   └── index.ts
│   ├── trpc/
│   │   ├── client.ts           # Client setup (RSC)
│   │   └── provider.tsx        # Provider for client components
│   └── lib/
│       └── utils.ts

**Client-side usage with React Query hooks:**

`1// In a React component: 2function UserList() { 3 // Automatic caching, refetching, loading states 4 const { data: users, isLoading } = trpc.userList.useQuery(); 5 6 const mutation = trpc.userCreate.useMutation({ 7 onSuccess: () => { 8 // Invalidate and refetch after mutation 9 trpcUtils.userList.invalidate(); 10 }, 11 }); 12 13 if (isLoading) return <p>Loading...</p>; 14 15 return ( 16 <ul> 17 {users?.map(u => <li key={u.id}>{u.name}</li>)} 18 </ul> 19 ); 20}`

## Footnotes

1.  [tRPC Next.js Pages Router Setup](https://trpc.io/docs/client/nextjs/pages-router/setup) - Official guide for integrating tRPC with Next.js Pages Router [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
    

### Advanced tRPC Topics

What is httpBatchLink and why does it matter?

How do Subscriptions work in tRPC?

How do you merge routers in tRPC?

Can tRPC work with non-TypeScript clients?

What is the .concat() pattern?

#### Danger: Don't Over-Couple Your Procedures

A common anti-pattern is shoving all business logic directly into tRPC procedure handlers. Keep your procedures thin — they should validate input, call a service/repository layer, and return results. Business logic and database access should live in separate modules that the procedure calls. This keeps your code testable and allows you to swap tRPC for REST or GraphQL later without rewriting your core logic .

## Footnotes

1.  [Building Production-Ready tRPC APIs - InfoQ](https://www.infoq.com/articles/building-trpc-api-typescript) - Production migration story: 2.4M requests/day, 99.97% uptime, error formatting, and middleware patterns [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
    

more...

### 

Developer Experience: Time to First Working API

Relative effort comparison (lower is better)

### tRPC with Next.js — Minimal Setup (Pages Router)

1.  1
    
    Step 1
    
    Install Dependencies
    
    `1npm install @trpc/server @trpc/client @trpc/react-query @trpc/next @tanstack/react-query@latest zod superjson`
    
2.  2
    
    Step 2
    
    Create the Server (API Route)
    
    In `pages/api/trpc/[trpc].ts`:
    
    `1import { createNextApiHandler } from '@trpc/server/adapters/next'; 2import { appRouter } from '@/server/routers/_app'; 3import { createContext } from '@/server/context'; 4 5export default createNextApiHandler({ 6 router: appRouter, 7 createContext, 8 onError: ({ error }) => { 9 console.error('tRPC Error:', error); 10 }, 11}); 12 13// Next.js config 14export const config = { api: { bodyParser: false } }; // Allow batching`
    
3.  3
    
    Step 3
    
    Create tRPC React Hooks
    
    In `utils/trpc.ts`:
    
    `1import { createTRPCNext } from '@trpc/next'; 2import type { AppRouter } from '@/server/routers/_app'; 3import { httpBatchLink } from '@trpc/client'; 4import superjson from 'superjson'; 5 6export const trpc = createTRPCNext<AppRouter>({ 7 config: () => ({ 8 links: [ 9 httpBatchLink({ 10 url: '/api/trpc', 11 transformer: superjson, 12 }), 13 ], 14 }), 15 ssr: true, // Enable server-side rendering of tRPC queries 16});`
    
4.  4
    
    Step 4
    
    Wrap Your App with the tRPC Provider
    
    In `pages/_app.tsx`:
    
    `1import { trpc } from '@/utils/trpc'; 2 3function MyApp({ Component, pageProps }) { 4 return <Component {...pageProps} />; 5} 6 7export default trpc.withTRPC(MyApp);`
    
    Now every component in your app can use `trpc.*.useQuery()` and `trpc.*.useMutation()` hooks with full type safety and autocomplete .
    
    ## Footnotes
    
    1.  [tRPC Next.js Pages Router Setup](https://trpc.io/docs/client/nextjs/pages-router/setup) - Official guide for integrating tRPC with Next.js Pages Router [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
        
    
5.  5
    
    Step 5
    
    Use tRPC in Components
    
    In any React component:
    
    `1import { trpc } from '@/utils/trpc'; 2 3function Dashboard() { 4 const { data, isLoading, error } = trpc.userList.useQuery(); 5 const createUser = trpc.userCreate.useMutation(); 6 7 const handleCreate = () => { 8 createUser.mutate({ name: 'New User' }); 9 }; 10 11 if (isLoading) return <div>Loading...</div>; 12 if (error) return <div>Error: {error.message}</div>; 13 14 return ( 15 <div> 16 {data?.map(user => <p key={user.id}>{user.name}</p>)} 17 <button onClick={handleCreate}>Add User</button> 18 </div> 19 ); 20}`
    

#### Pro Tip: Error Formatting with Zod

When using Zod for input validation, configure a custom error formatter on your tRPC instance to send structured validation errors to the client:

`1const t = initTRPC.context<Context>().create({ 2 errorFormatter({ shape, error }) { 3 return { 4 ...shape, 5 data: { 6 ...shape.data, 7 zodError: error.cause instanceof ZodError 8 ? error.cause.flatten() 9 : null, 10 }, 11 }; 12 }, 13});`

This lets the client access `error.data.zodError.fieldErrors` to show per-field validation messages in your form UI .

## Footnotes

1. [Building Production-Ready tRPC APIs - InfoQ](https://www.infoq.com/articles/building-trpc-api-typescript) - Production migration story: 2.4M requests/day, 99.97% uptime, error formatting, and middleware patterns [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 

more...

### Knowledge Check

Question 1 of 5

Q1Single choice

What is the primary mechanism that enables tRPC's end-to-end type safety without code generation?

The server generates a JSON schema at build time

The client imports the AppRouter type from the server codebase

tRPC uses GraphQL SDL under the hood

Code generation is run automatically in a pre-commit hook

BackNext

## Explore Related Topics

[1\\ \\ AI Safety\\ \\ AI safety ensures AI systems remain robust, interpretable, controllable, and aligned with human goals, preventing harmful or unintended outcomes across their lifecycle.\\ \\ - Key pillars are alignment, robustness, interpretability, and control, supported by operational practices (monitoring, incident response, governance) such as the NIST AI RMF’s Govern‑Map‑Measure‑Manage cycle. - Safety seeks to lower expected harm Expected Harm\=∑iP(failurei)×Impact(failurei)\\text{Expected Harm} = \\sum\_i P(\\text{failure}\_i)\\times \\text{Impact}(\\text{failure}\_i)Expected Harm\=∑i​P(failurei​)×Impact(failurei​) by cutting failure probabilities and impacts. - Frontier model assessments use benchmark tests, red teaming, open‑ended and elicitation‑aware evaluations, with risk thresholds deciding deployment. - A defense‑in‑depth strategy blends data curation, model safeguards, system limits, human oversight, and continuous monitoring, recognizing no single measure is sufficient.](https://coursify.hasanraiyan.me/research/ai-safety) [2\\ \\ Learn React in 30 Days: A Comprehensive Course\\ \\ Learn React in 30 Days: From Zero to Production](https://coursify.hasanraiyan.me/research/learn-react-in-30-days-a-comprehensive-course) [3\\ \\ TCP/IP Networking: The Architecture of the Internet\\ \\ This course covers the TCP/IP suite’s four‑layer architecture, key protocols, connection setup, addressing, and security considerations.\\ \\ - Each TCP/IP layer adds its own header via encapsulation, moving data from a process to the physical medium. - TCP is reliable and connection‑oriented; UDP is fast, connectionless with a small 8‑byte header. - The 3‑way handshake uses SYN, SYN‑ACK, then ACK to establish a TCP connection. - IPv4 uses 32‑bit addresses; IPv6 uses 128‑bit, and subnet masks define network vs host bits. - Ports 0‑1023 are well‑known (e.g., 80 for HTTP); IP spoofing is a security threat.](https://coursify.hasanraiyan.me/research/tcpip-networking-the-architecture-of-the-internet)

[![Coursify logo](https://coursify.hasanraiyan.me/_next/image?url=%2Fimages%2Fapps%2Fcoursify.png&w=48&q=75)Browse all research articles](https://coursify.hasanraiyan.me/research)