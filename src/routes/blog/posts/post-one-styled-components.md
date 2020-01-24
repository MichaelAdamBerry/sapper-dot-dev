---
title: Styled Components
date: 2019-09-20T12:51:00.000Z
---

Why Styled Components Make Sense in React and How to Get Started Using Them

<!-- more -->

## The Benefits of Styled Components

Web Components, Javascript frameworks like React, and UI design systems all share a common vision of client side web archetechture being composed with small, reusable, and self sufficient pieces.

Here are a few examples of the different types of components we typically construct in React and how styled components can help us simplify things.

These examples will all render a button that will update its background color when clicked.

In React we tend to think about component composition as being either stateless, or having state.

State-ful Components have local state which that need to indicate an update when that state change.

### A Button Component With State

```jsx
//Button.js
import React, {useState} from 'react';
const Button = () ⇒ {
  const [isClicked, toggleClicked] = useState(false)
  return (
    <button className={isClicked && "clicked"}>{!isClicked ? "Click Me" : "I've Been Clicked"}</button>
  )
}
export default Button;
```

```css
/* index.css */
.clicked {
  background-color: magenta;
}
```

Components can also recieve props from a parent component that will contain instuctions of how the components are rendered.

### A Stateless Component Recieving Prop Data From Parent

```jsx
// Button.js
  import React from 'react';
  const Button = ({onClick, isClicked}) ⇒ {
    return (
    <button onClick={onClick} className={isClicked && "clicked"}</button>
    )
  }

  export default Button;
```

```jsx
// Parent.js
  import React, {useState} from 'react';
  import Button from "./Button.js";

  const Parent = () ⇒ {
    const [isClicked, toggleClick] = useState(false);
    return (
    <Button onClick={toggleClick} isClicked={isClicked} />
    )
  }

  export default Button;
```

```css
/* index.css */
.clicked {
  background-color: magenta;
}
```

## Code Organization

If we could include our styles within our Javascript we would be able to organize code in a clearer and more maintainable manner.

This brings us to the core concept here of **colocation**. I learned about this concept in this excellent blog post by Kent C. Dodds.

[Read Kent's Post on Colocation Here](https://kentcdodds.com/blog/colocation)

Here's how Kent breaks this concept down with nice assist from Dan Abramov :

> "The concept of co-location can be boiled down to this fundamental principle: Place code as close to where it's relevant as possible. You might also say: 'Things that change together should be located as close as reasonable. (Dan Abramov said something like this to me once)."

This concept of organizing code based on the way the user experiences the code is fundamental in React.
It's why writing JSX. It seems intuitive that we should be describing / templating how our html is rendered along side our relevant javascript logic.

By adding styles to this equation we can go a stem further and create fully fledged components that include the components logic, descriptions of html structures, and styling. Our components are resuable, flexible, customizable while also resembling what you or your web designer intended.

## A Styled Component

### Example of a Styled Button Component

```jsx
//Button.js
import React, {useState} from 'react';
import StyledButton from "./StyledButton";

  const Button = () ⇒ {
    const [isClicked, toggleClicked] = useState(false)
    return <StyledButton isClicked={isClicked} />
  }

  export default Button;
```

```jsx
// StyledButton.js
import styled from "@emotion/styled"
const StyledButton = styled.button`
  background-color: ${ props => props.clicked && 'magenta' };`
};
```

Styled Components can be exported and reused throughout a project the same way a react component can be.

So can ditch the unnecessary className elements and reduce the code in our potentially sprawling css files.

And with the help of props, we can customize specific instances while keeping our code DRY.

IMHO this is both more readable and declarative code.

Refactoring components in this system becomes way less stressful because you don't have to comb through a giant file and with locally scoped styles colocated with Javascript we know exactly what we are changing.

## Styled JSX in Next.js

Here's another way you can achieve these goals using Styled JSX which is the out-of-box method of styling a Next.js application.

### Example Styled JSX Component (Default in Next.js)

```jsx
//Button.js in Next.js project
import React, {useState} from 'react';

const Button = () ⇒ {
  const [isClicked, toggleClicked] = useState(false)
  return (
    <>
    <button className={isClicked && "clicked"}>Click to Change Color</button>
    <style jsx>{`
      button.clicked  {
      background-color: "magenta";
      }`
    <style>
    </>
  )
}
export default Button;
```

Here you just wrap the css in a template literal inside a style tag and write css as you normally would in a stylesheet.

Personally I prefer using styed components for it's flexibility and reuseability. Emotion is my go-to library as there are plugins across frameworks. It also allows nesting styles.

Check out the emotion documentation [Here](https://emotion.sh/docs/styled)

And if you want to read more about styled components this article by Nwose Lotanna gives an in depth run down

[8 Reasons to Use Styled Components](https://www.notion.so/adamsdevstuff/8-reasons-to-use-styled-components-LogRocket-Blog-04bd5e5d69f14b4c8f2dc57b03377c94#03d780e0d5db4c24b81d70875203d894)
