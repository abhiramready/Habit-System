## Learn Programming 2023 🧑‍💻

## January - May
- Worked on Redux and Sagas
- Working on Cart and Checkout flow
- Creating reusable and configurable components with atomic design pattern
- Implemented a complete Checkout Re-design with minimal and modern UI

✅ **GitHub Contributions this year**
![image](https://github.com/abhiramready/Habit-System/assets/40287643/99c23a37-d5ad-4057-bb42-6ee253da26d6)


## June
### Catching up with React 18
- [React 18 New Features](https://www.freecodecamp.org/news/react-18-new-features/) ⭐
- [10 React Hooks Explained](https://www.youtube.com/watch?v=TNhaISOUy6Q) - Video by Fireship ⭐
- [React Testing Library Tutorial](https://www.robinwieruch.de/react-testing-library/) ⭐
- [React useRef() Hook Explained in 3 Steps](https://dmitripavlutin.com/react-useref/)  - Dmitri Pavlutin
- [React's useReducer Hook vs Redux](https://www.robinwieruch.de/redux-vs-usereducer/) - Robin
- [Generator functions in JS](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) - MDN
- [Your Guide to React.useCallback()](https://dmitripavlutin.com/react-usecallback/) - Dmitri Pavlutin
- [JavaScript Callback Functions and How to Use Them](https://www.freecodecamp.org/news/javascript-callback-functions-what-are-callbacks-in-js-and-how-to-use-them/) - FreeCodeCamp

### Learning [Next.js](https://nextjs.org/learn/foundations/about-nextjs)
Next.js has two forms of pre-rendering:  

Static Generation and Server-side Rendering. The difference is in when it generates the HTML for a page.
- SSG Static Generation is the pre-rendering method that generates the HTML at build time. The pre-rendered HTML is then reused on each request.
- SSR Server-side Rendering is the pre-rendering method that generates the HTML on each request.

#### Client-side Rendering in Next.js
- When the page loads, fetch external data from the client using JavaScript and populate the remaining parts.
- This approach works well for user dashboard pages, for example. Because a dashboard is a private, user-specific page, SEO is not relevant, and the page doesn’t need to be pre-rendered. The data is frequently updated, which requires request-time data fetching.

#### Server-side Rendering
```javascript
// context contains request-specific parameters.
export async function getServerSideProps(context) {
  return {
    props: {
      // props for your component
    },
  };
}
```
