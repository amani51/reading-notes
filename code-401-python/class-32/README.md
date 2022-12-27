# Class-32
## Intro to Next.js & Tailwind CSS
#### What is Next Js
- Next.js is a React framework that gives you building blocks to create web applications.
- By framework, we mean Next.js handles the tooling and configuration needed for React, and provides additional structure, features, and optimizations for your application.
![](https://nextjs.org/static/images/learn/foundations/next-app.png)
---------------------
#### Tailwind CSS
![](data:image/png;base64,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)
- A utility-first CSS framework packed with classes like flex, pt-4, text-center and rotate-90 that can be composed to build any design, directly in your markup.
- **Why Tailwind CSS?**
    - Faster UI building process
    - It is a utility-first CSS framework which means we can use utility classes to build custom designs without writing CSS as in the traditional approach.
- **Advantages of Tailwind CSS:**

    - No more silly names for CSS classes and Id’s.
    - Minimum lines of Code in CSS file.
    - We can customize the designs to make the components.
    - Makes the website responsive.
    - Makes the changes in the desired manner. 
    - CSS is global in nature and if make changes in the file the property is changed in all the HTML files linked to it. But with the help of Tailwind CSS we can use utility classes and make local changes.
- **Installation:** 
    There are two ways to use the CSS we can install them on our server or we can use the CDN link as well.
    - **Method 1**: Install Tailwind via `npm`
        1. `npm init -y`   
        2. `npm install tailwindcss`
        3. ```javascript
            @tailwind base;
            @tailwind components;
            @tailwind utilities;
            ```
        4. `npx tailwindcss init`
        5. `npx tailwindcss build styles.css -o output.css`
    - **Method 2**: Using Tailwind via `CDN`
        ```javascript
        <link href="https://unpkg.com/tailwindcss@^1.0/dist/tailwind.min.css"rel="stylesheet">
        ```
    - **Limitation of Tailwind**: But there are some limitations when CDN is used. Some of them are:

        - Customize Tailwind's default theme can't be used
        - Directives like @apply, @variants, etc can't be used
        - Can't install third-party plugins  
--------------
