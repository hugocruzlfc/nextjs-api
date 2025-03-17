## Deployment and “SPA Mode” considerations

Next.js can be deployed in two main ways:

### Standard Node.js deployment

The standard Next.js server deployment using next start enables you to use features like Route Handlers, Server Components, Middleware and more – while taking advantage of dynamic, request time information.

There is no additional configuration required. See [Deploying](https://nextjs.org/docs/app/building-your-application/deploying) for more details.

### SPA/Static Export

Next.js also supports outputting your entire site as a [static Single-Page Application (SPA)](https://nextjs.org/docs/app/building-your-application/upgrading/single-page-applications).

You can enable this by setting:

```typescript
import type { NextConfig } from "next";

const nextConfig: NextConfig = {
  output: "export",
};

export default nextConfig;
```

In static export mode, Next.js will generate purely static HTML, CSS, and JS. You cannot run server-side code (like API endpoints). If you still need an API, you’d have to host it separately (e.g., a standalone Node.js server).

### Note

GET Route Handlers can be statically exported if they don’t rely on dynamic request data. They become static files in your out folder.
All other server features (dynamic requests, rewriting cookies, etc.) are not supported in a pure SPA export.

## Deploying APIs on Vercel

If you are deploying your Next.js application to Vercel, we have a guide on [deploying APIs](https://vercel.com/guides/hosting-backend-apis). This includes other Vercel features like [programmatic rate-limiting](https://vercel.com/docs/vercel-waf/rate-limiting-sdk) through the Vercel Firewall. Vercel also offers [Cron Jobs](https://vercel.com/docs/cron-jobs/manage-cron-jobs), which are commonly needed with API approaches.
