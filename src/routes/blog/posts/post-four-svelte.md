---
title: Introduction to Svelte
date: 2019-10-24T12:51:00.000Z
---

Behold - The Framework That Was Promised.

<!-- more -->

_This is the first post in a series about my journey learning Svelte. I'm certainly not a Svelte expert yet, but I've worked through the tutorial in the official docs and am working on an survey application. As such, this first post is in some ways more about React, the reasons I'm interested in learning a new approach, and my first impressions of Svelte_

## Tl;dr

It's awesome! Good choice for a first framework as very similar thought model to vanilla javascript. Opinionated in all the right ways. Productivity gains you get out-of-the-box make learning Svelte well worth it.

## Looking for an Alternative to React

I began learning React in 2017 and it was my first Javascript framework (I know it's technically a "library" but c'mon ... ) . At the time I was in a "full stack" online program Udacity was offering and I started realizing that the curriculum didn't match any of the things I was seeing in job postings. I didn't see anyone listing Handlebars or Backbone in their tech stacks but almost everyone post lists React.

So I learned React, and it's been great. I think anyone whose main focus is getting their first development job should definitely start with React. It's such a dominating force in the front-end ecosystem and if you want to be as employable as possible, being a React developer is key.

On the other hand, I think that because React was my first framework I might not have realized what a paradigm shift React from frameworks before it and just vanilla javascript.

Here are the reasons I've been wanting to explore something new:

1. I often feel like personal projects I make don't need to have so much code and the structure that React insists upon. A common thought I have is this ... "this is too much code. This feels like it should be simpler. " So I'll spend time researching how I can eliminate unnecessary code and usually it doesn't amount to much of a difference. I do like the way React helps me organize my components and I've spent so much time investing in learning it so then I would think, "I guess I should just stick to this. I just learned hooks, damnit!"
2. React was developed and is maintained by Facebook. It seems like all the developers on the React team are great people but from a sustainability, moral, and political perspective I think the idea that companies owning web technologies as widespread and critical as React has become is crazy. Facebook is starting to look very Evil Empire these days tbh.

## Why Svelte Seemed Interesting or Why Not Vue

I haven't learned Vue yet, it was honestly next on my list until I saw this talk by Rich Harris which is a great introduction to the reasoning and foundational underpinnings of Svelte by it's creator Rich Harris.

Rich works at the New York Times as a graphic editor and his name is often underneath all those badass data visualizations and interactives you'll see on the Upshot or NYTimes/interactive. After getting started with Svelte this totally makes sense. This framework feels like it was designed to help people create applications efficiently and quickly. And with the amount of content that The New York Times puts out everyday... I can imagine quick and efficient would be good things.

## The Basics

The scope of this initial post is not to be a full tutorial. So here are what I see as the basics —

- Svelte's not actually new. Version 1 was released in 2016 and is currently on version 3.12.1. Significant changes were made when version 3 was realeased in the Spring of '19. And due to the simplicity of the framework, they do not anticipate many breaking changesmoving forward.
- Svelte's main selling point is that it eliminates the need for a virtual DOM. Instead there is build phase which transforms all the .svelte files to plain javascript. This reduces the amount of code that is shipped to browser as svelte doesn't need to ship a Svelte library with the code.
- This feels natural to me. I've been steeped in JAM stack development for a while now building projects with Gatsby and Next. Before Next and Gatsby sites deploy there is a build phase to convert code to static HTML which is rehydrated in the browser.

Here's the basic structure of a component in Svelte —

### App.Svelte

```html
<script>
  let name= "Adam Berry"
  let interests = ["movies", "music", "magic the gathering"];
  let show = false;
</script>

<style>
  section {
    width: 300px;
    margin: auto;
  }
  h2 {
    font-size: 2rem;
  }
</style>

<section class="bioSection">
  <h2 class="bioHeader">{name}</h2>
  <img class="bioImg" src="htpps://...." alt="avatar"/>
  <button on:click={() => show = true}>Toggle</button>
  {#if show}
    <p class="bioP">
      This is where I write about the things that I like.
    </p>
    <ul>
      {#each interests as interest}
      <li>{interest}</li>
      {/each}
    </ul>
  {/if}
</section>
```

As you can see, this is a pretty familiar looking structure. We have script tags where we write our javascript. Style tags contain CSS that is scoped to this component, and we are writing regular html with a few quirky additional curly braces, hashtags, and javascript keywords.

## 🤨 "Please Explain:"

Ok, here's a run down of the Svelte specific syntax that ties this little useless component together —

## 1. Conditions

We can define conditionally rendered html with this pattern:

### if/else Statements

```html
<div>
  {#if something === true }
  <div>...</div>
  {:else}
  <div>...</div>
  {/if}
</div>
```

## 2. Loops

We can iterate through an array to render lists using this pattern:

```html
{#each list as item}
<div>{item}</div>
{/each}
```

## 3. Event Handling With Directives

We can handle events like clicks with what Svelte defines as Element Directives. As you can give elements attributes so can you _direct_ how it should behave

Directives are one of the coolest features and deserve a whole post of their own, but here we can simply direct the button to fire our callback function when a click event occurs like this :

```html
<button on:click="{<callback" fn>}>A Svelte Button</button>
```

So that wraps up this first Svelte Post and I'm excited to keep diving deeper in the posts to come.
