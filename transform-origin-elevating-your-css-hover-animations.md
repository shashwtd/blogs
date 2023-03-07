---

title: Transform-Origin — Elevating Your CSS Hover Animations!
date: March 5, 2023
id: transform-origin-elevating-your-css-hover-animations
description: Take your hover animations to the next level with this quick guide on using transform-origin! By adjusting the transform-origin based on the direction of the mouse-leave, you can create more realistic and dynamic hover effects. With a bit of creativity and experimentation, you can customize this technique to fit the unique design needs for your website!

---

# Creating Realistic Hover Effects with CSS Transform Origin

Hover effects are a great way to add some visual interest and interactivity to your web designs. With CSS transform origin, you can take your hover effects to the next level by creating realistic and dynamic animations.

<br />

## What is CSS `transform-origin`?

CSS transform origin is a property that allows you to specify the origin point of a CSS transformation. It determines where the transformation takes place and in which direction. By default, the transform origin is set to the center of an element.

---

## How to use CSS transform origin to create hover effects?

To create a hover effect with CSS transform origin, you need to define the origin point based on the mouse position. Here's an example of how to create a hover effect on a list item:

```css
li {
	position: relative;
	transition: ease-in  0.3s;
	background: lightgray;
	--transform-origin: top;
}

li::after {
	content: '';
	content: "";
	position: absolute;
	top: 0;
	left: 0;
	background: lightblue;
	height: calc(100%  +  5px);
	width: calc(100%  +  10px);
	transition: transform ease-out  0.2s;
	transform: translate(-5px, -2.5px) scaleY(0);
	transform-origin: var(--transform-origin);
}

li:hover::after {
	transform: scaleY(1);
}
```
​
In this example, we define a CSS variable `--transform-origin` with the initial value of `top`. We will use this variable to set the transform origin for the `::after` pseudo-element when the list item is hovered. The `::after` pseudo-element is used to create a background effect that is revealed when the list item is hovered.

To calculate the mouse position relative to the list item, we will be using the `getBoundingClientRect()` method to get the position and size of the list item. We can then calculate the `y` coordinate of the mouse relative to the list item using the `clientY` property of the `event` object. 

Next, we will be creating a function that checks the direction the mouse left from. We will be using the methods described earlier.

```js
function setTransformOrigin(elm) { 
	const rect = elm.getBoundingClientRect(); 
	const y = event.clientY - rect.top;
	
	const origin = y >= rect.height / 2 ? 'center bottom' : 'center top';
	elm.style.setProperty('--transform-origin', origin); 
}
```


With this function, we can set the transform origin of the list item based on the mouse position.  The function takes an `elm` parameter which is the DOM element. 

## Conclusion

CSS transform origin is a powerful tool that can be used to create dynamic and realistic hover effects. By setting the transform origin based on the mouse position, you can create unique and visually interesting animations that will make your web designs stand out.

Incorporate this technique into your web designs and watch as your hover effects come to life.
