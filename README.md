# Frontend Mentor - 3-column preview card component solution

This is a solution to the [3-column preview card component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/3column-preview-card-component-pH92eAR2-). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
- [Author](#author)
- [Acknowledgments](#acknowledgments)

## Overview

### **The challenge**

Users should be able to:

- View the optimal layout depending on their device's screen size
- See hover states for interactive elements

### **Screenshot**

![](screenshots/finished-screenshot.png)

### **Links**

- Live Site URL: [Add live site URL here](https://your-live-site-url.com)

## **My process**

Firstly I placed all the html content that was needed, once it was all on the page I went into the chrome dev tools, and changed the screen size to be 375px, since that was the start dimensions for the mobile.

Started wrapping content into the appropriate semantic tags, main, sections.

Gave all the sections a h2 element, even though there is no h1 element on the page, this is because I think the h2 semantic better fits the purpose here.

Once I had grouped and styled the content for the appropriate dimension, I started slowly increasing the screen size to find the best size to break the layout into an horizontal style layout, which I found to be 857px. So added a min-width media querie for this size.

### **Built with**

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Mobile first workflow

### **What I learned**

I realized that text can be a bit tricky to have match up in a way so it doesn't push other content out of its placement, if it didn't match up the buttons wouldn't end up properly aligned.

I also tried to find a way to reduce the code I've used on the hover effects:

```css
#sedan button:hover {
  background-color: transparent;
  color: hsl(0, 0%, 95%);
}
#suv button:hover {
  background-color: transparent;
  color: hsl(0, 0%, 95%);
}

#luxury button:hover {
  background-color: transparent;
  color: hsl(0, 0%, 95%);
}
```

By applying these:

```css
main button:hover {
  background-color: transparent;
  color: hsl(0, 0%, 95%);
}

section button:hover {
  background-color: transparent;
  color: hsl(0, 0%, 95%);
}

section:last-child:hover {
  background-color: transparent;
  color: hsl(0, 0%, 95%);
}
```

But sadly none of them worked, and I'm not sure why.

Another redundancy I tried to eliminate was the border radiuses, which I've applied to the start first section and last section, instead of just getting it to work on the parent container:

```css
#sedan {
  background-color: hsl(31, 77%, 52%);
  border-radius: 10px 10px 0 0;
}

#luxury {
  background-color: hsl(179, 100%, 13%);
  border-radius: 0 0 10px 10px;
}
```

I tried to fix it by setting border-radius on the parent container and set the overflow property to hidden. And this works when the component is in its horizontal layout, but for some weird reason not in the vertical one.

```css
main {
  border-radius: 10px;
  overflow: hidden;
}
```

![](screenshots/overflow-hidden-not-working-on-mobile-view.png)

Not sure what causes this, but as I'm writing this I realize that only fixing this issue, will reduce a bit of code at least, so I've chosen to leave the border-radius and overflow on the main container, and apply an extra border radius to the luxury card section, which I then remove again when it enters the horizontal layout screen dimension.

```css
#luxury {
  border-radius: 0 0 10px 10px;

  @media only screen and (min-width: 857px) {

  #luxury {
    border-radius: 0;
  }
}
```

### Continued development

I thought I was spot on with the design, until I took a screenshot and placed it over the design I had in figma, and noticed some my parts are a lot bigger than the design. So I guess Id like to improve my attention to detail? I'm not sure how relevant having it pixel perfect is, and maybe in this day and age of having so many different screen sizes you can't really make it pixel perfect to the design?

I also want to continue to be conscious of semantics, I feel like I'm getting better with them, and tweaking and moving things with css is getting a lot simpler, so these little challenges are definitely working.

I've written this on every project, but I STILL want to learn CSS grid, haven't gotten around to it yet, probably because I'm getting so comfortable with flex-box, but I know flex-box is not the tool for layouts, and is mostly supposed to be used for alignment.

## Author

- Frontend Mentor - [@Dinesvlarsen](https://www.frontendmentor.io/profile/dinesvlarsen)
- Twitter - [@Dinesvlarsen](https://twitter.com/Dinesvlarsen)

## Acknowledgments

I got the tip of trying out overflow: hidden by @Kaleem420#9453 on the Jonas Schmedtmann discord server. So thanks for that🙏
