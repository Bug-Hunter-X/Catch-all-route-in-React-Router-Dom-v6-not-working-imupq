# Catch all route in React Router Dom v6 not working

This repository contains a minimal reproducible example of a bug in React Router Dom v6. The catch all route is not working as expected. It should match any route that is not defined. However, it is not matching any route at all.

## Bug Description

The issue can be reproduced by running the code in `App.js`. The catch all route (`/*`) should match any route that is not defined, but it is not.

## Solution

The solution is to move the catch all route to the end of the routes array.

```javascript
import { BrowserRouter, Routes, Route } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </BrowserRouter>
  );
}

function Home() {
  return <h1>Home</h1>;
}

function About() {
  return <h1>About</h1>;
}

function NotFound() {
  return <h1>Not Found</h1>;
}
export default App;
```