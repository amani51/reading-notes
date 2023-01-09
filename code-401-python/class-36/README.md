# Class-36
## Data Fetching 
### What is SWR
![](https://blog.openreplay.com/static/6d7149290210e561d8424f0ca10bb234/99fbb/hero.webp)
- SWR stands for `stale-while-revalidate`, a HTTP cache invalidation strategy popularized by HTTP RFC 5861. It basically means that it performs data fetching in 3 steps:

    1. Returns cached data first (stale)
    2. Sends the fetch request (revalidate)
    3. Returns the up-to-date data
- SWR is created by **Vercel** and one of its advantages is that it is a fast and lightweight package.
- **Why use SWR?**
    1. Built-in Cache + Real-Time Experience
        Using SWR’s strategy, the user sees the cached (stale) data first and requests are `automatically being cached`. Components will always be constantly updated with the most recent data, ensuring UI will always be `fast and reactive.`
    2. Auto Revalidation
        - SWR ensures that the user sees the most up-to-date data. So even with multiple tabs or windows, the data is always fresh and in sync when the window/tab is refocused.
        - SWR can also revalidate data on interval, to make sure multiple sessions will render the same components based on the data.
        - In the event the user disconnects from the internet, SWR will automatically revalidates data once the user is online again.
        ![](https://blog.openreplay.com/a3042d7185623fdfbf7192e6ea76904e/img1.gif)
    3. Pagination
        Instead of having to write your own logic with Fetch or Axios to paginate data or create an infinite loading UI for your app, SWR provides a simple Hook called `useSWRInfinite` to handle this for you.
        ![](https://blog.openreplay.com/8c0901932998513664048ba4ec11f144/img2.gif)
    4. More Features + Benefits of SWR
        - Local mutation
        - Dependent fetching
        - Smart error retry
        - Supports fetching from both REST and GraphQL APIs
        - Typescript and React Native ready