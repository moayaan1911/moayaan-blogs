---
title: "Get Started with Tailwind CSS"
datePublished: Sun Mar 12 2023 14:26:37 GMT+0000 (Coordinated Universal Time)
cuid: clf5ho9ol000c09lf247ua9kd
slug: get-started-with-tailwind-css
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678630914337/253ce51c-a199-4ebe-b5fc-a6f55091765b.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1678631172163/fb9cb4b7-6acb-46b9-a09a-55db10b5746e.jpeg
tags: css, design, html5, ui, tailwind-css

---

Tailwind CSS is a popular utility-first CSS framework that provides pre-designed classes to style your HTML elements. It aims to improve development speed by eliminating the need for writing custom CSS code.

## Advantages of Tailwind CSS:

* It enables you to style your HTML elements without writing custom CSS code.
    
* You can quickly create responsive designs using Tailwind's responsive utility classes.
    
* It's easy to customize the framework and create your own classes.
    
* Tailwind provides excellent documentation, making it easy to learn and use.
    

## Disadvantages of Tailwind CSS:

* It can make your HTML code look cluttered with many classes.
    
* It may not be suitable for large-scale projects where custom design is a priority.
    

## Getting started with Tailwind CSS:

Step 1: Install Tailwind CSS You can install Tailwind CSS using npm or yarn.

Using npm:

```bash
npm install tailwindcss
```

Using yarn:

```bash
yarn add tailwindcss
```

Step 2: Create a Tailwind configuration file Tailwind CSS comes with a default configuration file that you can customize according to your needs. To create a configuration file, use the following command:

```bash
npx tailwindcss init
```

Step 3: Create a CSS file Create a new CSS file and import the Tailwind CSS styles using `@tailwind` directive:

```bash
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Step 4: Start using Tailwind classes in your HTML You can now start using Tailwind classes to style your HTML elements. Here's an example:

```xml
<div class="flex justify-center items-center bg-gray-100 h-screen">
  <div class="bg-white rounded-lg p-6 shadow-lg">
    <h1 class="text-2xl font-bold mb-4">Hello, Tailwind CSS!</h1>
    <p class="text-gray-700">This is a sample paragraph using Tailwind classes.</p>
    <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-4">Click me!</button>
  </div>
</div>
```

In the example above, we used the `flex`, `justify-center`, `items-center`, `bg-gray-100`, `bg-white`, `rounded-lg`, `p-6`, `shadow-lg`, `text-2xl`, `font-bold`, `mb-4`, `text-gray-700`, `bg-blue-500`, `hover:bg-blue-700`, `text-white`, `py-2`, `px-4`, `rounded`, and `mt-4` classes to style our HTML elements.

Note that Tailwind's classes follow a specific naming convention that uses abbreviations to represent the properties they set. For example, `bg` stands for `background-color`, `p` stands for `padding`, and `mx` stands for `margin-x`.

## Some More Examples:

```xml
<div class="container mx-auto">
  <div class="grid grid-cols-2 gap-4">
    <div class="p-6 bg-white shadow-md rounded-lg">
      <h2 class="text-lg font-semibold mb-2">First item</h2>
      <p class="text-gray-700">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
    </div>
    <div class="p-6 bg-white shadow-md rounded-lg">
      <h2 class="text-lg font-semibold mb-2">Second item</h2>
      <p class="text-gray-700">Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
    </div>
  </div>
</div>
```

In this example, we used the `container`, `mx-auto`, `grid`, `grid-cols-2`, `gap-4`, `p-6`, `bg-white`, `shadow-md`, `rounded-lg`, `text-lg`, `font-semibold`, and `text-gray-700` classes. The `container` class centers the content horizontally and adds some padding to the sides. The `mx-auto` class centers the container horizontally. The `grid` and `grid-cols-2` classes create a two-column grid layout. The `gap-4` class adds a gap of 4 units between the grid items. The `p-6`, `bg-white`, `shadow-md`, and `rounded-lg` classes style the individual grid items. The `text-lg`, `font-semibold`, and `text-gray-700` classes style the headings and paragraphs inside the grid items.

```xml
<div class="flex items-center justify-center bg-gray-100 h-screen">
  <div class="w-64 bg-white rounded-lg shadow-lg overflow-hidden">
    <img class="h-48 w-full object-cover" src="https://picsum.photos/seed/picsum/200/300" alt="A random image">
    <div class="p-4">
      <h2 class="text-lg font-semibold mb-2">Product title</h2>
      <p class="text-gray-700 mb-2">$19.99</p>
      <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Add to cart</button>
    </div>
  </div>
</div>
```

In this example, we used the `flex`, `items-center`, `justify-center`, `bg-gray-100`, `h-screen`, `w-64`, `bg-white`, `rounded-lg`, `shadow-lg`, `overflow-hidden`, `h-48`, `w-full`, `object-cover`, `p-4`, `text-lg`, `font-semibold`, `text-gray-700`, `bg-blue-500`, `hover:bg-blue-700`, `text-white`, `font-bold`, `py-2`, `px-4`, and `rounded` classes. The `flex`, `items-center`, `justify-center`, `bg-gray-100`, and `h-screen` classes center the content both horizontally and vertically on the screen. The `w-64`, `bg-white`, `rounded-lg`, `shadow-lg`, and `overflow-hidden` classes style the container for the product. The `h-48`, `w-full`, and `object-cover` classes style the product image.

```xml
<div class="bg-gray-200 py-10">
  <div class="container mx-auto">
    <h1 class="text-3xl font-bold text-center mb-8">Frequently Asked Questions</h1>
    <div class="accordion">
      <div class="accordion-item">
        <h2 class="accordion-header">
          <button class="accordion-button">
            What is Tailwind CSS?
          </button>
        </h2>
        <div class="accordion-content">
          <p>
            Tailwind CSS is a utility-first CSS framework for rapidly building custom user interfaces. It provides a set of pre-defined classes that you can use to style your HTML elements.
          </p>
        </div>
      </div>
      <div class="accordion-item">
        <h2 class="accordion-header">
          <button class="accordion-button">
            How do I install Tailwind CSS?
          </button>
        </h2>
        <div class="accordion-content">
          <p>
            You can install Tailwind CSS using npm or yarn. To install it with npm, run the following command:
          </p>
          <code class="bg-gray-100 px-2 py-1 rounded-md mt-2 inline-block">npm install tailwindcss</code>
          <p>
            After that, you need to create a configuration file for Tailwind CSS and import it into your CSS file. You can find more information about this in the official Tailwind CSS documentation.
          </p>
        </div>
      </div>
      <div class="accordion-item">
        <h2 class="accordion-header">
          <button class="accordion-button">
            Can I customize the styles in Tailwind CSS?
          </button>
        </h2>
        <div class="accordion-content">
          <p>
            Yes, you can customize the styles in Tailwind CSS by modifying the configuration file. You can change the colors, fonts, spacing, and more. Tailwind CSS provides a lot of flexibility in this regard.
          </p>
        </div>
      </div>
    </div>
  </div>
</div>
```

In this example, we used the `bg-gray-200`, `py-10`, `container`, `mx-auto`, `text-3xl`, `font-bold`, `text-center`, `mb-8`, `accordion`, `accordion-item`, `accordion-header`, `accordion-button`, `accordion-content`, `bg-gray-100`, `px-2`, `py-1`, `rounded-md`, `mt-2`, and `inline-block` classes. The `bg-gray-200` and `py-10` classes style the background and padding of the container. The `container`, `mx-auto`, `text-3xl`, `font-bold`, `text-center`, and `mb-8` classes style the heading. The `accordion`, `accordion-item`, `accordion-header`, `accordion-button`, and `accordion-content` classes create an accordion menu with expandable sections. The `bg-gray-100`, `px-2`, `py-1`, `rounded-md`, `mt-2`, and `inline-block` classes style the code snippet inside one of the accordion sections.

## Login Page using Tailwind

```xml
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login Page</title>
    <!-- Include the Tailwind CSS framework -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/tailwindcss/2.1.2/tailwind.min.css">
  </head>
  <body class="bg-blue-500">
    <div class="flex items-center justify-center h-screen">
      <div class="w-full max-w-md">
        <div class="bg-white shadow-md rounded px-8 py-6">
          <div class="text-center">
            <img class="h-12 w-auto" src="https://picsum.photos/seed/picsum/200/200" alt="Logo">
            <h1 class="text-2xl font-bold text-gray-800 mt-2">Log In</h1>
          </div>
          <form class="mt-6">
            <div class="mb-4">
              <label class="block text-gray-700 font-bold mb-2" for="username">
                Username
              </label>
              <input class="appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username" type="text" placeholder="Username">
            </div>
            <div class="mb-6">
              <label class="block text-gray-700 font-bold mb-2" for="password">
                Password
              </label>
              <input class="appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="password" type="password" placeholder="Password">
            </div>
            <div class="flex items-center justify-between">
              <button class="bg-blue-700 hover:bg-blue-800 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
                Log In
              </button>
              <a class="inline-block align-baseline font-bold text-sm text-blue-700 hover:text-blue-800" href="#">
                Forgot Password?
              </a>
            </div>
          </form>
        </div>
      </div>
    </div>
  </body>
</html>
```

The body of the HTML document contains a div that is centered using the flexbox layout with the help of the "flex" and "items-center" classes. The div contains another div with the class "bg-white" that provides a white background for the login form. The form itself is created with the HTML "form" element.

Inside the form, there are two input fields for the username and password, respectively. Both input fields are styled with the "appearance-none", "border", "rounded", "py-2", "px-3", "text-gray-700", "leading-tight", "focus:outline-none" and "focus:shadow-outline" classes. These classes provide a consistent and clean style for the input fields.

The "flex" and "items-center" classes are used to center the "Log In" button and "Forgot Password?" link below the input fields. The "bg-blue-700" and "hover:bg-blue-800" classes provide a blue background color for the "Log In" button and a darker blue background color when the button is hovered over with the mouse. The "text-white" class sets the text color to white and the "font-bold", "py-2", and "px-4" classes provide additional styling for the button.

The "inline-block", "align-baseline", "font-bold", "text-sm", "text-blue-700", and "hover:text-blue-800" classes are used for the "Forgot Password?" link. The link is displayed as an inline block element with baseline alignment, and the font is bold with a small size. The text color is blue, and it changes to a darker blue when the link is hovered over with the mouse.

Finally, there is an image of a logo that is displayed with the help of the "img" tag and styled with the "h-12" and "w-auto" classes, which set the height to 12 units and the width to auto, respectively.

## Landing Page using Tailwind

```xml
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crypto Landing Page</title>
    <!-- Include the Tailwind CSS framework -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/tailwindcss/2.2.15/tailwind.min.css">
  </head>
  <body class="bg-gray-100">
    <nav class="bg-white shadow">
      <div class="container mx-auto px-4">
        <div class="flex justify-between items-center py-4">
          <div class="flex justify-start">
            <a class="text-gray-900 font-bold text-xl" href="#">Crypto Site</a>
          </div>
          <div class="flex">
            <a class="text-gray-900 text-sm mr-4" href="#">Home</a>
            <a class="text-gray-900 text-sm mr-4" href="#">About</a>
            <a class="text-gray-900 text-sm" href="#">Contact</a>
          </div>
        </div>
      </div>
    </nav>
    
    <div class="container mx-auto my-8 px-4">
      <div class="flex flex-col md:flex-row md:items-center md:justify-between">
        <div class="md:w-1/2">
          <h1 class="text-4xl font-bold text-gray-900">Welcome to Crypto Site</h1>
          <p class="text-lg text-gray-800 mt-4">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis feugiat ex vitae lorem pulvinar elementum. Nulla facilisi. Nam sit amet dictum leo.</p>
          <div class="mt-8">
            <a href="#" class="bg-blue-700 hover:bg-blue-800 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">Learn More</a>
          </div>
        </div>
        <div class="md:w-1/2 mt-8 md:mt-0">
          <img src="https://picsum.photos/seed/picsum/800/600" class="rounded-lg shadow-lg">
        </div>
      </div>
    </div>
    
    <!-- Include the Tailwind CSS framework -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/tailwindcss/2.2.15/tailwind.min.js"></script>
  </body>
</html>
```

The first section contains the navigation bar, which is styled with a white background and a drop shadow effect. The logo and links are aligned with flexbox and are responsive on different screen sizes.

The second section contains a heading, paragraph, and call-to-action button, all styled with different text sizes, colors, and spacing. The button is styled with a blue background and white text color on hover. The image on the right side is responsive and has rounded corners and a shadow effect.

The page is made responsive by using the grid system of Tailwind CSS. The container element is centered using the `mx-auto` class, and different classes are used to adjust the width and order of the elements on different screen sizes.

Overall, this code uses basic HTML markup with Tailwind CSS classes to create a responsive and visually appealing landing page for a crypto site.

## Conclusion:

Tailwind CSS is a great choice for projects that require fast development and prototyping. By providing pre-designed classes, it eliminates the need for writing custom CSS code, which can save you time and effort. However, it may not be the best choice for large-scale projects that require custom design and optimization.