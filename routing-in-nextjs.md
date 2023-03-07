---

title: Routing in Next.js — The Complete guide!
description: Routing is an essential part of any web application, and Next.js provides a powerful and flexible system for handling it. Learn how to create simple and dynamic routes, customize URLs with dynamic parameters, and create nested routes in this comprehensive guide to routing in Next.js.
date: March 8, 2023
id: routing-in-nextjs

---

# Routing in Next.js

Routing is a fundamental part of any web application, allowing users to navigate between different pages and views. In Next.js, routing is handled by the built-in `Link` component, which makes it easy to create dynamic and SEO-friendly URLs for your pages.

## Creating Simple Routes

To create a simple route in Next.js, all you need to do is create a file in the `pages` directory with the name of the route. For example, to create a page at the URL `http://localhost:3000/about`, you would create a file at `pages/about.js`.

Here's an example `pages/about.js` file:

```javascript
function AboutPage() {
  return <h1>About Page</h1>
}

export default AboutPage
```

This file exports a simple component that renders an `h1` element with the text "About Page". When a user navigates to `http://localhost:3000/about`, they will see this page.

---

## Using the Link Component

Next.js provides a `Link` component that makes it easy to create links between pages. Instead of using the traditional `<a>` tag, you can use the `Link` component to create links that work with Next.js's routing system.

Here's an example of how to use the `Link` component:

```
import Link from 'next/link'

<Link href="/about">
  <a>About Us</a>
</Link>
```

This will create a link that displays as "About Us", but when the user clicks on it, they will be taken to the URL `http://localhost:3000/about`.

---

## Customizing URLs with Dynamic Routes

Next.js also makes it easy to create dynamic routes that can accept parameters. For example, you might want to create a page that displays information about a specific product, with a URL like `http://localhost:3000/products/123`.

To create a dynamic route in Next.js, you can use square brackets in the file name to indicate which part of the URL is dynamic. For example, to create a dynamic route at `http://localhost:3000/products/[id]`, you would create a file at `pages/products/[id].js`.

Here's an example `pages/products/[id].js` file:

```
function ProductPage({ id }) {
  return <h1>Product {id}</h1>
}

export async function getServerSideProps(context) {
  const { params } = context
  const id = params.id
  return { props: { id } }
}

export default ProductPage
```

The `getServerSideProps` function is used to fetch data for the page. In this case, we're using the `params` object to extract the `id` parameter from the URL. When a user navigates to `http://localhost:3000/products/123`, they will see a page with the text "Product 123".

To create a link to a dynamic route, you can use the `Link` component with an object that contains the dynamic parameter. For example:

```
<Link href="/products/[id]" as="/products/123">
  <a>Product 123</a>
</Link>
```
This will create a link that displays as "Product 123", but when the user clicks on it, they will be taken to the dynamic URL `http://localhost:3000/products/[id]` with the `id` parameter set to `123`.

---

## Nested Routes

Next.js also supports nested routes, which allow you to create pages with more complex URLs. For example, you might want to create a page that displays information about a specific category of products, with a URL like `http://localhost:3000/products/electronics/123`.

To create a nested route in Next.js, you can use multiple square brackets in the file name to indicate the different dynamic parameters. For example, to create a nested route at `http://localhost:3000/products/[category]/[id]`, you would create a file at `pages/products/[category]/[id].js`.

Here's an example `pages/products/[category]/[id].js` file:

```
function ProductPage({ category, id }) {
  return (
    <>
      <h1>Category: {category}</h1>
      <h2>Product: {id}</h2>
    </>
  )
}

export async function getServerSideProps(context) {
  const { params } = context
  const category = params.category
  const id = params.id
  return { props: { category, id } }
}

export default ProductPage
```

When a user navigates to `http://localhost:3000/products/electronics/123`, they will see a page with the text "Category: electronics" and "Product: 123".

To create a link to a nested route, you can use the `Link` component with an object that contains both dynamic parameters. For example:

```
<Link href="/products/[category]/[id]" as="/products/electronics/123">
  <a>Electronics Product 123</a>
</Link>
```

This will create a link that displays as "Electronics Product 123", but when the user clicks on it, they will be taken to the nested URL `http://localhost:3000/products/[category]/[id]` with the `category` parameter set to `electronics` and the `id` parameter set to `123`.

---

## Conclusion

Routing is an essential part of any web application, and Next.js provides a powerful and flexible system for handling it. With Next.js, you can create simple static routes, dynamic routes with parameters, and even nested routes with multiple parameters. By using the `Link` component and the `getServerSideProps` function, you can create dynamic and SEO-friendly URLs that make it easy for users to navigate your site.

In this blog post, we've covered the basics of routing in Next.js, including creating simple routes, using the `Link` component, customizing URLs with dynamic routes, and creating nested routes. With this knowledge, you should be able to create robust and flexible routing systems for your Next.js applications.
