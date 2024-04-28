# next-typed-mdx

A lib for you to 
1. Integrate MDX parsing blog / docs into your next.js typescript project
2. serve as a starter for standalone blog / docs repos.

## Features 
1. Type checking MDX parse results
2. Static Site Generation
3. Grey matter info parsing
4. i18n

All in one config
```
// typed-mdx.config.ts
export default {
  mdxDir: process.cwd() + "/blogs",
  transformMdxResult: (result: {slug: string; data: Record<string, unknown>, markdown: string}) => {
    return zMdxResult.parse(result);
  },
}
```

Where you can configure `zMdxResult` as you wish
```
export const zMdxResult = z.object({
  slug: z.string(),
  data: z.object({
    title: z.string(),
    author: z.object({
      name: z.string(),
      picture: z.string(),
      twitterUrl: z.string(),
      twitterHandle: z.string(),
    }),
    "date": z.string(),
    "coverImage": z.string(),
    "coverImageAlt": z.string(),
    "excerpt": z.string().optional(),
    "draft": z.boolean(),
  }),
  markdown: z.string(),
});

```

## Info

A descendant of https://github.com/johnpolacek/nextjs-mdx-blog-starter with the following features

Powers [slidde.co/blogs](https://slidde.co/blogs)

