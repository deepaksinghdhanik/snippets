## Media Queries for Standard Devices


### Wearables

#### Apple watch

```
@media
  (max-device-width: 42mm)
  and (min-device-width: 38mm) { 

}
```

#### Moto 360 Watch 
```
@media 
  (max-device-width: 218px)
  and (max-device-height: 281px) { 

}

```
### For Mobile
```
@media only screen 
  and (min-device-width: 375px) 
  and (max-device-width: 667px) 
  and (-webkit-min-device-pixel-ratio: 2) { 

}

/* Portrait */
@media only screen 
  and (min-device-width: 375px) 
  and (max-device-width: 812px) 
  and (-webkit-min-device-pixel-ratio: 3)
  and (orientation: portrait) { 

}

/* Landscape */
@media only screen 
  and (min-device-width: 375px) 
  and (max-device-width: 812px) 
  and (-webkit-min-device-pixel-ratio: 3)
  and (orientation: landscape) { 
}
```
### Laptops

```
/*  Non-Retina Screens  */
@media screen 
  and (min-device-width: 1200px) 
  and (max-device-width: 1600px) 
  and (-webkit-min-device-pixel-ratio: 1) { 
}

/*  Retina Screens  */
@media screen 
  and (min-device-width: 1200px) 
  and (max-device-width: 1600px) 
  and (-webkit-min-device-pixel-ratio: 2)
  and (min-resolution: 192dpi) { 
}

```




## Truncate String with Ellipsis

```
All the following are required, so the text must be in a single straight line that overflows a box where that overflow is hidden.
```
***HTML***
```
<h1>
  This little piggy went to market and this little piggy stayed home.
</h1>
```
***CSS***

```
h1 {
  width: 200px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  
  padding: 20px;
  font-size: 1.3rem;
  margin: 0;
  background: white;
  resize: horizontal;
}

body {
  height: 100vh;
  overflow: hidden;
  display: grid;
  place-items: center;
  background: #ccc;
}
 
```
***Result***

>This little piggy...


## Custom File Input Styling

```
If you're interested in Webkit/Blink/Chrome specific styling, there is a proprietary pseudo element to hide, and then use an also non-standard psudeo-on-an-input:

```

***HTML***
```
<input type="file" class="custom-file-input">
```

***CSS***

```
.custom-file-input::-webkit-file-upload-button {
  visibility: hidden;
}
.custom-file-input::before {
  content: 'Select some files';
  display: inline-block;
  background: linear-gradient(top, #f9f9f9, #e3e3e3);
  border: 1px solid #999;
  border-radius: 3px;
  padding: 5px 8px;
  outline: none;
  white-space: nowrap;
  -webkit-user-select: none;
  cursor: pointer;
  text-shadow: 1px 1px #fff;
  font-weight: 700;
  font-size: 10pt;
}
.custom-file-input:hover::before {
  border-color: black;
}
.custom-file-input:active::before {
  background: -webkit-linear-gradient(top, #e3e3e3, #f9f9f9);
}
```


##Perfect CSS Sprite / Sliding Doors Button

```
Big note here! Sliding doors is a pretty old technique. It had its time on the web, but it's probably not the smartest way to go these days. We have border-radius now and gradient backgrounds and all that, which unlock most of what we were trying to achieve back in the day of sliding doors.

But it's still fun to document how it works, so here it is:
```

***HTML***
```
<a href="#" class="button">
  <span>Sliding Doors Button</span>
</a>
```

***CSS**
```
.button {
  float: left;
  clear: both;
  background: url(RIGHT_SIDE.png) top right no-repeat;
  margin: 5px;
  padding-right: 20px;
  color: white;
  text-decoration: none;
}
.button span {
  background: url(LEFT_SIDE.png) top left no-repeat;
  line-height: 22px;
  padding: 7px 0 5px 18px;
  display: block;
}
.button:hover {
  background-position: right -34px;
}
.button:hover span {
  background-position: 0 -34px; color: #fff;
}
```

## CSS Radial Gradient

```
 When we talk about gradients, it's worth beginning with the fact that gradients are an image replacement in CSS. That's a fancy way of saying that creating a gradient in CSS provides the browser with instructions for painting an image on the screen rather than you providing the browser with the source URL of a file you created in an image editing application, like Photoshop or Sketch. It's a native CSS way for doing the same thing in code and, as such, gradients are included in the CSS Image Values and Replaced Content specification.

A radial gradient differs from a linear gradient in that it starts at a single point and emanates outward. Gradients are often used to simulate a light source, which we know isn't always straight. That makes them useful to make the transitions between colors seem even more natural.


The default is for the first color to start in the center center position of the element and then fade to the end color toward the edge of the element. The fade happens at an equal rate no matter which direction.
```

#### Syntax
```
The radial-gradient() notation is used on either the background or background-image property in CSS. This makes total sense when we recall that gradients are basically the CSS to create images that we would otherwise make in image editing software and place on a background property anyway.
```
#### Official Syntax
```
<radial-gradient> = radial-gradient(
  [ [ <shape> || <size> ] [ at <position> ]? , |
    at <position>, 
  ]?
  <color-stop> [ , <color-stop> ]+
)
```

#### Values

The radial-gradient notation accepts the following values noted above:

- shape: Determines the shape of the gradient follows when transitioning outward, from one color to the next. Since we're talking about radial gradients, the shapes are limited to being circular in nature. We can omit this value and the notation will measure the element's side lengths to determine whether one value better matches the situation. For example, an element that is a perfect square would be a great match for circle whereas anything rectangular is ripe for ellipse.
- circle
- ellipse
- size: Influences the ending shape of the gradient by taking the shape value and instructing where the gradient should end based on the center of the shape. This can be expressed by name or an exact measure of length.
    - closest-side: The gradient will end at side closest to the center of the shape. If two sides match this criteria, then it will be evenly distributed.
    - farthest-side (default): The opposite of closest-side, where the gradient will end at the side furthest from the shape's center.
    - closest-corner: The gradient will end at the corner that matches as the closest to the shape's center.
    - farthest-cornerThe opposite of closest-corner, where the gradient ends at the corner that is located furthest from the shape's center.
    - <length>: We can specify a numeric value that serves as the circle's radius. This has to be stated in positive pixels or relative units. Sorry, no negative units or percentages allowed because a negative circle would be vacuum and percentages can be relative to any number of surrounding values.
    - <length> or percentage: A second numeric value can be provided to declare the explicit size of an ellipse, but not a circle. Again, negative values are a no-no, but percentages are fair game since the size is relative to the gradient box rather than the element.
    - position: This works very much the same way that it does on background-position. That means top, right, left, and center all work here, as well as combinations where two named values (e.g. top center) are provided. We can also specify an exact position using a numeric value, including percentage, all of which are relative to the element's bounding box. Default is center center.
    - color-stop: These are color values that define the gradient. Any color value is accepted here, including hex, named, RGB and HSL.

#### Usage

Here's how that looks at perhaps its most basic. Note that we are not declaring the shape>, size, position or color-stop values, which all default to values placing the gradient at the very center of the element and transition evenly between the declared color values.

***CSS**
```
.gradient {
  background-image:
    radial-gradient(
      yellow,
      #f06d06
    );
}

```

# The Clearfix: Force an Element To Self-Clear its Children

> This will do you fine these days (IE 8 and up):
        ```
        .group:after {
        content: "";
        display: table;
        clear: both;
        }
        ```

- Apply it to any parent element in which you need to clear the floats. For example:

***HTML***
```
<div class="group">
  <div class="is-floated"></div>
  <div class="is-floated"></div>
  <div class="is-floated"></div>
</div>
```

>You would use this instead of clearing the float with something like <br style="clear: both;" /> at the bottom of the parent (easy to forget, not handleable right in CSS, non-semantic) or using something like overflow: hidden; on the parent (you don't always want to hide overflow).

#### Basic Link Rollover as CSS Sprite

***HTML***
```
<h1>Image Sprite</h1>
<a href="#"></a>
```

***CSS***
```
a {
  background: url(sprite.png) no-repeat;
  display: block;
  height: 30px;
  width: 250px;
}

a:hover {
  background-position: 0 -30px;
}
```

#### CSS Conic Gradient
```
A conic gradient is similar to a radial gradient. Both are circular and use the center of the element as the source point for color stops. However, where the color stops of a radial gradient emerge from the center of the circle, a conic gradient places them around the circle.
```
```
Conic gradients were not included in the original batch of CSS Gradients in CSS Level 3, but are included in the CSS Image Values and Replaced Content specification in Level 4, which is currently in working draft at the time of this writing.
```
#### Syntax
>The conic gradient syntax is easier to understand in plain English:

Make a conic-gradient that is located at [some point] that starts with [one color] at some angle and ends with [another color] at [some angle]

The official specification looks more like this:

```
conic-gradient() = conic-gradient(
  [ from <angle> ]? [ at <position> ]?,
  <angular-color-stop-list>
)
```
```
At its most basic level, it looks like this:

.conic-gradient {
  background: conic-gradient(#fff, #000);
}

```
```
.conic-gradient {
  /* Original example */
  background-image: conic-gradient(#fff, #000);
  /* Explicitly state the location center point */
  background: conic-gradient(at 50% 50%, #fff, #000);
  /* Explicitly state the angle of the start color */
  background: conic-gradient(from 0deg, #fff, #000);
  /* Explicitly state the angle of the start color and center point location */
  background: conic-gradient(from 0deg at center, #fff, #000);
  /* Explicitly state the angles of both colors as percentages instead of degrees */
  background: conic-gradient(#fff 0%, #000 100%);
  /* Explicitly state the angle of the starting color in degrees and the ending color by a full turn of the circle */
  background: conic-gradient(#fff 0deg, #000 1turn);
}
```


## Handling Long Words and URLs (Forcing Breaks, Hyphenation, Ellipsis, etc)

```
here are times when a really long string of text can overflow the container of a layout.

```
***CSS***
```
.dont-break-out {

  /* These are technically the same, but use both */
  overflow-wrap: break-word;
  word-wrap: break-word;

  -ms-word-break: break-all;
  /* This is the dangerous one in WebKit, as it breaks things wherever */
  word-break: break-all;
  /* Instead use this non-standard one: */
  word-break: break-word;

  /* Adds a hyphen where the word breaks, if supported (No Blink) */
  -ms-hyphens: auto;
  -moz-hyphens: auto;
  -webkit-hyphens: auto;
  hyphens: auto;
}
```
```
- overflow-wrap: break-word; makes sure the long string will wrap and not bust out of the container. You might as well use word-wrap as well because as the spec says, they are literally just alternate names for each other. Some browsers support one and not the other. Firefox (tested v43) only supports word-wrap. Blink (tested Chrome v45) will take either one.
-  With overflow-wrap in use all by itself, words will break kinda anywhere they need to. If there is an "acceptable break" character (like a literal dash, for instance), it will break there, otherwise it just does what it needs to do.
- You might as well use hyphens as well, because then it will try to tastefully add a hyphen where it breaks if the browser supports it (Blink doesn't at time of writing, Firefox does).
- word-break: break-all; is to tell the browser that it's OK to break the word wherever it needs to. Even though it kinda does that anyway so I'm not sure in what cases it's 100% necessary.

```
#### Preventing Overflow with Ellipsis
```
.ellipses {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
```

## Hexagon with Shadow

***HTML***
```
<div class="hexagon"><span></span></div>
```

***CSS***
```
.hexagon {
  width: 100px;
  height: 55px;
  position: relative;
}

.hexagon, 
.hexagon:before, 
.hexagon:after {
  background: red;
  box-shadow: 0 0 10px rgba(0,0,0,0.8);   
}

.hexagon:before,
.hexagon:after {
  content: "";
  position: absolute;
  left: 22px;
  width: 57px;
  height: 57px;
  transform: rotate(145deg) skew(22.5deg);
}

.hexagon:before {
  top: -29px;
}

.hexagon:after {
  top: 27px;
}

.hexagon span {
  position: absolute;
  top: 0;
  left: 0;
  width: 100px;
  height: 55px;
  background: red;
  z-index: 1;
}

```

## CSS Hacks Targeting Firefox
***Firefox 2***
```
html>/**/body .selector, x:-moz-any-link {
  color:lime;
}
```

***Firefox 3***
```
html>/**/body .selector, x:-moz-any-link, x:default {
  color:lime;
}

&

.selector, x:-moz-any-link, x:default { color:lime; }

```

***Any Firefox***
```
@document url("https://example.com") { 
  .selector {
     color:lime;
  }
}

```

## Signify “PDF Bombs”

```
Any ol' anchor link can be a link to a PDF document, but clicking a link like that thinking otherwise can be surprising and uncomfortable for a user. This CSS can visually signify those links.
```
***HTML***
```
<p>Watch out for the <a href="some.pdf" data-size="2 MB">PDF bomb</a> here!</p>
```

***CSS**
```
/* Add " (PDF)" text after links that go to PDFs */
a[href$=".pdf"]:after { content: " (PDF)"; }

/* If file size specified as data attribute, use that too */
a[href$=".pdf"][data-size]:after { content: " (PDF, " attr(data-size) ")"; }

```
 - Result :- Watch out for the PDF bomb (PDF, 2 MB) here!

 ## Change Autocomplete Styles in WebKit Browsers

 ```
 Many browsers (including Chrome and Safari) provide a setting that allows users to automatically fill in details for common form fields. You have seen this when completing a form that asks for things like name, address and email.

The catch is that users must have enabled this setting in order for this snippet to be effective. If the setting is enabled, then WebKit browsers will style the fields it has autocompleted for the user
```

#### The Snippet
```
We can use the -webkit-autofill pseudo-selector to target those fields and style them as we see fit. The default styling only affects the background color, but most other properties apply here, such as border and font-size. We can even change the color of the text using -webkit-text-fill-color which is included in the snippet below.
```
***CSS***
```
/* Change Autocomplete styles in Chrome*/
input:-webkit-autofill,
input:-webkit-autofill:hover, 
input:-webkit-autofill:focus
textarea:-webkit-autofill,
textarea:-webkit-autofill:hover
textarea:-webkit-autofill:focus,
select:-webkit-autofill,
select:-webkit-autofill:hover,
select:-webkit-autofill:focus {
  border: 1px solid green;
  -webkit-text-fill-color: green;
  -webkit-box-shadow: 0 0 0px 1000px #000 inset;
  transition: background-color 5000s ease-in-out 0s;
}
```

## Typewriter Effect

```

```

***HTML***
```
<div class="typewriter">
  <h1>The cat and the hat.</h1>
</div>
```
***CSS***
```
.typewriter h1 {
  overflow: hidden; /* Ensures the content is not revealed until the animation */
  border-right: .15em solid orange; /* The typwriter cursor */
  white-space: nowrap; /* Keeps the content on a single line */
  margin: 0 auto; /* Gives that scrolling effect as the typing happens */
  letter-spacing: .15em; /* Adjust as needed */
  animation: 
    typing 3.5s steps(40, end),
    blink-caret .75s step-end infinite;
}

/* The typing effect */
@keyframes typing {
  from { width: 0 }
  to { width: 100% }
}

/* The typewriter cursor effect */
@keyframes blink-caret {
  from, to { border-color: transparent }
  50% { border-color: orange; }
}
```

***Notes***
- Demo relies on flexbox, so that could affect the layout in testing
- Assumes the use of Autoprefixer
- The width of the text container will be determined by the length of the text being used
- Adding more steps to the typing animation will increase the smoothness of the typing
- Adjust the letter-spacing based on the font-family and font-size being used

***Another Example***

***HTML***
```
<div class="css-typing">
  <p>
    Typed text 1
  </p>
  <p>
    Typed text 2 Longer
  </p>
  <p>
    Typed text 3
  </p>
</div>
```
***CSS***
```
.css-typing p {
  border-right: .15em solid orange;
  font-family: "Courier";
  font-size: 14px;
  white-space: nowrap;
  overflow: hidden;
}
.css-typing p:nth-child(1) {
  width: 7.3em;
  -webkit-animation: type 2s steps(40, end);
  animation: type 2s steps(40, end);
  -webkit-animation-fill-mode: forwards;
  animation-fill-mode: forwards;
}

.css-typing p:nth-child(2) {
  width: 11.5em;
  opacity: 0;
  -webkit-animation: type2 2s steps(40, end);
  animation: type2 2s steps(40, end);
  -webkit-animation-delay: 2s;
  animation-delay: 2s;
  -webkit-animation-fill-mode: forwards;
  animation-fill-mode: forwards;
}

.css-typing p:nth-child(3) {
  width: 7.3em;
  opacity: 0;
  -webkit-animation: type3 5s steps(20, end), blink .5s step-end infinite alternate;
  animation: type3 5s steps(20, end), blink .5s step-end infinite alternate;
  -webkit-animation-delay: 4s;
  animation-delay: 4s;
  -webkit-animation-fill-mode: forwards;
  animation-fill-mode: forwards;
}

@keyframes type {
  0% {
    width: 0;
  }
  99.9% {
    border-right: .15em solid orange;
  }
  100% {
    border: none;
  }
}

@-webkit-keyframes type {
  0% {
    width: 0;
  }
  99.9% {
    border-right: .15em solid orange;
  }
  100% {
    border: none;
  }
}

@keyframes type2 {
  0% {
    width: 0;
  }
  1% {
    opacity: 1;
  }
  99.9% {
    border-right: .15em solid orange;
  }
  100% {
    opacity: 1;
    border: none;
  }
}

@-webkit-keyframes type2 {
  0% {
    width: 0;
  }
  1% {
    opacity: 1;
  }
  99.9% {
    border-right: .15em solid orange;
  }
  100% {
    opacity: 1;
    border: none;
  }
}

@keyframes type3 {
  0% {
    width: 0;
  }
  1% {
    opacity: 1;
  }
  100% {
    opacity: 1;
  }
}

@-webkit-keyframes type3 {
  0% {
    width: 0;
  }
  1% {
    opacity: 1;
  }
  100% {
    opacity: 1;
  }
}

@keyframes blink {
  50% {
    border-color: transparent;
  }
}
@-webkit-keyframes blink {
  50% {
    border-color: tranparent;
  }
}
```


## CSS Repeating Gradients

```
Repeating gradients take a trick we can already do with the creative use of color-stops on the linear-gradient() and radial-gradient() notations, and bakes it in for us.

The idea is that we can create patterns out of the gradients we create and allow them to repeat infinitely.

There is a trick, with non-repeating gradients, to create the gradient in such a way that if it was a little tiny rectangle, it would line up with other little tiny rectangle versions of itself to create a repeating pattern. So essentially create that gradient and set the background-size to make that little tiny rectangle. That made it easy to make stripes, which you could then rotate or whatever.
```

####Syntax
```
There are three types of repeating gradients, two of which are currently supported in the official specification and one that is in the current working draft.

The syntax for each notation is the same as its related gradient type. For example, repeating-linear-gradient() follows the same syntax as linear-gradient().
```
>Repeating Gradient	            Related Notation	Supported?
>repeating-linear-gradient()	linear-gradient()	    Yes
>repeating-radial-gradient	    radial-gradient()	    Yes
>repeating-conic-gradient	    conic-gradient()	    No


```
Where the gradient repeats is determined by the final color stop. If that's at 20px, the size of the gradient (which then repeats) is a 20px by 20px square. The same is true if there are multiple colors chained to the pattern. The final color with the final stop is what determines the size and location of the repeat.

```
***HTML***
```
<div class="repeat"></div>
```
***CSS***
```
.repeat {
  width: 100px;
  height: 100px;
  background-image: 
    repeating-linear-gradient(
      45deg,
      yellow,
      yellow 10px,
      red 10px,
      red 20px /* determines size */
    );
}
```


## CSS Linear Gradient

```
Perhaps the most common type of gradient we see in web design is the linear-gradient(). It's called "linear" because the colors flow from left-to-right, top-to-bottom, or at any angle you chose in a single direction.


Linear gradients were introduced in CSS Level 3 as part of the CSS Image Values and Replaced Content specification. It might sound funny to catalog this feature with images, but gradients are basically a way to generate an image natively in code without the use of image editing software. As such, gradients are applied to background properties, which we'll get into right now.

```
***HTML***
```
<div class="gradient">
  
</div>
```
***CSS***
```
div {
  height: 100px;
  background-color: red;
  background-image:
    linear-gradient(
      red, #f06d06
    );
}

- Another Option

/* Explicitly declare the direction */
background-image: linear-gradient(to bottom, red, #f06d06);

/* Explicitly declare the angle, in degrees */
background-image: linear-gradient(72deg, red, #f06d06);

- Chaining Multiple Colors

.gradient {
  background-image:
    linear-gradient(
      to right, 
      red, 
      #f06d06, 
      rgb(255, 255, 0), 
      green
    );
}

```

## System Font Stack
```
Defaulting to the system font of a particular operating system can boost performance because the browser doesn't have to download any font files, it's using one it already had. That's true of any "web safe" font, though. The beauty of "system" fonts is that it matches what the current OS uses, so it can be a comfortable look.
```

***Get to the snippet, already!***
```
The reason for the preface is that it shows how deep you may need to go back to support system fonts. Additionally, it helps show that with new system versions, come new fonts, and thus the possibility of needing to update your font stack.
```

***Method 1: System Fonts at the Element Level***
```
Chrome and Safari have recently shipped "system-ui" which is a generic font family that can be used in place of "-apple-system" and "BlinkMacSystemFont" in the following examples. Hat tip to J.J. for the info.
One method for applying system fonts is by directly calling them on an element using the font-family property.
```

>GitHub uses this method on their site, applying system fonts on the body element:
***CSS***
```
/* System Fonts as used by GitHub */
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
}
```
```
Both Medium and the WordPress admin use a similar approach, with a slight variation, most notably support for Oxygen Sans (created for the GNU+Linux operating system) and Cantarell (created for the GNOME operating system). This snippet also drops support for certain types of emoji and symbols:
```
***CSS***
```
/* System Fonts as used by Medium and WordPress */
body {
  font-family: -apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Oxygen-Sans,Ubuntu,Cantarell,"Helvetica Neue",sans-serif;
}

Note: This method should only be used on the font-family property instead of the font shorthand. Booking.com published a thorough write-up on the warnings it generates due to the leading font appearing to be a vendor prefix.
```

***Method 2: System Font Stacks***
```
The limitation of the first method is that you have to call the full stack of fonts each time it's used on an element and that can get cumbersome and bloat your code, depending on where and how it's used.

Jonathan Neal offers an alternative method where system fonts are declared using @font-face.

The benefit here is that you can declare the fonts once and then that becomes the thing you can on the font-family property instead of the long list of fonts each and every time.
```

***CSS***
```
/* Define the "system" font family */
@font-face {
  font-family: system;
  font-style: normal;
  font-weight: 300;
  src: local(".SFNSText-Light"), local(".HelveticaNeueDeskInterface-Light"), local(".LucidaGrandeUI"), local("Ubuntu Light"), local("Segoe UI Light"), local("Roboto-Light"), local("DroidSans"), local("Tahoma");
}

/* Now, let's apply it on an element */
body {
  font-family: "system";
}
```
```
Note that Jonathan's full example illustrates the capability to define variations of the system font family that was defined in the snippet above to account for italics, bolding, and additional weights.
```

## Animated Grainy Texture

```
The DayTrip website uses a neat effect on its page header that distorts the background image with an animated, grainy texture. The effect is subtle but creates a dusty, retro vibe.
```

#### Step 1: Setting Things Up
```
First, let's set up the our page header. We're going to use a common pattern where a background image takes up the entire space.
```
***CSS***
>.page-header {
  height: 100vh;
  background-image: url("/path/to/image.jpg");
}


#### Step 2: Selecting a Texture
```
Next, we need an image with a grainy texture to it. You can create this yourself. Subtle Patterns also has a number of nice options, including this one that we'll use for our demo. Note that the image does not need to be huge. Something in the neighborhood of 400px square will do the trick.

The idea is that we will overlay the grainy texture on top of the .page-header. We can use the :after pseudo-element on .page-header so there is no need to create another element.
```

***CSS***

>.page-header {
  height: 100vh;
  background-image: url("/path/to/image.jpg");
}

>.page-header:after {
  /* content is required when using :after */
  content: "";
  /* The grainy image */
  background-image: url("/path/to/grainy/image.jpg");
  /* Specify a height and width above and beyond the page header for movement */
  height: 300%;
  width: 300%;
  /* We're using opacity in place of a transparent image */
  opacity: 0.3;
  /* We'll need this when the animation kicks in to hold the position of the texture */
  position: fixed;
}

```
Note that we placed a height and width on the pseudo-element as well as a top and left so that it actually exceeds the boundary of the page header and is centered to it. We want to do this so that the grainy texture layer has room to move around without exposing the page header layer underneath.
```

#### Step 3: Animating the Grainy Layer
```
The last thing we need to do is animate the grainy layer. This is the effect that we're going after and gives the page header that retro, analog appeal.

The DayTrip site uses the following to define the animation keyframes:
```

***CSS***
>@keyframes grain {
  0%, 100% { transform:translate(0, 0) }
  10% { transform:translate(-5%, -10%) }
  20% { transform:translate(-15%, 5%) }
  30% { transform:translate(7%, -25%) }
  40% { transform:translate(-5%, 25%) }
  50% { transform:translate(-15%, 10%) }
  60% { transform:translate(15%, 0%) }
  70% { transform:translate(0%, 15%) }
  80% { transform:translate(3%, 35%) }
  90% { transform:translate(-10%, 10%) }
}

```
It's sort of tough to visualize what that code means, but it's basically moving the top grainy layer around in a zig-zag pattern.


Now all we have to do is apply the keyframes to .page-header:after to see it take effect. We'll set the animation to play for 8 seconds and loop infinitely:

.page-header:after {
```

***CSS***
```
Now all we have to do is apply the keyframes to .page-header:after to see it take effect. We'll set the animation to play for 8 seconds and loop infinitely:
```

>.page-header:after {
  /* content is required when using :after */
  content: "";
  /* The animation */
  animation: grain 8s steps(10) infinite;
  /* The grainy image */
  background-image: url("/path/to/grainy/image.jpg");
  /* Specify a height and width above and beyond the page header for movement */
  height: 300%;
  width: 300%;
  /* We're using opacity in place of a transparent image */
  opacity: 0.3;
  /* We'll need this when the animation kicks in to hold the position of the texture */
  position: fixed;
}


### Putting it All Together
```
Here's the full snippet with all the pieces in place. Note that we are assuming the use of Autoprefixer for all vendor prefixing.
```

>.page-header {
  height: 100vh;
  background-image: url("/path/to/image.jpg");
}

>.page-header:after {
  animation: grain 8s steps(10) infinite;
  background-image: url("/path/to/grainy/image.jpg");
  content: "";
  height: 300%;
  left: -50%;
  opacity: 0.3;
  position: fixed;
  top: -100%;
  width: 300%;
}

>@keyframes grain {
  0%, 100% { transform:translate(0, 0) }
  10% { transform:translate(-5%, -10%) }
  20% { transform:translate(-15%, 5%) }
  30% { transform:translate(7%, -25%) }
  40% { transform:translate(-5%, 25%) }
  50% { transform:translate(-15%, 10%) }
  60% { transform:translate(15%, 0%) }
  70% { transform:translate(0%, 15%) }
  80% { transform:translate(3%, 35%) }
  90% { transform:translate(-10%, 10%) }
}




## Stacked Paper Effect

```
A popular design technique is to create a content container that looks like a sheet of paper and to stack other sheets of paper below it, adding a layered or three-dimensional style. We can create this effect using straight up CSS, but there are multiple types of stacked paper designs we can consider. We'll provide snippets for four in particular.
```

***Vertical Stack of Paper on Bottom***
```
The idea here is that our content container is the top sheet of paper and more sheets are stacked beneath it with their edges displayed at the bottom of the top sheet.
```
***HTML***

><div class="paper"></div>

***CSS***
>.paper {
  background: #fff;
  box-shadow:
    /* The top layer shadow */
    0 1px 1px rgba(0,0,0,0.15),
    /* The second layer */
    0 10px 0 -5px #eee,
    /* The second layer shadow */
    0 10px 1px -4px rgba(0,0,0,0.15),
     /* The third layer */
    0 20px 0 -10px #eee,
    /* The third layer shadow */
    0 20px 1px -9px rgba(0,0,0,0.15);
    /* Padding for demo purposes */
    padding: 30px;
}


***Vertical Stack of Paper on Top***
```
This is the same concept as the last one, but with the stack of papers revealed on the top of the container instead of the bottom. The only difference here is that we have repositioned the the box-shadoow property on the .paper element using negative numbers.
```

***HTML***

><div class="paper"></div>

***CSS***

>.paper {
  background: #fff;
  box-shadow:
    /* The top layer shadow */
    0 -1px 1px rgba(0,0,0,0.15),
    /* The second layer */
    0 -10px 0 -5px #eee,
    /* The second layer shadow */
    0 -10px 1px -4px rgba(0,0,0,0.15),
     /* The third layer */
    0 -20px 0 -10px #eee,
    /* The third layer shadow */
    0 -20px 1px -9px rgba(0,0,0,0.15);
    /* Padding for demo purposes */
    padding: 30px;
}


***Diagonal Stack of Paper***
```
This is a slightly different method, where we use the ::before and ::after pseudo-elements to create the additional sheets of paper, rather than the box-shadow technique used in the previous examples.
```
***HTML***

><div class="paper"></div>

***CSS***

>/* Diagonal stacked paper effect */
.paper {
  background-color: #fff;
  /* Need position to allow stacking of pseudo-elements */
  position: relative;
  /* Padding for demo purposes */
  padding: 30px;
}

>.paper,
.paper::before,
.paper::after {
  /* Add shadow to distinguish sheets from one another */
  box-shadow: 2px 1px 1px rgba(0,0,0,0.15);
}

>.paper::before,
.paper::after {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: #eee;
}

>/* Second sheet of paper */
.paper::before {
  left: 7px;
  top: 5px;
  z-index: -1;
}

>/* Third sheet of paper */
.paper::after {
  left: 12px;
  top: 10px;
  z-index: -2;
}


***Disorganized Paper Stack***
```
We can stagger the sheets of paper to create an intentionally messy look using the same sort of technique with pseudo-elements as the last example, though using the transform property to rotate the underlying sheets of paper. This example assumes the use of Autoprefixer or that prefixes are used for the transform property where browser support may wane.
```
***HTML***

><div class="paper"></div>

***CSS***
>.paper {
  background: #fff;
  padding: 30px;
  position: relative;
}

>.paper,
.paper::before,
.paper::after {
  /* Styles to distinguish sheets from one another */
  box-shadow: 1px 1px 1px rgba(0,0,0,0.25);
  border: 1px solid #bbb;
}

>.paper::before,
.paper::after {
  content: "";
  position: absolute;
  height: 95%;
  width: 99%;
  background-color: #eee;
}

>.paper::before {
  right: 15px;
  top: 0;
  transform: rotate(-1deg);
  z-index: -1;
}

>.paper::after {
  top: 5px;
  right: -5px;
  transform: rotate(1deg);
  z-index: -2;
}

***Fluid Typography***

```
html {
  font-size: 16px;
}
@media screen and (min-width: 320px) {
  html {
    font-size: calc(16px + 6 * ((100vw - 320px) / 680));
  }
}
@media screen and (min-width: 1000px) {
  html {
    font-size: 22px;
  }
}
```

```
That would scale font-size from a minimum of 16px (at a 320px viewport) to a maximum of 22px (at a 1000px viewport). Here's a demo of that, but as a Sass @mixin (which we'll cover later).

Sass was used just to make that output a little easier to generate, and the fact that there is a smide of math involved. Let's take a look.

Using viewport units and calc(), we can have font-size (and other properties) adjust their size based on the size of the screen. So rather than always being the same size, or jumping from one size to the next at media queries, the size can be fluid.
```
```
Here's the math, credit Mike Riethmuller:
```
>body {
  font-size: calc([minimum size] + ([maximum size] - [minimum size]) * ((100vw - [minimum viewport width]) / ([maximum viewport width] - [minimum viewport width])));
}

```
The reason that math is a little complicated is that we're trying to avoid type ever getting smaller than our minimum or bigger than our maximum, which is very easy to do with viewport units.

For example, if we want the our font size in a range where 14px is the minimum size at the smallest viewport width of 300px and where 26px is the maximum size at the largest viewport width of 1600px, then our equation looks like this:
```
>body {
  font-size: calc(14px + (26 - 14) * ((100vw - 300px) / (1600 - 300)));
}



#### Nested & Expandable Folders
```
This was a demo originally by Martin Ivanov, utilizing hidden checkboxes and adjacent sibling combinators to set the "state" of each folder. The live demo has since fallen off of the internet, so I'll post a copy of it here, with the original code below it.
```
***HTML***
```
<div class="css-treeview">
	<ul>
		<li><input type="checkbox" id="item-0" /><label for="item-0">This Folder is Closed By Default</label>
			<ul>
				<li><input type="checkbox" id="item-0-0" /><label for="item-0-0">Ooops! A Nested Folder</label>
					<ul>
						<li><input type="checkbox" id="item-0-0-0" /><label for="item-0-0-0">Look Ma - No Hands!</label>
							<ul>
								<li><a href="./">First Nested Item</a></li>
								<li><a href="./">Second Nested Item</a></li>
								<li><a href="./">Third Nested Item</a></li>
								<li><a href="./">Fourth Nested Item</a></li>
							</ul>
						</li>
						<li><a href="./">Item 1</a></li>
						<li><a href="./">Item 2</a></li>
						<li><a href="./">Item 3</a></li>
					</ul>
				</li>
				<li><input type="checkbox" id="item-0-1" /><label for="item-0-1">Yet Another One</label>
					<ul>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
					</ul>
				</li>
				<li><input type="checkbox" id="item-0-2" disabled="disabled" /><label for="item-0-2">Disabled Nested Items</label>
					<ul>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
					</ul>
				</li>
				<li><a href="./">item</a></li>
				<li><a href="./">item</a></li>
				<li><a href="./">item</a></li>
				<li><a href="./">item</a></li>
			</ul>
		</li>
		<li><input type="checkbox" id="item-1" checked="checked" /><label for="item-1">This One is Open by Default...</label>
			<ul>
				<li><input type="checkbox" id="item-1-0" /><label for="item-1-0">And Contains More Nested Items...</label>
					<ul>
						<li><a href="./">Look Ma - No Hands</a></li>
						<li><a href="./">Another Item</a></li>
						<li><a href="./">And Yet Another</a></li>
					</ul>
				</li>
				<li><a href="./">Lorem</a></li>
				<li><a href="./">Ipsum</a></li>
				<li><a href="./">Dolor</a></li>
				<li><a href="./">Sit Amet</a></li>
			</ul>
		</li>
		<li><input type="checkbox" id="item-2" /><label for="item-2">Can You Believe...</label>
			<ul>
				<li><input type="checkbox" id="item-2-0" /><label for="item-2-0">That This Treeview...</label>
					<ul>
						<li><input type="checkbox" id="item-2-2-0" /><label for="item-2-2-0">Does Not Use Any JavaScript...</label>
							<ul>
								<li><a href="./">But Relies Only</a></li>
								<li><a href="./">On the Power</a></li>
								<li><a href="./">Of CSS3</a></li>
							</ul>
						</li>
						<li><a href="./">Item 1</a></li>
						<li><a href="./">Item 2</a></li>
						<li><a href="./">Item 3</a></li>
					</ul>
				</li>
				<li><input type="checkbox" id="item-2-1" /><label for="item-2-1">This is a Folder With...</label>
					<ul>
						<li><a href="./">Some Nested Items...</a></li>
						<li><a href="./">Some Nested Items...</a></li>
						<li><a href="./">Some Nested Items...</a></li>
						<li><a href="./">Some Nested Items...</a></li>
						<li><a href="./">Some Nested Items...</a></li>
					</ul>
				</li>
				<li><input type="checkbox" id="item-2-2" disabled="disabled" /><label for="item-2-2">Disabled Nested Items</label>
					<ul>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
						<li><a href="./">item</a></li>
					</ul>
				</li>
			</ul>
		</li>
	</ul>
</div>
```

***CSS***
```
.css-treeview ul,
.css-treeview li
{
	padding: 0;
	margin: 0;
	list-style: none;
}

.css-treeview input
{
	position: absolute;
	opacity: 0;
}

.css-treeview
{
	font: normal 11px "Segoe UI", Arial, Sans-serif;
	-moz-user-select: none;
	-webkit-user-select: none;
	user-select: none;
}

.css-treeview a
{
	color: #00f;
	text-decoration: none;
}

.css-treeview a:hover
{
	text-decoration: underline;
}

.css-treeview input + label + ul
{
	margin: 0 0 0 22px;
}

.css-treeview input + label + ul
{
	display: none;
}

.css-treeview label,
.css-treeview label::before
{
	cursor: pointer;
}

.css-treeview input:disabled + label
{
	cursor: default;
	opacity: .6;
}

.css-treeview input:checked:not(:disabled) + label + ul
{
	display: block;
}

.css-treeview label,
.css-treeview label::before
{
	background: url("icons.png") no-repeat;
}

.css-treeview label,
.css-treeview a,
.css-treeview label::before
{
	display: inline-block;
	height: 16px;
	line-height: 16px;,
	vertical-align: middle;
}

.css-treeview label
{
	background-position: 18px 0;
}

.css-treeview label::before
{
	content: "";
	width: 16px;
	margin: 0 22px 0 0;
	vertical-align: middle;
	background-position: 0 -32px;
}

.css-treeview input:checked + label::before
{
	background-position: 0 -16px;
}

/* webkit adjacent element selector bugfix */
@media screen and (-webkit-min-device-pixel-ratio:0)
{
	.css-treeview 
	{
		-webkit-animation: webkit-adjacent-element-selector-bugfix infinite 1s;
	}
	
	@-webkit-keyframes webkit-adjacent-element-selector-bugfix 
	{
		from 
		{ 
			padding: 0;
		} 
		to 
		{ 
			padding: 0;
		}
	}
}
```

## Absolute Center (Vertical & Horizontal) an Image

***CSS background-image Technique:***
>html { 
   width:100%; 
   height:100%; 
   background:url(logo.png) center center no-repeat;
}


***CSS + Inline Image Technique:***
```
img {
   position: absolute;
   top: 50%;
   left: 50%;
   width: 500px;
   height: 500px;
   margin-top: -250px; /* Half the height */
   margin-left: -250px; /* Half the width */
}
```

***Table technique:***


```
***HTML***

<table id="wrapper">
  <tr>
    <td><img src="logo.png" alt="" /></td>
  </tr>
</table>

***CSS***

html, body, #wrapper {
   height:100%;
   width: 100%;
   margin: 0;
   padding: 0;
   border: 0;
}
#wrapper td {
   vertical-align: middle;
   text-align: center;
}

```


## Star Wars Crawl Text

```
The opening to Star Wars is iconic. The effect of text scrolling both up and away from the screen was both a crazy cool special effect for a movie back in 1977 and a cool typographical style that was brand new at the time.

We can achieve a similar effect with HTML and CSS! This post is more about how to get that sliding text effect rather than trying to re-create the full Star Wars opening sequence or matching the exact styles used in the movie, so let's get to a place where this is the final result:
```

***The Basic HTML***
```
First, let's set up out HTML for the content:
```

***HTML***
```
<section class="star-wars">

  <div class="crawl">
    
    <div class="title">
      <p>Episode IV</p>
      <h1>A New Hope</h1>
    </div>
    
    <p>It is a period of civil war. Rebel spaceships, striking from a hidden base, have won their first victory against the evil Galactic Empire.</p>     
    <p>During the battle, Rebel spies managed to steal secret plans to the Empire’s ultimate weapon, the DEATH STAR, an armored space station with enough power to destroy an entire planet.</p>
    <p>Pursued by the Empire’s sinister agents, Princess Leia races home aboard her starship, custodian of the stolen plans that can save her people and restore freedom to the galaxy…</p>

  </div>

</section>
```

```
This gives us all the pieces we need:

A container called star-wars that we will use to position the content. This is also necessary because we will be using the perspective CSS property, where having a parent element is a helpful way to add depth or skew a child element's transform property.
A container called crawl that will hold the actual text and be the the element that we apply the CSS animation to.
The content!
You may have noticed that the movie title is wrapped in an extra <div> container called title. This is not necessary, but could provide you with additional styling options should you need them.
```

***The Basic CSS***
```
The trick is to imagine a three-dimensional space where the text crawls vertical up the Y-axis and out along the Z-axis. This gives the impression the text is both slide up the screen and away from the viewer at the same time.

First, let's set up the document <body> so that the screen is not scrollable. We want the text to come up from the bottom of the screen without the viewer being able to scroll and see the text before it enters. We can use overflow: hidden to do that:
```

***CSS***
```
body {
  /* Force the body to fill the entire screen */
  width: 100%;
  height: 100%;
  /* Hide elements that flow outside the viewable space */
  overflow: hidden;
  /* Black background for the screen */
  background: #000;
}

Now we can move on to styling our star-wars container, which is the parent element for our demo


.star-wars {
  /* Flexbox to center the entire element on the screen */
  display: flex;
  justify-content: center;
  /* This is a magic number based on the context in which this snippet is used and effects the perspective */
  height: 800px;
  /* This sets allows us to transform the text on a 3D plane, and is somewhat a magic number */
  perspective: 400px;
  /* The rest is totally up to personal styling preferences */
  color: #feda4a;
  font-family: 'Pathway Gothic One', sans-serif;
  font-size: 500%;
  font-weight: 600;
  letter-spacing: 6px;
  line-height: 150%;
  text-align: justify;
}

Next up, we can apply styles to the crawl element. Again, this element is important because it contains the properties that will transform the text and be animated.


.crawl {
  /* Position the element so we can adjust the top property in the animation */
  position: relative;
  /* Making sure the text is fully off the screen at the start and end of the animation */
  top: -100px;
  /* Defines the skew origin at the very center when we apply transforms on the animation */
  transform-origin: 50% 100%;
}

So far, we have a nice looking bunch of text, but it's neither skewed nor animated. Let's make that happen.
```

***Animation!***

```
This is what you really care about, right? First, we're going to define the @keyframes for the animation. The animation is doing a little more than animating for us, because we're going to be adding our transform properties here, particularly for the movement along the Z-axis. We'll start the animation at 0% where the text is closest to the viewer and is located below the screen, out of view, then end the animation at 100% where it is far away from the viewer and flowing up and over the top of the screen.
```

```
/* We're calling this animation "crawl" */
@keyframes crawl {
  0% {
    /* The element starts below the screen */
    top: 0;
    /* Rotate the text 20 degrees but keep it close to the viewer */
    transform: rotateX(20deg) translateZ(0);
  }
  100% { 
    /* This is a magic number, but using a big one to make sure the text is fully off the screen at the end */
    top: -6000px;
    /* Slightly increasing the rotation at the end and moving the text far away from the viewer */
    transform: rotateX(25deg) translateZ(-2500px);
  }
}

Now, let's apply that animation on the .crawl element:

.crawl {
  /* Position the element so we can adjust the top property in the animation */
  position: relative;
  /* Defines the skew origin at the very center when we apply transforms on the animation */
  transform-origin: 50% 100%;
  /* Adds the crawl animation, which plays for one minute */
  animation: crawl 60s linear;
}

```
***Fun Times With Fine-Tuning***

```
You can have a little more fun with things once the main effect is in place. For example, we can add a little fade at the top of the screen to accentuate the effect of the text crawling off into the distance:
```

***HTML***
```
<div class="fade"></div>
```
```
Add that element to the top of the HTML and text will flow behind a gradient that goes from transparent to the same background as the <body>:
```
***CSS**
```
.fade {
  position: relative;
  width: 100%;
  min-height: 60vh;
  top: -25px;
  background-image: linear-gradient(0deg, transparent, black 75%);
  z-index: 1;
}
```

#### The Full Example

>Here is the full code from this post pulled together.

***HTML***
```
<div class="fade"></div>

<section class="star-wars">

  <div class="crawl">

    <div class="title">
      <p>Episode IV</p>
      <h1>A New Hope</h1>
    </div>
    
    <p>It is a period of civil war. Rebel spaceships, striking from a hidden base, have won their first victory against the evil Galactic Empire.</p>      
    <p>During the battle, Rebel spies managed to steal secret plans to the Empire’s ultimate weapon, the DEATH STAR, an armored space station with enough power to destroy an entire planet.</p>
    <p>Pursued by the Empire’s sinister agents, Princess Leia races home aboard her starship, custodian of the stolen plans that can save her people and restore freedom to the galaxy…</p>

  </div>

</section>

```
***CSS***
```
body {
  width: 100%;
  height: 100%;
  background: #000;
  overflow: hidden;
}

.fade {
  position: relative;
  width: 100%;
  min-height: 60vh;
  top: -25px;
  background-image: linear-gradient(0deg, transparent, black 75%);
  z-index: 1;
}

.star-wars {
  display: flex;
  justify-content: center;
  position: relative;
  height: 800px;
  color: #feda4a;
  font-family: 'Pathway Gothic One', sans-serif;
  font-size: 500%;
  font-weight: 600;
  letter-spacing: 6px;
  line-height: 150%;
  perspective: 400px;
  text-align: justify;
}

.crawl {
  position: relative;
  top: 9999px;
  transform-origin: 50% 100%;
  animation: crawl 60s linear;
}

.crawl > .title {
  font-size: 90%;
  text-align: center;
}

.crawl > .title h1 {
  margin: 0 0 100px;
  text-transform: uppercase;
}

@keyframes crawl {
  0% {
    top: 0;
    transform: rotateX(20deg)  translateZ(0);
  }
  100% { 
    top: -6000px;
    transform: rotateX(25deg) translateZ(-2500px);
  }
}
```


## Drop Caps

***Cross-browser way (extra markup)***

```
Just wrap the first character of the paragraph in a span, then target the span with CSS and style away.
```

***HTML***
```
<p><span class="firstcharacter">L</span> orem ipsum dolor sit amet, consectetur adipiscing elit. Mauris tristique lobortis orci ac lacinia. Fusce eu purus eget diam vehicula auctor nec eu elit. Morbi consequat facilisis orci vel malesuada. Donec ultrices molestie sollicitudin. Aliquam pharetra libero enim. Donec et suscipit massa. Donec dui odio, dignissim non sodales et, tincidunt a sapien. Phasellus elit nibh, adipiscing sed blandit vel, interdum et arcu.
</p>
```

***CSS***
```
.firstcharacter {
  color: #903;
  float: left;
  font-family: Georgia;
  font-size: 75px;
  line-height: 60px;
  padding-top: 4px;
  padding-right: 8px;
  padding-left: 3px;
}
```

#### CSS3 way (no extra markup)
```
Target the first character of the first paragraph using pseudo class selectors. No extra markup needed, but no IE < 9 support.
```
 
***HTML***
```
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris tristique lobortis orci ac lacinia. Fusce eu purus eget diam vehicula auctor nec eu elit. Morbi consequat facilisis orci vel malesuada. Donec ultrices molestie sollicitudin. Aliquam pharetra libero enim. Donec et suscipit massa. Donec dui odio, dignissim non sodales et, tincidunt a sapien. Phasellus elit nibh, adipiscing sed blandit vel, interdum et arcu.
</p>
```

***CSS***
```
p:first-child:first-letter {
  color: #903;
  float: left;
  font-family: Georgia;
  font-size: 75px;
  line-height: 60px;
  padding-top: 4px;
  padding-right: 8px;
  padding-left: 3px;
}
```

#### The initial-letter way

```
The browser support for initial-letter is pretty sparse at the time of this writing, but it can be used to calculate the number of lines the drop capped letter should occupy and the font size instead of doing that on your own.
```
***CSS***
```
p:first-child:first-letter {
  color: #903; 
  font-family: Georgia;
  initial-letter: 2;
}
```


## Hide Scrollbar in Edge, IE 10/11

```
You can make it auto-hiding instead of always-showing:
```

***CSS***
```
html {
  -ms-overflow-style: -ms-autohiding-scrollbar;
}
```



## Force Vertical Scrollbar

***CSS***
```
html {
  overflow-y: scroll;
}
```
```
This is invalid CSS, but it works in everything except Opera. The reason for this is to prevent "centering jumps" when navigating back and forth between pages with enough content to have a vertical scroll bar and pages that do not.
```


## CSS Triangle

***HTML***
```
You can make them with a single div. It's nice to have classes for each direction possibility.
```
```
<div class="arrow-up"></div>
<div class="arrow-down"></div>
<div class="arrow-left"></div>
<div class="arrow-right"></div>
```

***CSS***
```
The idea is a box with zero width and height. The actual width and height of the arrow is determined by the width of the border. In an up arrow, for example, the bottom border is colored while the left and right are transparent, which forms the triangle.
```
```
.arrow-up {
  width: 0; 
  height: 0; 
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  
  border-bottom: 5px solid black;
}

.arrow-down {
  width: 0; 
  height: 0; 
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
  
  border-top: 20px solid #f00;
}

.arrow-right {
  width: 0; 
  height: 0; 
  border-top: 60px solid transparent;
  border-bottom: 60px solid transparent;
  
  border-left: 60px solid green;
}

.arrow-left {
  width: 0; 
  height: 0; 
  border-top: 10px solid transparent;
  border-bottom: 10px solid transparent; 
  
  border-right:10px solid blue; 
}
```


## Keyframe Animation Syntax

**Basic Declaration & Usage**

***CSS***
```
@-webkit-keyframes NAME-YOUR-ANIMATION {
  0%   { opacity: 0; }
  100% { opacity: 1; }
}
@-moz-keyframes NAME-YOUR-ANIMATION {
  0%   { opacity: 0; }
  100% { opacity: 1; }
}
@-o-keyframes NAME-YOUR-ANIMATION {
  0%   { opacity: 0; }
  100% { opacity: 1; }
}
@keyframes NAME-YOUR-ANIMATION {
  0%   { opacity: 0; }
  100% { opacity: 1; }
}


#box {
  -webkit-animation: NAME-YOUR-ANIMATION 5s infinite; /* Safari 4+ */
  -moz-animation:    NAME-YOUR-ANIMATION 5s infinite; /* Fx 5+ */
  -o-animation:      NAME-YOUR-ANIMATION 5s infinite; /* Opera 12+ */
  animation:         NAME-YOUR-ANIMATION 5s infinite; /* IE 10+, Fx 29+ */
}

```
>For the sake of brevity the rest of the code on this page will not use any prefixes, but real world usage should use all the vendor prefixes from above


**Multiple steps**

***CSS***
```
@keyframes fontbulger {
  0% {
    font-size: 10px;
  }
  30% {
    font-size: 15px;
  }
  100% {
    font-size: 12px;
  }
}

#box {
   animation: fontbulger 2s infinite;
}
```
>If an animation has the same starting and ending properties, one way to do that is to comma-separate the 0% and 100% values:

***CSS***
```
@keyframes fontbulger {
  0%, 100% {
    font-size: 10px;
  }
  50% {
    font-size: 12px;
  }
}
```
>Or, you could always tell the animation to run twice (or any even number of times) and tell the direction to alternate.

***Animation Shorthand***

```
Just space-separate all the individual values. The order doesn't matter except when using both duration and delay, they need to be in that order. In the example below 1s = duration, 2s = delay, 3 = iterations.
```

***CSS**
```
animation: test 1s 2s 3 alternate backwards
```

***Combine transform and animation***

***CSS**
```
@keyframes infinite-spinning {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
```

***Multiple animations***
```
You can comma-separate the values to declare multiple animations on a selector.
```

***CSS***
```
.animate-this {
   animation: 
      first-animation 2s infinite, 
      another-animation 1s;
}
```

***Steps()***
```
The steps() function controls exactly how many keyframes will render in the animation timeframe. Let's say you declare:
```

***CSS***
```
@keyframes move {
  from { top: 0; left: 0; }
  to   { top: 100px; left: 100px; }
}
```

>If you use steps(10) in your animation, it will make sure only 10 keyframes happen in the allotted time.

```
.move {
  animation: move 10s steps(10) infinite alternate;
}
```


## Tucked Corners

***HTML***
```
<div class="corners">
   Content
</div>
```

***CSS***
```
body {
  background: #e6e6e6;
}

.corners { 
  background: #f6f6f6;
  height: 700px;
  margin: 50px auto;
  max-width: 600px;
  position: relative;
  width: 80%;
  box-shadow: 0 1px 7px hsla(0, 0%, 0%, 0.2);
}

/* Corner Effect */
.corners:after,
.corners:before {
  background: #e6e6e6;
  content: '';
  height: 50px;
  position: absolute;
  top: -25px;
  width: 100px;
  box-shadow: 0 5px 10px -7px hsla(0, 0% ,0%, 0.5);
}
.corners:after {
  left: -50px;
  transform: rotate(-45deg);
}
.corners:before {
  right: -50px;
  transform: rotate(45deg);
}

```


## Monotone an Image with CSS

>You can always apply a filter to an element to make it monotone in the grayscale sense:

***HTML***
```
<img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/3/sara-shirt-example.jpg">

<img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/3/sara-shirt-example.jpg" class="filtered">

```

***CSS***
```
.filtered {
  -webkit-filter: grayscale(100%);
  filter: grayscale(100%);
}

img {
  float: left;
  max-width: 50%;
  border: 10px solid white;
}

* {
  box-sizing: border-box;
}
```

>If you put that in a container with a background color and lower the opacity, you can get a colored monotone kind of effect:

***HTML***
```
<img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/3/sara-shirt-example.jpg" class="not-filtered">

<div class="filtered">
  <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/3/sara-shirt-example.jpg">
</div>
```

***CSS***
```
.filtered {
   background: yellow;
   position: relative;
}
.filtered img {
  -webkit-filter: grayscale(100%);
  filter: grayscale(100%);
  opacity: 0.5;
}

.filtered,
.not-filtered {
  float: left;
  max-width: 50%;
  border: 10px solid white;
}
img {
  display: block;
  max-width: 100%;
}
* {
  box-sizing: border-box;
}
```

>Maarten van der Velde wrote in to say that rather than lowering the opacity, we can combine it with mix-blend-mode and blowing out the contrast:

***HTML***
```
<img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/3/sara-shirt-example.jpg" class="not-filtered">

<div class="filtered">
  <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/3/sara-shirt-example.jpg">
</div>
```

***CSS***
```
.filtered {
   background: #00c2ff;
}

.filtered img {
  mix-blend-mode: screen;
  -webkit-filter: grayscale(100%) contrast(200%);
  filter: grayscale(100%) contrast(200%);
  opacity: 1;
}

.filtered,
.not-filtered {
  float: left;
  max-width: 50%;
  border: 10px solid white;
}
img {
  display: block;
  max-width: 100%;
}
* {
  box-sizing: border-box;
}
```

>Amelia Bellamy-Royds also covered using SVG color filters to do this, which has an amazing amount of control:

***HTML***
```
<svg class="defs-only">
  <filter id="monochrome" color-interpolation-filters="sRGB"
          x="0" y="0" height="100%" width="100%">
    <feColorMatrix type="matrix"
      values="0.95 0 0 0 0.05 
              0.85 0 0 0 0.15  
              0.50 0 0 0 0.50 
              0    0 0 1 0" />
  </filter>
</svg>
<a class="profile-link" href="#" title="More about Amelia Bellamy-Royds">
  <img class="profile-pic" src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/91525/AmeliaBR-bw.jpg"/></a>
<a class="profile-link" href="#" title="More about AmeliaBR">
  <img class="profile-pic" src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/91525/AmeliaBR2-bw.jpg"/></a>

```

***CSS***
```
.profile-link {
  display: inline-block;
  padding: 1em;
  width: 10em;
  max-width: 80%;
}
.profile-pic {
  width: 100%;
  height: auto;
  border-radius: 50%;
  box-shadow: #222 0.2em 0.2em 1em;
  /*
  transition: filter 0.3s, box-shadow 0.3s;
  -webkit-transition: filter 0.3s, -webkit-filter 0.3s, box-shadow 0.3s;
}
.profile-link:hover .profile-pic, 
.profile-link:focus .profile-pic {
  */
  -webkit-filter: url(#monochrome);
  filter:  url(#monochrome);
  box-shadow: #224 0.2em 0.2em 0.6em 0.1em;
}
.defs-only {
  position: absolute;
  height: 0; width: 0;
  overflow: none;
  left: -100%;
}
```

## Sticky Footer

>Works great if you can apply a fixed height to the footer.

***HTML***
```
<div class="page-wrap">
  
  Content!
      
</div>

<footer class="site-footer">
  I'm the Sticky Footer.
</footer>
```

***CSS***
```
* {
  margin: 0;
}
html, body {
  height: 100%;
}
.page-wrap {
  min-height: 100%;
  /* equal to footer height */
  margin-bottom: -142px; 
}
.page-wrap:after {
  content: "";
  display: block;
}
.site-footer, .page-wrap:after {
  height: 142px; 
}
.site-footer {
  background: orange;
}
```


## Comments in CSS

```
The stuff inside the /* */ marks are CSS comments. This allows you to enter notes into CSS that will not be interpreted. In this case, this comment lets someone reading the CSS file know that that particular line of CSS was intended to allow for using ems to set font size later in the CSS in a more intuitive base 10 way.
```


## Corner Ribbon

***HTML***
```
<div class="wrapper">
       <div class="ribbon-wrapper-green"><div class="ribbon-green">NEWS</div></div>
</div>​
```

***CSS***
```
.wrapper {
  margin: 50px auto;
  width: 280px;
  height: 370px;
  background: white;
  border-radius: 10px;
  -webkit-box-shadow: 0px 0px 8px rgba(0,0,0,0.3);
  -moz-box-shadow:    0px 0px 8px rgba(0,0,0,0.3);
  box-shadow:         0px 0px 8px rgba(0,0,0,0.3);
  position: relative;
  z-index: 90;
}

.ribbon-wrapper-green {
  width: 85px;
  height: 88px;
  overflow: hidden;
  position: absolute;
  top: -3px;
  right: -3px;
}

.ribbon-green {
  font: bold 15px Sans-Serif;
  color: #333;
  text-align: center;
  text-shadow: rgba(255,255,255,0.5) 0px 1px 0px;
  -webkit-transform: rotate(45deg);
  -moz-transform:    rotate(45deg);
  -ms-transform:     rotate(45deg);
  -o-transform:      rotate(45deg);
  position: relative;
  padding: 7px 0;
  left: -5px;
  top: 15px;
  width: 120px;
  background-color: #BFDC7A;
  background-image: -webkit-gradient(linear, left top, left bottom, from(#BFDC7A), to(#8EBF45)); 
  background-image: -webkit-linear-gradient(top, #BFDC7A, #8EBF45); 
  background-image:    -moz-linear-gradient(top, #BFDC7A, #8EBF45); 
  background-image:     -ms-linear-gradient(top, #BFDC7A, #8EBF45); 
  background-image:      -o-linear-gradient(top, #BFDC7A, #8EBF45); 
  color: #6a6340;
  -webkit-box-shadow: 0px 0px 3px rgba(0,0,0,0.3);
  -moz-box-shadow:    0px 0px 3px rgba(0,0,0,0.3);
  box-shadow:         0px 0px 3px rgba(0,0,0,0.3);
}

.ribbon-green:before, .ribbon-green:after {
  content: "";
  border-top:   3px solid #6e8900;   
  border-left:  3px solid transparent;
  border-right: 3px solid transparent;
  position:absolute;
  bottom: -3px;
}

.ribbon-green:before {
  left: 0;
}
.ribbon-green:after {
  right: 0;
}​
```


## Orientation Lock

***CSS***
```
@media screen and (min-width: 320px) and (max-width: 767px) and (orientation: landscape) {
  html {
    transform: rotate(-90deg);
    transform-origin: left top;
    width: 100vh;
    overflow-x: hidden;
    position: absolute;
    top: 100%;
    left: 0;
  }
}
```


## Prevent Superscripts and Subscripts from Affecting Line-Height

***CSS***

```
sup, sub {
  vertical-align: baseline;
  position: relative;
  top: -0.4em;
}
sub { 
  top: 0.4em; 
}
```

## Two-Color Three-Dimensional Blocks and Text

```
We can use multiple text-shadow and box-shadow values to create a three-dimensional look to blocks or text, like this screenshot of David DeSandro's footer. However in that example, the "three dimesional" part is a solid color.

By alternating colors back and forth in the "stacking order" of our box or text shadow declaration, we can simulate a more three dimensional / lighted effect.
```
***CSS**
```
text-shadow:   1px 0px #eee, 0px 1px #ccc,
               2px 1px #eee, 1px 2px #ccc,
               3px 2px #eee, 2px 3px #ccc,
               4px 3px #eee, 3px 4px #ccc,
               5px 4px #eee, 4px 5px #ccc,
               6px 5px #eee, 5px 6px #ccc,
               7px 6px #eee, 6px 7px #ccc,
               8px 7px #eee, 7px 8px #ccc,
               8px 8px #eee;

```

## Ribbon

***HTML***
```
<h1 class="ribbon">
   <strong class="ribbon-content">Everybody loves ribbons</strong>
</h1>
```

***CSS***
```
.ribbon {
 font-size: 16px !important;
 /* This ribbon is based on a 16px font side and a 24px vertical rhythm. I've used em's to position each element for scalability. If you want to use a different font size you may have to play with the position of the ribbon elements */

 width: 50%;
    
 position: relative;
 background: #ba89b6;
 color: #fff;
 text-align: center;
 padding: 1em 2em; /* Adjust to suit */
 margin: 2em auto 3em; /* Based on 24px vertical rhythm. 48px bottom margin - normally 24 but the ribbon 'graphics' take up 24px themselves so we double it. */
}
.ribbon:before, .ribbon:after {
 content: "";
 position: absolute;
 display: block;
 bottom: -1em;
 border: 1.5em solid #986794;
 z-index: -1;
}
.ribbon:before {
 left: -2em;
 border-right-width: 1.5em;
 border-left-color: transparent;
}
.ribbon:after {
 right: -2em;
 border-left-width: 1.5em;
 border-right-color: transparent;
}
.ribbon .ribbon-content:before, .ribbon .ribbon-content:after {
 content: "";
 position: absolute;
 display: block;
 border-style: solid;
 border-color: #804f7c transparent transparent transparent;
 bottom: -1em;
}
.ribbon .ribbon-content:before {
 left: 0;
 border-width: 1em 0 0 1em;
}
.ribbon .ribbon-content:after {
 right: 0;
 border-width: 1em 1em 0 0;
}
```

#### Protector

```
This technique uses negative z-index values on some of the pseudo elements. That means that they can go behind other elements that have opaque backgrounds, which ruins the effect. To fix this, you'll need to make sure the immediate parent of the ribbons does not have a background applied and has relative postioning with positive z-index. Use an additional wrapper if needed.
```

***HTML***
```
<div class="non-semantic-protector"> 
   <!-- ribbons and other content in here -->
</div>
```

***CSS***
```
.non-semantic-protector { position: relative; z-index: 1; }
```


## Toggle Visibility When Hiding Elements

```
The development team at Medium have discussed some bad practices that break accessibility. In one example, they argue that opacity is not well supported by screen readers and so if we want to hide an element in a transition then we should always use the visibility attribute, too:
```

***CSS***
```
.m-fadeOut {
  visibility: hidden;
  opacity: 0;
  transition: visibility 0s linear 300ms, opacity 300ms;
}
.m-fadeIn {
  visibility: visible;
  opacity: 1;
  transition: visibility 0s linear 0s, opacity 300ms;
}
```
>https://css-tricks.com/snippets/css/toggle-visibility-when-hiding-elements/


## “Shake” CSS Keyframe Animation

```
This assumes the use of an autoprefixer.
```

***CSS***
```
.face:hover {
  animation: shake 0.82s cubic-bezier(.36,.07,.19,.97) both;
  transform: translate3d(0, 0, 0);
  backface-visibility: hidden;
  perspective: 1000px;
}

@keyframes shake {
  10%, 90% {
    transform: translate3d(-1px, 0, 0);
  }
  
  20%, 80% {
    transform: translate3d(2px, 0, 0);
  }

  30%, 50%, 70% {
    transform: translate3d(-4px, 0, 0);
  }

  40%, 60% {
    transform: translate3d(4px, 0, 0);
  }
}
```

## Momentum Scrolling on iOS Overflow Elements

```
Web pages on iOS by default have a "momentum" style scrolling where a flick of the finger sends the web page scrolling and it keeps going until eventually slowing down and stopping as if friction is slowing it down. Like if you were to push a hockey puck across the ice or something. You might think that any element with scrolling would have this behavior as well, but it doesn't. You can add it back with a special property.
```

***CSS***

```
.module {
  width: 300px;
  height: 200px;

  overflow-y: scroll; /* has to be scroll, not auto */
  -webkit-overflow-scrolling: touch;
}
```

## Font Shorthand

```
body {
  font: font-style font-variant font-weight font-size/line-height font-family;
}
```

## Basics of Google Font API

```
Link to CSS files
You essentially hotlink directly to CSS files on Google.com. Through URL parameters, you specificity which fonts you want, and what variations of those fonts.
```
***HTML***
```
<head>
  
   ...

   <link rel="stylesheet" type="text/css" href="http://fonts.googleapis.com/css?family=Tangerine:bold,bolditalic|Inconsolata:italic|Droid+Sans">
</head>
```
```
Idea: You can avoid an extra network request by opening that stylesheet and copy-and-pasting the @font-face stuff into your main stylesheet. But beware: Google does some User Agent sniffing stuff to sometimes serve different things to different devices as needed. You won't benefit from that if done this way.
```

***CSS***

>CSS
In your CSS you can then specify these new fonts by name on any element you wish to use them.

```
body { 
  font-family: 'Tangerine', 'Inconsolata', 'Droid Sans', serif; 
  font-size: 48px; 
}
```

#### FontLoader
```
You can use the FontLoader JavaScript instead of linking to the CSS. It has advantages, like controlling the Flash of Unstyled Text (FOUT), and also disadvantages, like the fact that the fonts won't load for users with JavaScript off.
```

***HTML***
```
<script src="http://ajax.googleapis.com/ajax/libs/webfont/1/webfont.js"></script>
<script type="text/javascript">
  WebFont.load({
    google: {
      families: ['Cantarell']
    }
  });
</script>
<style type="text/css">
  .wf-loading h1 { visibility: hidden; }
  .wf-active h1, .wf-inactive h1 { 
    visibility: visible; font-family: 'Cantarell'; 
  }
</style>
```
>Those class names, e.g .wf-loading get applied to the <html> element. So notice when the fonts are "loading", you can use that class name to hide the text. Then when they are shown, make them visible again. That is how FOUT is controlled.


## Multiple Borders

```
- Using pseudo element(s)

You can position a pseudo element such that it's either behind the element, and larger, making a border effect with it's own background, or smaller and inside (but make sure the content gets positioned on top).

The element needing multiple borders should have its own border and relative positioning.
```

***CSS***
```
.borders {
  position: relative;
  border: 5px solid #f00;
}
```

```
The secondary border is added with a pseudo element. It is set with absolute positioning and inset with top/left/bottom/right values. This will also have a border and is kept beneath the content (preserving, for example, selectability of text and clickability of links) by giving it a negative z-index value. Careful with negative z-index, if this is within yet another element with it's own background color, this may not work.
```

***CSS***
```
.borders:before {
  content: " ";
  position: absolute;
  z-index: -1;
  top: 5px;
  left: 5px;
  right: 5px;
  bottom: 5px;
  border: 5px solid #ffea00;
}
```
```
You can do a third border by using the :after pseudo class as well. Take special note that Firefox 3 (pre 3.6) screws this up by supporting :after and :before, but not allowing them to be absolutely positioned (so it looks weird).
```

```
Using outline

While it's a bit more limited than border (goes around entire element no matter what) outline is a extra free border.
```

***CSS***
```
.borders {
  border: 5px solid blue; 
  outline: 5px solid red;
}
```

```
Using box-shadow
You can use box-shadow to make a border effect, by making the the shadow offset and have 0 blur. Plus, by comma-separating values, you can have as many "borders" as you like:
```

***CSS***
```
.blur {
  box-shadow:
    0 0 0 10px hsl(0, 0%, 80%),
    0 0 0 15px hsl(0, 0%, 90%);
}
```

```
Using a clipped background
You can make the background of an element stop before the padding. That way an elements normal border can look like a double border in a way.
```

***CSS***
```
.borders {
  border: solid 1px #f06d06;
  padding: 5px;
  background-clip: content-box; /* support: IE9+ */
  background-color: #ccc;
}
```

## Cross Browser Opacity

```
These days, you really don't have to worry about opacity being a difficult thing cross-browser. You just use the opacity property, like this:
```
***CSS***
```
.thing {
  opacity: 0.5;
}
```

>0 is totally transparent (will not be visible at all, like visibility: hidden;) and 1 is totally opaque (default). Anything in between is partially transparent.

>For historical reasons, this is how is we used to do it:

***CSS***
```
.transparent_class {
  /* IE 8 */
  -ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity=50)";

  /* IE 5-7 */
  filter: alpha(opacity=50);

  /* Netscape */
  -moz-opacity: 0.5;

  /* Safari 1.x */
  -khtml-opacity: 0.5;

  /* Good browsers */
  opacity: 0.5;
}
```


## Scale on Hover with Transition

>Bring your own prefixes!

***CSS***
```
.grow { transition: all .2s ease-in-out; }
.grow:hover { transform: scale(1.1); }
```

## Gradient Underlines

***CSS***
```
a {
  position: relative;
  padding-bottom: 2px;
  text-decoration: none;
}

a:hover::after {
  content: "";
  position: absolute;
  bottom: 2px;
  left: 0;
  height: 1px;
  width: 100%;
  background: #444;
  background: linear-gradient(left, transparent 0%,#444 50%,transparent 100%);
 }

```

## Glowing Blue Input Highlights

```
Like mid-2012 Twitter.
```
***CSS***
```
input[type=text], textarea {
  -webkit-transition: all 0.30s ease-in-out;
  -moz-transition: all 0.30s ease-in-out;
  -ms-transition: all 0.30s ease-in-out;
  -o-transition: all 0.30s ease-in-out;
  outline: none;
  padding: 3px 0px 3px 3px;
  margin: 5px 1px 3px 0px;
  border: 1px solid #DDDDDD;
}
 
input[type=text]:focus, textarea:focus {
  box-shadow: 0 0 5px rgba(81, 203, 238, 1);
  padding: 3px 0px 3px 3px;
  margin: 5px 1px 3px 0px;
  border: 1px solid rgba(81, 203, 238, 1);
}

```

## Simple and Nice Blockquote Styling

```
The blockquote displays in standards-compliant browsers with the "big quotes before" effect, and in IE with a thick left border and a light grey background.
Unlike other blockquote techniques, this style does not require a nested block-level element (like p). As such, it turns a paragraph into an inline-styled element to keep the content from dropping below the quote.
```

***CSS***
```
blockquote {
  background: #f9f9f9;
  border-left: 10px solid #ccc;
  margin: 1.5em 10px;
  padding: 0.5em 10px;
  quotes: "\201C""\201D""\2018""\2019";
}
blockquote:before {
  color: #ccc;
  content: open-quote;
  font-size: 4em;
  line-height: 0.1em;
  margin-right: 0.25em;
  vertical-align: -0.4em;
}
blockquote p {
  display: inline;
}
```

>https://css-tricks.com/examples/Blockquotes/


## Transparent Background Images

```
There is no CSS property background-opacity, but you can fake it by inserting a pseudo element with regular opacity the exact size of the element behind it.
```

***CSS***
```
div {
  width: 200px;
  height: 200px;
  display: block;
  position: relative;
}

div::after {
  content: "";
  background: url(image.jpg);
  opacity: 0.5;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  position: absolute;
  z-index: -1;   
}
```

## Mixins for Rem Font Sizing
```
The rem font-size unit is similar to em, only instead of cascading it's always relative to the root (html) element (more information). This has pretty good modern browser support, it's just IE 8 and down we need to provide px fallbacks for.
```
```
Instead of repeating ourselves everywhere, we can use a LESS or SASS mixins to keep it clean. These mixins assumes:
```
***CSS***
```
html {
  font-size: 62.5%; /* Sets up the Base 10 stuff */
}
```

***CSS***
```
body {
  margin: 160px 320px 480px 640px;
  margin: 10rem 20rem 30rem 40rem; 
}
```

>For More Information use this link
https://css-tricks.com/snippets/css/less-mixin-for-rem-font-sizing/



## Browser Specific Hacks

***CSS***
```
/***** Selector Hacks ******/

/* IE6 and below */
* html #uno  { color: red }
 
/* IE7 */
*:first-child+html #dos { color: red } 
 
/* IE7, FF, Saf, Opera  */
html>body #tres { color: red }
 
/* IE8, FF, Saf, Opera (Everything but IE 6,7) */
html>/**/body #cuatro { color: red }
 
/* Opera 9.27 and below, safari 2 */
html:first-child #cinco { color: red }
 
/* Safari 2-3 */
html[xmlns*=""] body:last-child #seis { color: red }
 
/* safari 3+, chrome 1+, opera9+, ff 3.5+ */
body:nth-of-type(1) #siete { color: red }
 
/* safari 3+, chrome 1+, opera9+, ff 3.5+ */
body:first-of-type #ocho {  color: red }
 
/* saf3+, chrome1+ */
@media screen and (-webkit-min-device-pixel-ratio:0) {
 #diez  { color: red  }
}
 
/* iPhone / mobile webkit */
@media screen and (max-device-width: 480px) {
 #veintiseis { color: red  }
}
 
/* Safari 2 - 3.1 */
html[xmlns*=""]:root #trece  { color: red  }
 
/* Safari 2 - 3.1, Opera 9.25 */
*|html[xmlns*=""] #catorce { color: red  }
 
/* Everything but IE6-8 */
:root *> #quince { color: red  }
 
/* IE7 */
*+html #dieciocho {  color: red }
 
/* Firefox only. 1+ */
#veinticuatro,  x:-moz-any-link  { color: red }
 
/* Firefox 3.0+ */
#veinticinco,  x:-moz-any-link, x:default  { color: red  }
 
 
 
/***** Attribute Hacks ******/
 
/* IE6 */
#once { _color: blue }
 
/* IE6, IE7 */
#doce { *color: blue; /* or #color: blue */ }
 
/* Everything but IE6 */
#diecisiete { color/**/: blue }
 
/* IE6, IE7, IE8 */
#diecinueve { color: blue\9; }
 
/* IE7, IE8 */
#veinte { color/*\**/: blue\9; }
 
/* IE6, IE7 -- acts as an !important */
#veintesiete { color: blue !ie; } /* string after ! can be anything */

```

>Check out BrowserHacks.com for more.
http://browserhacks.com/


## “Stitched” Look

***HTML***
```
<div class="stitched">

  Stitched

</div>
```

***CSS***
```
.stitched {
   padding: 20px;
   margin: 10px;
   background: #ff0030;
   color: #fff;
   font-size: 21px;
   font-weight: bold;
   line-height: 1.3em;
   border: 2px dashed #fff;
   border-radius: 10px;
   box-shadow: 0 0 0 4px #ff0030, 2px 1px 6px 4px rgba(10, 10, 0, 0.5);
   text-shadow: -1px -1px #aa3030;
   font-weight: normal;
}

body {
  padding: 10px;
}
```

## Retina Display Media Query

```
For including high-res graphics, but only for screens that can make use of them. "Retina" being "2x":
```
***CSS***
```
@media 
(-webkit-min-device-pixel-ratio: 2), 
(min-resolution: 192dpi) { 
    /* Retina-specific stuff here */
}
```
>Or other highish-res:

***CSS***
```
/* 1.25 dpr */
@media 
(-webkit-min-device-pixel-ratio: 1.25), 
(min-resolution: 120dpi){ 
    /* Retina-specific stuff here */
}

/* 1.3 dpr */
@media 
(-webkit-min-device-pixel-ratio: 1.3), 
(min-resolution: 124.8dpi){ 
    /* Retina-specific stuff here */
}

/* 1.5 dpr */
@media 
(-webkit-min-device-pixel-ratio: 1.5), 
(min-resolution: 144dpi){ 
    /* Retina-specific stuff here */
}
```


#### Old Stuff (don't use, keeping for posterity)

***CSS***
```
@media
only screen and (-webkit-min-device-pixel-ratio: 2),
only screen and (   min--moz-device-pixel-ratio: 2),
only screen and (     -o-min-device-pixel-ratio: 2/1) { 
  
  /* Retina-specific stuff here */

}
```
```
@media
only screen and (-webkit-min-device-pixel-ratio: 2),
only screen and (   min--moz-device-pixel-ratio: 2),
only screen and (     -o-min-device-pixel-ratio: 2/1),
only screen and (        min-device-pixel-ratio: 2),
only screen and (                min-resolution: 192dpi),
only screen and (                min-resolution: 2dppx) { 
  
  /* Retina-specific stuff here */

}
```

- Notes:
    - The super weird min--moz-device-pixel-ratio is probably a bug, might wanna put in -moz-min-device-pixel-ratio also in case they fix it but leave it prefixed.
    - Here's the spec on resolution units.

```
Example:

Let's say you had three major breakpoints in a design. This design also had a large background graphic and you wanted it looking it's best on any screen (retina or not) and not waste any bandwidth. You'd set up 6 media queries, one for each breakpoint and one for each one of those breakpoints on retina. Then you'd override the background image all the way down.
```
***CSS***
```
@media only screen and (min-width: 320px) {

  /* Small screen, non-retina */

}

@media
only screen and (-webkit-min-device-pixel-ratio: 2)      and (min-width: 320px),
only screen and (   min--moz-device-pixel-ratio: 2)      and (min-width: 320px),
only screen and (     -o-min-device-pixel-ratio: 2/1)    and (min-width: 320px),
only screen and (        min-device-pixel-ratio: 2)      and (min-width: 320px),
only screen and (                min-resolution: 192dpi) and (min-width: 320px),
only screen and (                min-resolution: 2dppx)  and (min-width: 320px) { 

  /* Small screen, retina, stuff to override above media query */

}

@media only screen and (min-width: 700px) {

  /* Medium screen, non-retina */

}

@media
only screen and (-webkit-min-device-pixel-ratio: 2)      and (min-width: 700px),
only screen and (   min--moz-device-pixel-ratio: 2)      and (min-width: 700px),
only screen and (     -o-min-device-pixel-ratio: 2/1)    and (min-width: 700px),
only screen and (        min-device-pixel-ratio: 2)      and (min-width: 700px),
only screen and (                min-resolution: 192dpi) and (min-width: 700px),
only screen and (                min-resolution: 2dppx)  and (min-width: 700px) { 

  /* Medium screen, retina, stuff to override above media query */

}

@media only screen and (min-width: 1300px) {

  /* Large screen, non-retina */

}

@media
only screen and (-webkit-min-device-pixel-ratio: 2)      and (min-width: 1300px),
only screen and (   min--moz-device-pixel-ratio: 2)      and (min-width: 1300px),
only screen and (     -o-min-device-pixel-ratio: 2/1)    and (min-width: 1300px),
only screen and (        min-device-pixel-ratio: 2)      and (min-width: 1300px),
only screen and (                min-resolution: 192dpi) and (min-width: 1300px),
only screen and (                min-resolution: 2dppx)  and (min-width: 1300px) { 

  /* Large screen, retina, stuff to override above media query */

}
 Wufoo
Chris CoyierWufoo powers all our web forms here at CSS-Tricks, and has for over a decade!
Wufoo Sponsorship
 Illustration of laptop with a security check
Chris Coyier One of the many features of the Jetpack plugin for WordPress is backups and security. We use it 
```


## Style Placeholder Text -- :placeholder-shown

```
The :placeholder-shown pseudo-class selects the input element itself when placeholder text exists in a form input. Think of it as a nice way to distinguish between inputs that are currently showing placeholder text versus those that are not.

```
***HTML***
```
<form>
  
  <input type="text" placeholder="Placeholder text" value="Currently has a value (not showing placeholder).">
  
  <input type="text" placeholder="Currently has no value (showing placeholder).">
  
</form>
```

***CSS***
```
input {
  font-size: 1.5rem;
  margin: 10px;
  padding: 10px;
  width: 65%;
}
input:placeholder-shown {
  border: 5px solid red;
}



html, body {
  background: #333;
}

body {
  padding-top: 4em;
}

form {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
```

#### The idea behind placeholders
```
Text-based <input>s and the <textarea> input can have placeholder text. It's text that is shown when the input is empty, to suggest a possible value. For example, a form asking for a school might have a label for what it's asking for, but then suggest "Forest Hills Example High School" in the placeholder as an example value:
```

***HTML***
```
<code><label for="school">School Name:</label>
<input placeholder="Forest Hills Example High School" type="text" name="school" id="school">
```

#### The difference between :placeholder-shown and ::placeholder

```
:placeholder-shown is for selecting the input itself when it's placeholder text is being shown. As opposed to ::placeholder which styles the placeholder text.

I found this highly confusing as

the specs only have :placeholder-shown and not ::placeholder
:placeholder-shown can still affect the styling of the placeholder text, since it's a parent element (e.g. font-size).
Note that :placeholder-shown is a pseudo class (it's an element in a particular state) and ::placeholder is a pseudo element (a visible thing that isn't really in the DOM). Distinguishable by single-versus-double colons.

Tab Atkins cleared it up for me via email:

:placeholder-shown, being a pseudo-class, has to select an existing element - it selects the input whenever you're in the placeholder-showing state. The ::placeholder pseudo-element wraps the actual placeholder text.
```
>For More Detail
https://css-tricks.com/almanac/selectors/p/placeholder-shown/


## Gradient Text

```
This is WebKit only, but is the cleanest way to accomplish it as the text remains editable and selectable web text.
```

***CSS***
```
h1 {
  font-size: 72px;
  background: -webkit-linear-gradient(#eee, #333);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
```


## Turn Off Number Input Spinners

```
WebKit desktop browsers add little up down arrows to number inputs called spinners. You can turn them off visually like this:

```
***CSS***
```
input[type=number]::-webkit-inner-spin-button, 
input[type=number]::-webkit-outer-spin-button { 
  -webkit-appearance: none; 
  margin: 0; 
}
```

```
Note that some other functionality still exists, like being able to increment the number via the scroll wheel on a mouse.
```

## Accessibility/SEO Friendly CSS Hiding
```
Removes an item from the page, without affecting page flow or causing scrollbars. Much better than display: none; or even visibility: hidden;
```

***CSS***

```
#content {
    position: absolute;
    top: -9999px;
    left: -9999px;
}
```

## Make “Pre” Text Wrap

```
Text in <pre> tags doesn't wrap by default. For example, see the code snippet below! If this is causing layout problems, one solution is to give the pre block an overflow property to hide the excess or cause it to scroll. The other solution is to have it wrap.
```

***CSS***
```
/* Browser specific (not valid) styles to make preformatted text wrap */		

pre {
 white-space: pre-wrap;       /* css-3 */
 white-space: -moz-pre-wrap;  /* Mozilla, since 1999 */
 white-space: -pre-wrap;      /* Opera 4-6 */
 white-space: -o-pre-wrap;    /* Opera 7 */
 word-wrap: break-word;       /* Internet Explorer 5.5+ */
}
```

## Solarized Theme for CodeMirror and Prettify

```
Here's for Google Code Prettify
```

```
.prettyprint {
  color: #839496;
  background-color: #002b36;
}

.prettyprint .pln {
  color: inherit;
}

.prettyprint .str,
.prettyprint .lit,
.prettyprint .atv {
  color: #2aa198;
}

.prettyprint .kwd {
  color: #268bd2;
}

.prettyprint .com,
.prettyprint .dec {
  color: #586e75;
  font-style: italic;
}

.prettyprint .typ {
  color: #b58900;
}

.prettyprint .pun {
  color: inherit;
}

.prettyprint .opn {
  color: inherit;
}

.prettyprint .clo {
  color: inherit;
}

.prettyprint .tag {
  color: #268bd2;
  font-weight: bold;
}

.prettyprint .atn {
  color: inherit;
}
```

```
here's for CodeMirror.
```

***CSS***

```
html * {
  color-profile: sRGB;
  rendering-intent: auto;
}
.cm-s-solarized-light {
  background-color: #fdf6e3;
  color: #657b83;
}
.cm-s-solarized-light .emphasis {
  font-weight: bold;
}
.cm-s-solarized-light .dotted {
  border-bottom: 1px dotted #cb4b16;
}
.cm-s-solarized-light .CodeMirror-gutter {
  background-color: #eee8d5;
  border-right: 3px solid #eee8d5;
}
.cm-s-solarized-light .CodeMirror-gutter .CodeMirror-gutter-text {
  color: #93a1a1;
}
.cm-s-solarized-light .CodeMirror-cursor {
  border-left-color: #002b36 !important;
}
.cm-s-solarized-light .CodeMirror-matchingbracket {
  color: #002b36;
  background-color: #eee8d5;
  box-shadow: 0 0 10px #eee8d5;
  font-weight: bold;
}
.cm-s-solarized-light .CodeMirror-nonmatchingbracket {
  color: #002b36;
  background-color: #eee8d5;
  box-shadow: 0 0 10px #eee8d5;
  font-weight: bold;
  color: #dc322f;
  border-bottom: 1px dotted #cb4b16;
}
.cm-s-solarized-light span.cm-keyword {
  color: #657b83;
  font-weight: bold;
}
.cm-s-solarized-light span.cm-atom {
  color: #2aa198;
}
.cm-s-solarized-light span.cm-number {
  color: #586e75;
}
.cm-s-solarized-light span.cm-def {
  color: #268bd2;
}
.cm-s-solarized-light span.cm-variable {
  color: #cb4b16;
}
.cm-s-solarized-light span.cm-variable-2 {
  color: #cb4b16;
}
.cm-s-solarized-light span.cm-variable-3 {
  color: #cb4b16;
}
.cm-s-solarized-light span.cm-comment {
  color: #93a1a1;
}
.cm-s-solarized-light span.cm-property {
  color: #b58900;
}
.cm-s-solarized-light span.cm-operator {
  color: #657b83;
}
.cm-s-solarized-light span.cm-string {
  color: #6c71c4;
}
.cm-s-solarized-light span.cm-error {
  font-weight: bold;
  border-bottom: 1px dotted #cb4b16;
}
.cm-s-solarized-light span.cm-bracket {
  color: #cb4b16;
}
.cm-s-solarized-light span.cm-tag {
  color: #657b83;
}
.cm-s-solarized-light span.cm-attribute {
  color: #586e75;
  font-weight: bold;
}
.cm-s-solarized-light span.cm-meta {
  color: #268bd2;
}
.cm-s-solarized-dark {
  background-color: #002b36;
  color: #839496;
}
.cm-s-solarized-dark .emphasis {
  font-weight: bold;
}
.cm-s-solarized-dark .dotted {
  border-bottom: 1px dotted #cb4b16;
}
.cm-s-solarized-dark .CodeMirror-gutter {
  background-color: #073642;
  border-right: 3px solid #073642;
}
.cm-s-solarized-dark .CodeMirror-gutter .CodeMirror-gutter-text {
  color: #586e75;
}
.cm-s-solarized-dark .CodeMirror-cursor {
  border-left-color: #fdf6e3 !important;
}
.cm-s-solarized-dark .CodeMirror-matchingbracket {
  color: #fdf6e3;
  background-color: #073642;
  box-shadow: 0 0 10px #073642;
  font-weight: bold;
}
.cm-s-solarized-dark .CodeMirror-nonmatchingbracket {
  color: #fdf6e3;
  background-color: #073642;
  box-shadow: 0 0 10px #073642;
  font-weight: bold;
  color: #dc322f;
  border-bottom: 1px dotted #cb4b16;
}
.cm-s-solarized-dark span.cm-keyword {
  color: #839496;
  font-weight: bold;
}
.cm-s-solarized-dark span.cm-atom {
  color: #2aa198;
}
.cm-s-solarized-dark span.cm-number {
  color: #93a1a1;
}
.cm-s-solarized-dark span.cm-def {
  color: #268bd2;
}
.cm-s-solarized-dark span.cm-variable {
  color: #cb4b16;
}
.cm-s-solarized-dark span.cm-variable-2 {
  color: #cb4b16;
}
.cm-s-solarized-dark span.cm-variable-3 {
  color: #cb4b16;
}
.cm-s-solarized-dark span.cm-comment {
  color: #586e75;
}
.cm-s-solarized-dark span.cm-property {
  color: #b58900;
}
.cm-s-solarized-dark span.cm-operator {
  color: #839496;
}
.cm-s-solarized-dark span.cm-string {
  color: #6c71c4;
}
.cm-s-solarized-dark span.cm-error {
  font-weight: bold;
  border-bottom: 1px dotted #cb4b16;
}
.cm-s-solarized-dark span.cm-bracket {
  color: #cb4b16;
}
.cm-s-solarized-dark span.cm-tag {
  color: #839496;
}
.cm-s-solarized-dark span.cm-attribute {
  color: #93a1a1;
  font-weight: bold;
}
.cm-s-solarized-dark span.cm-meta {
  color: #268bd2;
}
```

## Forcing Grayscale Printing
```
At the time of this writing, this will only work in Chrome 18+, but it's standardized so support will eventually come to everywhere.
```

***CSS***
```
@media print {
  body {
    /* IE4-8 and 9 (deprecated). */
    filter: Gray();
    /* SVG version for IE10, Chrome 17, FF3.5, 
       Safari 5.2 and Opera 11.6 */
    filter: url('#grayscale'); 
    /* CSS3 filter, at the moment Webkit only. Prefix it for
       future implementations */
    -webkit-filter: grayscale(100%); 
    filter: grayscale(100%); /* future-proof */
  }
}
```


## Page Curl Shadows

***CSS***
```
ul.box {
position: relative;
z-index: 1; /* prevent shadows falling behind containers with backgrounds */
overflow: hidden;
list-style: none;
margin: 0;
padding: 0; }

ul.box li {
position: relative;
float: left;
width: 250px;
height: 150px;
padding: 0;
border: 1px solid #efefef;
margin: 0 30px 30px 0;
background: #fff;
-webkit-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.27), 0 0 40px rgba(0, 0, 0, 0.06) inset;
-moz-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.27), 0 0 40px rgba(0, 0, 0, 0.06) inset; 
box-shadow: 0 1px 4px rgba(0, 0, 0, 0.27), 0 0 40px rgba(0, 0, 0, 0.06) inset; }

ul.box li:before,
ul.box li:after {
content: '';
z-index: -1;
position: absolute;
left: 10px;
bottom: 10px;
width: 70%;
max-width: 300px; /* avoid rotation causing ugly appearance at large container widths */
max-height: 100px;
height: 55%;
-webkit-box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
-moz-box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
-webkit-transform: skew(-15deg) rotate(-6deg);
-moz-transform: skew(-15deg) rotate(-6deg);
-ms-transform: skew(-15deg) rotate(-6deg);
-o-transform: skew(-15deg) rotate(-6deg);
transform: skew(-15deg) rotate(-6deg); }

ul.box li:after {
left: auto;
right: 10px;
-webkit-transform: skew(15deg) rotate(6deg);
-moz-transform: skew(15deg) rotate(6deg);
-ms-transform: skew(15deg) rotate(6deg);
-o-transform: skew(15deg) rotate(6deg);
transform: skew(15deg) rotate(6deg); }
```

>Be careful that these boxes aren't sitting within another element that has a background, otherwise the negative z-index values (required for this to work) will force the shadows underneath that and not show up.



## Font Stacks

***CSS***
```
/* Times New Roman-based stack */
font-family: Cambria, "Hoefler Text", Utopia, "Liberation Serif", "Nimbus Roman No9 L Regular", Times, "Times New Roman", serif;

/* Modern Georgia-based serif stack */
font-family: Constantia, "Lucida Bright", Lucidabright, "Lucida Serif", Lucida, "DejaVu Serif", "Bitstream Vera Serif", "Liberation Serif", Georgia, serif;

/* Traditional Garamond-based serif stack */
font-family: "Palatino Linotype", Palatino, Palladio, "URW Palladio L", "Book Antiqua", Baskerville, "Bookman Old Style", "Bitstream Charter", "Nimbus Roman No9 L", Garamond, "Apple Garamond", "ITC Garamond Narrow", "New Century Schoolbook", "Century Schoolbook", "Century Schoolbook L", Georgia, serif;

/* Helvetica/Arial-based sans serif stack */
font-family: Frutiger, "Frutiger Linotype", Univers, Calibri, "Gill Sans", "Gill Sans MT", "Myriad Pro", Myriad, "DejaVu Sans Condensed", "Liberation Sans", "Nimbus Sans L", Tahoma, Geneva, "Helvetica Neue", Helvetica, Arial, sans-serif;

/* Verdana-based sans serif stack */
font-family: Corbel, "Lucida Grande", "Lucida Sans Unicode", "Lucida Sans", "DejaVu Sans", "Bitstream Vera Sans", "Liberation Sans", Verdana, "Verdana Ref", sans-serif;

/* Trebuchet-based sans serif stack */
font-family: "Segoe UI", Candara, "Bitstream Vera Sans", "DejaVu Sans", "Bitstream Vera Sans", "Trebuchet MS", Verdana, "Verdana Ref", sans-serif;

/* Impact-based sans serif stack */
font-family: Impact, Haettenschweiler, "Franklin Gothic Bold", Charcoal, "Helvetica Inserat", "Bitstream Vera Sans Bold", "Arial Black", sans-serif;

/* Monospace stack */
font-family: Consolas, "Andale Mono WT", "Andale Mono", "Lucida Console", "Lucida Sans Typewriter", "DejaVu Sans Mono", "Bitstream Vera Sans Mono", "Liberation Mono", "Nimbus Mono L", Monaco, "Courier New", Courier, monospace;

```

## Layered Paper

***HTML***
```
<div class="layered-paper">
    Howdy
</div>
```

***CSS***
```
.layered-paper {
    background: #eee;
    box-shadow:
        0 1px 1px rgba(0,0,0,0.15), /* The top layer shadow */
        0 10px 0 -5px #eee, /* The second layer */
        0 10px 1px -4px rgba(0,0,0,0.15), /* The second layer shadow */
        0 20px 0 -10px #eee, /* The third layer */
        0 20px 1px -9px rgba(0,0,0,0.15); /* The third layer shadow */
}
```

## Named Colors and Hex Equivalents
>https://css-tricks.com/snippets/css/named-colors-and-hex-equivalents/


## Common Unicode Icons

***HTML***
```
<p>
  <a href="mailto:chriscoyier@gmail.com">
    chriscoyier@gmail.com
  </a>
</p>

<p class="phone">
    555-555-5555
</p>

<p class="important">
  REMEMBER: drink slushies too fast.
</p>

<blockquote>
   Designers tend to whisper, ad agencies tend to shout.
</blockquote>

<p class="alert">
   Stranger Danger!
<p>
```

***CSS***
```
a[href^="mailto:"]:before { content: "\2709"; }
.phone:before             { content: "\2706"; }
.important:before         { content: "\27BD"; }
blockquote:before         { content: "\275D"; }
blockquote:after          { content: "\275E"; }
.alert:before             { content: "\26A0"; }
```

## Reversing Text

```
For right-to-left languages, you can swap the default left-to-right layout in most browsers simply through the dir attribute.
```

***HTML***
```
<body dir="rtl">
  text in right-to-left language
</body>
```
>You can use that attribute on any text element, it doesn't have to be the body. Likewise, you can swap it with just CSS:

***CSS***
```
body {
  unicode-bidi:bidi-override;
  direction:rtl;
}

 - The following are "less practical" but still interesting:

 /* Flip each letter backwards */

div {
  -webkit-transform:rotateY(180deg);
  -moz-transform:rotateY(180deg);
  -o-transform:rotateY(180deg);
  -ms-transform:rotateY(180deg);
  unicode-bidi:bidi-override;
  direction:rtl;
}

/* Entire text flipped around */
div {
  -webkit-transform:rotateY(180deg);
  -moz-transform:rotateY(180deg);
  -o-transform:rotateY(180deg);
  -ms-transform:rotateY(180deg);
}

```

## CSS Box Shadow

```
Used in casting shadows off block-level elements (like divs).

```

***CSS***
```
.shadow {
  -moz-box-shadow:    3px 3px 5px 6px #ccc;
  -webkit-box-shadow: 3px 3px 5px 6px #ccc;
  box-shadow:         3px 3px 5px 6px #ccc;
}
```
- The horizontal offset of the shadow, positive means the shadow will be on the right of the box, a negative offset will put the shadow on the left of the box.
- The vertical offset of the shadow, a negative one means the box-shadow will be above the box, a positive one means the shadow will be below the box.
- The blur radius (optional), if set to 0 the shadow will be sharp, the higher the number, the more blurred it will be.
- The spread radius (optional), positive values increase the size of the shadow, negative values decrease the size. Default is 0 (the shadow is same size as blur).
- Color


#### Inner Shadow

***CSS***
```
.shadow {
   -moz-box-shadow:    inset 0 0 10px #000000;
   -webkit-box-shadow: inset 0 0 10px #000000;
   box-shadow:         inset 0 0 10px #000000;
}
```

#### Internet Explorer Box Shadow

***HTML***
```
<div class="shadow1">
	<div class="content">
		Box-shadowed element
	</div>
</div>
```

***CSS***
```
.shadow1 {
	margin: 40px;
	background-color: rgb(68,68,68); /* Needed for IEs */

	-moz-box-shadow: 5px 5px 5px rgba(68,68,68,0.6);
	-webkit-box-shadow: 5px 5px 5px rgba(68,68,68,0.6);
	box-shadow: 5px 5px 5px rgba(68,68,68,0.6);

	filter: progid:DXImageTransform.Microsoft.Blur(PixelRadius=3,MakeShadow=true,ShadowOpacity=0.30);
	-ms-filter: "progid:DXImageTransform.Microsoft.Blur(PixelRadius=3,MakeShadow=true,ShadowOpacity=0.30)";
	zoom: 1;
}
.shadow1 .content {
	position: relative; /* This protects the inner element from being blurred */
	padding: 100px;
	background-color: #DDD;
}
```

#### One-Side Only

>Using a negative spread radius, you can get squeeze in a box shadow and only push it off one edge of a box.

***CSS***
```
.one-edge-shadow {
	-webkit-box-shadow: 0 8px 6px -6px black;
	   -moz-box-shadow: 0 8px 6px -6px black;
	        box-shadow: 0 8px 6px -6px black;
}
```

>https://css-tricks.com/snippets/css/css-box-shadow/



## Useful CSS3 LESS Mixins

***LESS***
```
.text-shadow (@string: 0 1px 3px rgba(0, 0, 0, 0.25)) {
	text-shadow: @string;
}
.box-shadow (@string) {
	-webkit-box-shadow: @string;
	-moz-box-shadow:    @string;
	box-shadow:         @string;
}
.drop-shadow (@x: 0, @y: 1px, @blur: 2px, @spread: 0, @alpha: 0.25) {
	-webkit-box-shadow:	@x @y @blur @spread rgba(0, 0, 0, @alpha);
	-moz-box-shadow:	@x @y @blur @spread rgba(0, 0, 0, @alpha);
	box-shadow:		@x @y @blur @spread rgba(0, 0, 0, @alpha);
}
.inner-shadow (@x: 0, @y: 1px, @blur: 2px, @spread: 0, @alpha: 0.25) {
	-webkit-box-shadow: inset @x @y @blur @spread rgba(0, 0, 0, @alpha);
	-moz-box-shadow:    inset @x @y @blur @spread rgba(0, 0, 0, @alpha);
	box-shadow:         inset @x @y @blur @spread rgba(0, 0, 0, @alpha);
}

.box-sizing (@type: border-box) {
	-webkit-box-sizing: @type;
	-moz-box-sizing:    @type;
	box-sizing:         @type;
}

.border-radius (@radius: 5px) {
	-webkit-border-radius: @radius;
	-moz-border-radius:    @radius;
	border-radius:         @radius;

	-moz-background-clip:    padding;
	-webkit-background-clip: padding-box;
	background-clip:         padding-box;
}
.border-radiuses (@topright: 0, @bottomright: 0, @bottomleft: 0, @topleft: 0) {
	-webkit-border-top-right-radius:    @topright;
	-webkit-border-bottom-right-radius: @bottomright;
	-webkit-border-bottom-left-radius:  @bottomleft;
	-webkit-border-top-left-radius:     @topleft;

	-moz-border-radius-topright:        @topright;
	-moz-border-radius-bottomright:     @bottomright;
	-moz-border-radius-bottomleft:      @bottomleft;
	-moz-border-radius-topleft:         @topleft;

	border-top-right-radius:            @topright;
	border-bottom-right-radius:         @bottomright;
	border-bottom-left-radius:          @bottomleft;
	border-top-left-radius:             @topleft;

	-moz-background-clip:    padding; 
	-webkit-background-clip: padding-box; 
	background-clip:         padding-box; 
}

.opacity (@opacity: 0.5) {
	-webkit-opacity: 	@opacity;
	-moz-opacity: 		@opacity;
	opacity: 		@opacity;
}

.gradient (@startColor: #eee, @endColor: white) {
	background-color: @startColor;
	background: -webkit-gradient(linear, left top, left bottom, from(@startColor), to(@endColor));
	background: -webkit-linear-gradient(top, @startColor, @endColor);
	background: -moz-linear-gradient(top, @startColor, @endColor);
	background: -ms-linear-gradient(top, @startColor, @endColor);
	background: -o-linear-gradient(top, @startColor, @endColor);
}
.horizontal-gradient (@startColor: #eee, @endColor: white) {
 	background-color: @startColor;
	background-image: -webkit-gradient(linear, left top, right top, from(@startColor), to(@endColor));
	background-image: -webkit-linear-gradient(left, @startColor, @endColor);
	background-image: -moz-linear-gradient(left, @startColor, @endColor);
	background-image: -ms-linear-gradient(left, @startColor, @endColor);
	background-image: -o-linear-gradient(left, @startColor, @endColor);
}

.animation (@name, @duration: 300ms, @delay: 0s, @ease: ease) {
	-webkit-animation: @name @duration @delay @ease;
	-moz-animation:    @name @duration @delay @ease;
	-ms-animation:     @name @duration @delay @ease;
}

.transition (@transition) {
	-webkit-transition: @transition;  
	-moz-transition:    @transition;
	-ms-transition:     @transition; 
	-o-transition:      @transition;  
}
.transform(@string){
	-webkit-transform: @string;
	-moz-transform: 	 @string;
	-ms-transform: 		 @string;
	-o-transform: 		 @string;
}
.scale (@factor) {
	-webkit-transform: scale(@factor);
	-moz-transform: 	 scale(@factor);
	-ms-transform: 		 scale(@factor);
	-o-transform: 		 scale(@factor);
}
.rotate (@deg) {
	-webkit-transform: rotate(@deg);
	-moz-transform: 	 rotate(@deg);
	-ms-transform: 		 rotate(@deg);
	-o-transform: 		 rotate(@deg);
}
.skew (@deg, @deg2) {
	-webkit-transform:       skew(@deg, @deg2);
	-moz-transform: 	 skew(@deg, @deg2);
	-ms-transform: 		 skew(@deg, @deg2);
	-o-transform: 		 skew(@deg, @deg2);
}
.translate (@x, @y:0) {
	-webkit-transform:       translate(@x, @y);
	-moz-transform: 	 translate(@x, @y);
	-ms-transform: 		 translate(@x, @y);
	-o-transform: 		 translate(@x, @y);
}
.translate3d (@x, @y: 0, @z: 0) {
	-webkit-transform:       translate3d(@x, @y, @z);
	-moz-transform: 	 translate3d(@x, @y, @z);
	-ms-transform: 		 translate3d(@x, @y, @z);
	-o-transform: 		 translate3d(@x, @y, @z);
}
.perspective (@value: 1000) {
	-webkit-perspective: 	@value;
	-moz-perspective: 	@value;
	-ms-perspective: 	@value;
	perspective: 		@value;
}
.transform-origin (@x:center, @y:center) {
	-webkit-transform-origin: @x @y;
	-moz-transform-origin:    @x @y;
	-ms-transform-origin:     @x @y;
	-o-transform-origin:      @x @y;
}
```

## Custom Checkboxes and Radio Buttons

```
The selectors here are specific to Wufoo markup, but the concepts at work can work for any form. The overall idea is that you make the default radio buttons and checkboxes invisible by setting their opacity to zero, and replace them with graphics. Then use the :checked selector to alternate the graphics between their checked and unchecked versions.
```

***CSS***
```
/* 
    Hide the original radios and checkboxes
    (but still accessible)
    
    :not(#foo) > is a rule filter to block browsers
                 that don't support that selector from
                 applying rules they shouldn't
       
*/
li:not(#foo) > fieldset > div > span > input[type='radio'], 
li:not(#foo) > fieldset > div > span > input[type='checkbox'] {
    
    /* Hide the input, but have it still be clickable */
    opacity: 0;
    
    float: left;
    width: 18px;
}


li:not(#foo) > fieldset > div > span > input[type='radio'] + label,
li:not(#foo) > fieldset > div > span > input[type='checkbox'] + label {
    margin: 0;
    clear: none;
    
    /* Left padding makes room for image */
    padding: 5px 0 4px 24px;

    /* Make look clickable because they are */
    cursor: pointer;
    
    background: url(off.png) left center no-repeat; 
}

/*
    Change from unchecked to checked graphic
*/
li:not(#foo) > fieldset > div > span > input[type='radio']:checked + label {
    background-image: url(radio.png);
}
li:not(#foo) > fieldset > div > span > input[type='checkbox']:checked + label {
    background-image: url(check.png);
}
```


## Smiley Slider

```
Requires jQuery and jQuery UI for the actual slider. The face is made from elements made into circles with border-radius. The mouth, indicating happiness level, is another circle just cropped down to size with a parent element with hidden overflow.
```

***HTML***
```
<div id="slider"></div>

<div id="face">
	<div id="mouth-box">
		<div id="mouth" class="straight"></div>
	</div>
</div>
```

***CSS***
```
#face { 
  width: 100px; 
  height: 100px; 
  position: relative;
  border: 2px solid black;
  border-radius: 50px; 
  margin: 20px auto; 
}

#face:before, #face:after {
  position: absolute;
  content: "";
  width: 10px;
  height: 10px;
  top: 30px;
  border-radius: 10px;
  background: black; 
}
#face:before {
  left: 30px; 
}
#face:after {
  left: 60px; 
}

#mouth-box {
  width: 60px; 
  height: 20px; 
  left: 20px; 
  top: 60px; 
  overflow: hidden; 
  background: white; 
  position: relative; 
}

#mouth { 
  width: 60px; 
  height: 60px; 
  border-radius: 30px; 
  border: 2px solid black; 
  position: absolute; 
  top: 0; 
  left: 0; 
}

#mouth.straight {
  height: 0px !important;
  top: 7px !important;
  border-width: 1px;
  bottom: auto !important;
}
```

***JQuery***
```
var newWidth,
    mouth = $("#mouth");

$( "#slider" ).slider({
   slide: function(event, ui) {
     
     if (ui.value > 51 ) {
       
       mouth.css({ bottom: 0, top: "auto" });
       
       newWidth = 160 - ui.value;
       
       mouth.css({
         width           : newWidth,
         height          : newWidth,
         "border-radius" : newWidth / 2,
         left            : -25 + ((ui.value-50) / 2)
       })
       .removeClass("straight");
       
     } else if ((ui.value > 48) && (ui.value < 52)) {
       
       mouth.addClass("straight");
       
     }  else {
       
       mouth.css({ top: 0, bottom: "auto" });
       
       newWidth = ui.value + 60;
       
       mouth.css({
         width           : newWidth,
         height          : newWidth,
         "border-radius" : newWidth / 2,
         left            : -ui.value / 2
       })
       .removeClass("straight");
       
     }
     
   },
  value: 50
});
```


## Transparent Inside Border
***HTML***
```
<div class="inner-border">
    Transparent Inside Border
</div>
```

***CSS***
```
.inner-border {
    background: #000;
    color: #fff;
    margin: 50px;
    padding: 15px;
    position: relative;
}
.inner-border:before {
    border: 5px solid #000;
    content: "";
    position: absolute;
    top: -10px;
    bottom: -10px;
    left: -10px;
    right: -10px;
}
```

## Text Rotation

***CSS***
```
.rotate {

/* Safari */
-webkit-transform: rotate(-90deg);

/* Firefox */
-moz-transform: rotate(-90deg);

/* IE */
-ms-transform: rotate(-90deg);

/* Opera */
-o-transform: rotate(-90deg);

/* Internet Explorer */
filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=3);

}

```

```
The example above rotates text 90 degrees counterclockwise.

The rotation property of Internet Explorer’s BasicImage filter can accept one of four values: 0, 1, 2, or 3 which will rotate the element 0, 90, 180 or 270 degrees respectively.

Also see this blog post about sideways headers.

```
>For More Detail
https://css-tricks.com/snippets/css/text-rotation/



## Remove Gray Highlight When Tapping Links in Mobile Safari

***CSS***
```
-webkit-tap-highlight-color: rgba(0,0,0,0);
```
>And then to allow :active styles to work in your CSS on a page in Mobile Safari:

***JS***
```
document.addEventListener("touchstart", function(){}, true);
```


## Force File Upload Input Button To Right Side In WebKit
```
Firefox and IE have the "choose file" button to the right of the filepath, while Webkit puts it on the left. This makes WebKit put it on the right as well.
```

***HTML***
```
<input type="file">
```

***CSS***
```
input[type="file"]{
   -webkit-appearance: none;
   text-align: left;
   -webkit-rtl-ordering:  left;
}
input[type="file"]::-webkit-file-upload-button{
   -webkit-appearance: none;
   float: right;
   margin: 0 0 0 10px;
   border: 1px solid #aaaaaa;
   border-radius: 4px;
   background-image: -webkit-gradient(linear, left bottom, left top, from(#d2d0d0), to(#f0f0f0));
   background-image: -moz-linear-gradient(90deg, #d2d0d0 0%, #f0f0f0 100%);
}
```


## Noise Data URI Image

***CSS***
```
background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAMAAAAp4XiDAAAAUVBMVEWFhYWDg4N3d3dtbW17e3t1dXWBgYGHh4d5eXlzc3OLi4ubm5uVlZWPj4+NjY19fX2JiYl/f39ra2uRkZGZmZlpaWmXl5dvb29xcXGTk5NnZ2c8TV1mAAAAG3RSTlNAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEAvEOwtAAAFVklEQVR4XpWWB67c2BUFb3g557T/hRo9/WUMZHlgr4Bg8Z4qQgQJlHI4A8SzFVrapvmTF9O7dmYRFZ60YiBhJRCgh1FYhiLAmdvX0CzTOpNE77ME0Zty/nWWzchDtiqrmQDeuv3powQ5ta2eN0FY0InkqDD73lT9c9lEzwUNqgFHs9VQce3TVClFCQrSTfOiYkVJQBmpbq2L6iZavPnAPcoU0dSw0SUTqz/GtrGuXfbyyBniKykOWQWGqwwMA7QiYAxi+IlPdqo+hYHnUt5ZPfnsHJyNiDtnpJyayNBkF6cWoYGAMY92U2hXHF/C1M8uP/ZtYdiuj26UdAdQQSXQErwSOMzt/XWRWAz5GuSBIkwG1H3FabJ2OsUOUhGC6tK4EMtJO0ttC6IBD3kM0ve0tJwMdSfjZo+EEISaeTr9P3wYrGjXqyC1krcKdhMpxEnt5JetoulscpyzhXN5FRpuPHvbeQaKxFAEB6EN+cYN6xD7RYGpXpNndMmZgM5Dcs3YSNFDHUo2LGfZuukSWyUYirJAdYbF3MfqEKmjM+I2EfhA94iG3L7uKrR+GdWD73ydlIB+6hgref1QTlmgmbM3/LeX5GI1Ux1RWpgxpLuZ2+I+IjzZ8wqE4nilvQdkUdfhzI5QDWy+kw5Wgg2pGpeEVeCCA7b85BO3F9DzxB3cdqvBzWcmzbyMiqhzuYqtHRVG2y4x+KOlnyqla8AoW
 WpuBoYRxzXrfKuILl6SfiWCbjxoZJUaCBj1CjH7GIaDbc9kqBY3W/Rgjda1iqQcOJu2WW+76pZC9QG7M00dffe9hNnseupFL53r8F7YHSwJWUKP2q+k7RdsxyOB11n0xtOvnW4irMMFNV4H0uqwS5ExsmP9AxbDTc9JwgneAT5vTiUSm1E7BSflSt3bfa1tv8Di3R8n3Af7MNWzs49hmauE2wP+ttrq+AsWpFG2awvsuOqbipWHgtuvuaAE+A1Z/7gC9hesnr+7wqCwG8c5yAg3AL1fm8T9AZtp/bbJGwl1pNrE7RuOX7PeMRUERVaPpEs+yqeoSmuOlokqw49pgomjLeh7icHNlG19yjs6XXOMedYm5xH2YxpV2tc0Ro2jJfxC50ApuxGob7lMsxfTbeUv07TyYxpeLucEH1gNd4IKH2LAg5TdVhlCafZvpskfncCfx8pOhJzd76bJWeYFnFciwcYfubRc12Ip/ppIhA1/mSZ/RxjFDrJC5xifFjJpY2Xl5zXdguFqYyTR1zSp1Y9p+tktDYYSNflcxI0iyO4TPBdlRcpeqjK/piF5bklq77VSEaA+z8qmJTFzIWiitbnzR794USKBUaT0NTEsVjZqLaFVqJoPN9ODG70IPbfBHKK+/q/AWR0tJzYHRULOa4MP+W/HfGadZUbfw177G7j/OGbIs8TahLyynl4X4RinF793Oz+BU0saXtUHrVBFT/DnA3ctNPoGbs4hRIjTok8i+algT1lTHi4SxFvONKNrgQFAq2/gFnWMXgwffgYMJpiKYkmW3tTg3ZQ9Jq+f8XN+A5eeUKHWvJWJ2sgJ1Sop+wwhqFVijqWaJhwtD8MNlSBeWNNWTa5Z5kPZw5+LbVT99wqTdx29lMUH4OIG/D86ruKEauBjvH5xy6um/Sfj7ei6UUVk4AIl3MyD4MSSTOFgSwsH/QJWaQ5as7ZcmgBZkzjjU1UrQ74ci1gWBCSGHtuV1H2mhS
 nO3Wp/3fEV5a+4wz//6qy8JxjZsmxxy5+4w9CDNJY09T072iKG0EnOS0arEYgXqYnXcYHwjTtUNAcMelOd4xpkoqiTYICWFq0JSiPfPDQdnt+4/wuqcXY47QILbgAAAABJRU5ErkJggg==);

```

## Bouncy Animated Loading Animation

***HTML***
```
<div class="loader">
    <span></span>
    <span></span>
    <span></span>
</div>
```


***CSS***
```
.loader {
    text-align: center;    
}
.loader span {
    display: inline-block;
    vertical-align: middle;
    width: 10px;
    height: 10px;
    margin: 50px auto;
    background: black;
    border-radius: 50px;
    -webkit-animation: loader 0.9s infinite alternate;
    -moz-animation: loader 0.9s infinite alternate;
}
.loader span:nth-of-type(2) {
    -webkit-animation-delay: 0.3s;
    -moz-animation-delay: 0.3s;
}
.loader span:nth-of-type(3) {
    -webkit-animation-delay: 0.6s;
    -moz-animation-delay: 0.6s;
}
@-webkit-keyframes loader {
  0% {
    width: 10px;
    height: 10px;
    opacity: 0.9;
    -webkit-transform: translateY(0);
  }
  100% {
    width: 24px;
    height: 24px;
    opacity: 0.1;
    -webkit-transform: translateY(-21px);
  }
}
@-moz-keyframes loader {
  0% {
    width: 10px;
    height: 10px;
    opacity: 0.9;
    -moz-transform: translateY(0);
  }
  100% {
    width: 24px;
    height: 24px;
    opacity: 0.1;
    -moz-transform: translateY(-21px);
  }
}
```

>For More Detail
https://css-tricks.com/snippets/css/bouncy-animated-loading-animation/



## Make Non-Password Inputs Use Bullets (or Bullet Alternatives)

```
This works on texty inputs (e.g. text, email, etc) but you cannot change actual password inputs. Use case = ???.

```

***CSS***
```
input { -webkit-text-security: none; }
input { -webkit-text-security: circle; }
input { -webkit-text-security: square; }
input { -webkit-text-security: disc; /* Default */ }
```


## Triangular List Bullets

***CSS***
```
ul {
    margin: 0.75em 0;
    padding: 0 1em;
    list-style: none;
}
li:before { 
    content: "";
    border-color: transparent #111;
    border-style: solid;
    border-width: 0.35em 0 0.35em 0.45em;
    display: block;
    height: 0;
    width: 0;
    left: -1em;
    top: 0.9em;
    position: relative;
}
```

## Slide In Image Boxes

***CSS***
```
footer {
    clear:both;
    overflow:hidden;
    font-size:16px;
    line-height:1.3;
}
#footer-boxes {
    -moz-column-count:2;
    -moz-column-gap:10px;
    -webkit-column-count:2;
    -webkit-column-gap:10px;
    column-count:4;
    column-gap:10px;
}
.footer-box {
    margin:0 0 10px 0;
    display:inline-block;
    width:262px;
    height:140px;
    padding:15px;
    background:#e6e2df;
    color:#b2aaa4;
    -webkit-transition:all 0.2s ease;
    -moz-transition:all 0.2s ease;
    background-position:320px 50%;
    background-repeat:no-repeat;
    text-decoration: none;
}
.footer-box h5 {
    font: bold 24px Sans-Serif !important;
    text-transform:uppercase;
    font-size:38px;
    line-height:1;
    padding:0 0 10px 0;
}
.footer-box:hover h5 {
    text-shadow:0 0 4px rgba(0,0,0,0.4);
    color:white;
}
.footer-box:hover p {
    color:white;
}
.footer-box p {
    font-size:12px;
    width:175px;
    line-height:1.5;
}
.footer-box:hover {
    background-position:200px 50%;
}
#f-diw {
    background-image:url(http://cdn.css-tricks.com/wp-content/themes/CSS-Tricks-8/images/css-tricks.png);
    background-position:290px -1288px;
}
#f-diw:hover {
    background-color:#237abe;
    background-position:186px -1288px;
}
#f-qod {
    background-image:url(http://cdn.css-tricks.com/wp-content/themes/CSS-Tricks-8/images/css-tricks.png);
    background-position:290px -1448px;
}
#f-qod:hover {
    background-color:#37597a;
    background-position:186px -1448px;
}
#f-htmlipsum {
    background-image:url(http://cdn.css-tricks.com/wp-content/themes/CSS-Tricks-8/images/css-tricks.png);
    background-position:290px -1608px;
}
#f-htmlipsum:hover {
    background-color:#333333;
    background-position:186px -1608px;
}
#f-qod:hover p {
    color:#adbde3;
}
#f-bookshelf {
    background-image:url(http://cdn.css-tricks.com/wp-content/themes/CSS-Tricks-8/images/css-tricks.png);
    background-position:290px -1768px;
}
#f-bookshelf:hover {
    background-color:#ff8400;
    background-position:186px -1768px;
}
#f-html-ipsum:hover p {
    color:#fff8da;
}
#f-twitter {
    background-image:url(http://css-tricks.com/images/css-tricks.png);
    background-position:290px -1928px;
}
#f-twitter:hover {
    background-color:#4ed2fe;
    background-position:186px -1928px;
}
#f-forrst {
    background-image:url(http://css-tricks.com/images/css-tricks.png);
    background-position:290px -2088px;
}
#f-forrst:hover {
    background-color:#203f16;
    background-position:186px -2088px;
}
#f-forrst:hover p {
    color: #92c59c;
}

```

>For More Detail
https://css-tricks.com/snippets/css/slide-in-image-boxes/



## Expanding Boxes Navigation

***CSS***
```
nav {
    background: #444;
    border-bottom: 8px solid #E6E2DF;
    overflow: hidden;
    position: relative;
    width: 100%;
}
nav:after {
    content: "";
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
    height: 2px;
    background: white; 
}
nav ul {
    background: -moz-linear-gradient(left,
                #444 0%,
                #444 50%,
                #41d05f 100%);
    background: -webkit-gradient(linear, left top, right top,
                color-stop(0%,#444),
                color-stop(50%,#444),
                color-stop(50%,#41d05f),
                color-stop(100%,#41d05f));
    list-style: none;
    overflow: hidden;
    padding: 0 0 0 20px;
    width: 810px;
}
nav li {
    display: inline;
}
nav a {
    color: white;
    display: block;
    float: left;
    font-family: "myriad-pro-1","myriad-pro-2", HelveticaNeue, Helvetica, Arial, Sans-Serif;
    font-size: 22px;
    padding: 12px 0;
    text-decoration: none;
    text-align: center;
    width: 19%;
    -webkit-transition: width 0.12s ease;
       -moz-transition: width 0.12s ease;
         -o-transition: width 0.12s ease;
            transition: width 0.12s ease;
}
nav a:hover {
    color: white;
}
nav a:hover span {
    border-bottom: 2px solid white;
}
nav .a-home {
    background: #ff8400;
    z-index: 100;
    position: relative;
}    
nav .a-forums {
    background: #e42b2b;
}    
nav .a-videos {
    background: #a800ff;
}    
nav .a-downloads {
    background: #49a7f3;
}   
nav .a-snippets {
    background: #41d05f;
}
.home nav {
    border-bottom-color: #ff8400;
}
.forums nav {
    border-bottom-color: #e42b2b;
}
.videos nav {
    border-bottom-color: #a800ff;
}
.downloads nav {
    border-bottom-color: #49a7f3;
}
.snippets nav {
    border-bottom-color: #41d05f;
}
nav li:hover a {
    width: 24%;
}
nav ul:hover .active {
    width: 19%;
}
nav ul:hover .active:hover {
    width: 24%;
}
nav li a.active {
    width: 24%;
}
```

>For More Details
https://css-tricks.com/snippets/css/expanding-boxes-navigation/

## Prevent Bounce Scroll in Lion

```
Just make sure you zero out the margin and padding on those elements as well (normal in any reset or normalization).
```
***CSS***
```
html, body {
  height: 100%;
  overflow: hidden;
}
```


## Diagonal Graph Paper Gradient

***CSS***
```
#example-gradient {
  height: 200px;
  margin: 0 0 20px 0;
  background-color: #eaeaea;
  background-size: 20px 20px;
  background-image:
     -webkit-repeating-linear-gradient(45deg, rgba(0, 191, 255, .5), rgba(0, 191, 255, .5) 1px, transparent 1px, transparent 15px),
     -webkit-repeating-linear-gradient(-45deg, rgba(255, 105, 180, .5), rgba(255, 105, 180, .5) 1px, transparent 1px, transparent 15px);
  background-image:
     -moz-repeating-linear-gradient(45deg, rgba(0, 191, 255, .5), rgba(0, 191, 255, .5) 1px, transparent 1px, transparent 15px),
     -moz-repeating-linear-gradient(-45deg, rgba(255, 105, 180, .5), rgba(255, 105, 180, .5) 1px, transparent 1px, transparent 15px);
  background-image:
     -o-repeating-linear-gradient(45deg, rgba(0, 191, 255, .5), rgba(0, 191, 255, .5) 1px, transparent 1px, transparent 15px),
     -o-repeating-linear-gradient(-45deg, rgba(255, 105, 180, .5), rgba(255, 105, 180, .5) 1px, transparent 1px, transparent 15px);
  background-image:
     repeating-linear-gradient(45deg, rgba(0, 191, 255, .5), rgba(0, 191, 255, .5) 1px, transparent 1px, transparent 15px),
     repeating-linear-gradient(-45deg, rgba(255, 105, 180, .5), rgba(255, 105, 180, .5) 1px, transparent 1px, transparent 15px);
}
```

>For More Detail
https://css-tricks.com/snippets/css/diagonal-graph-paper-gradient/


## Spinny Leaf Menu

***HTML***
```
<nav>
  <ul class="top-menu">
    <li><a href=#>Home</a><div class="menu-item" id="home"></div></li>
    <li><a href=#>Catalog</a><div class="menu-item" id="cataloge"></div></li>
    <li><a href=#>Price</a><div class="menu-item" id="price"></div></li>
    <li><a href=#>About</a><div class="menu-item" id="about"></div></li>
    <li><a href=#>Contact</a><div class="menu-item" id="contact"></div></li>
  </ul>
</nav>

```

***CSS***
```
nav {
	width: 960px;
	height: 100px;
	margin: 120px auto;
	text-align: center;
}
.top-menu li {
	display: inline-block;
	text-align: center;
	margin: 30px 5px;
	position: relative;
	-webkit-transition: all 0.3s ease; 
	-moz-transition: all 0.3s ease;
	-o-transition: all 0.3s ease;
}
.top-menu li:hover {
	margin: 30px 20px; 
}
.top-menu li:active {
	margin: 30px 33px; 
}
.top-menu li a  {
	width: 100px;
	height: 100px;
	z-index: 9999;
	position: absolute;
	top: 35px;
	font-weight: bold;
	display: block;
	text-decoration: none;
	font-size: 20px;
	color: #fff;
	text-shadow: 0px 1px 1px rgba(0,0,0,0.4), 0px 4px 6px rgba(0,0,0,0.1), 0px 9px 11px rgba(0,0,0,0.1);
	-webkit-transition: all 0.1s linear; 
	-moz-transition: all 0.1s linear;
	-o-transition: all 0.1s linear;
}
.top-menu li:active a {
	font-size: 26px;
	top: 30px;
	text-shadow: none;
}
.top-menu li div.menu-item {	
	width: 100px;
	height: 100px;
	display: block;
	-webkit-transition: all 0.2s ease; 
	-moz-transition: all 0.2s ease;
	-o-transition: all 0.2s ease;
	-webkit-border-top-left-radius: 100px; 
	-webkit-border-bottom-right-radius: 100px; 
	-moz-border-radius-topleft: 100px; 
	-moz-border-radius-bottomright: 100px; 
	border-top-left-radius: 100px; 
	border-bottom-right-radius: 100px;
	-webkit-transform: rotate(45deg);
	-moz-transform: rotate(45deg);
	-o-transform: rotate(45deg);
}
.top-menu li:hover div.menu-item{ 
	-webkit-border-top-left-radius: 80px; 
	-webkit-border-bottom-right-radius: 80px; 
	-moz-border-radius-topleft: 80px; 
	-moz-border-radius-bottomright: 80px; 
	border-top-left-radius: 80px; 
	border-bottom-right-radius: 80px; 
		-webkit-transform: rotate(225deg);
	-moz-transform: rotate(225deg);
	-o-transform: rotate(225deg);
}
.top-menu li:active div.menu-item{ 
	-webkit-border-top-left-radius: 50px; 
	-webkit-border-bottom-right-radius: 50px; 
	-moz-border-radius-topleft: 50px; 
	-moz-border-radius-bottomright: 50px; 
	border-top-left-radius: 50px; 
	border-bottom-right-radius: 50px; 

}
#home { background: #41D05F; }
#cataloge { background: #E42B2B; }
#price { background: #ff8400; }
#about { background: #a800ff; }
#contact { background: #49a7f3; }
```



## Non-Form Fieldset Look

***HTML***
```
<section class="fieldset">
 <h1>This is not a fieldset</h1>
 <p>Booyah!</p>
</section>
```

***CSS***
```
.fieldset {
  position: relative;
  border: 1px solid #ddd;
  padding: 10px;
}

.fieldset h1 {
  position: absolute;
  top: 0;
  font-size: 18px;
  line-height: 1;
  margin: -9px 0 0; /* half of font-size */
  background: #fff;
  padding: 0 3px;
}
```


## Blurry Text

```
Make the text color transparent but add a shadow:
```
***CSS***
```
.blur {
   color: transparent;
   text-shadow: 0 0 5px rgba(0,0,0,0.5);
}
```
```
More browsers support color than text-shadow though, so you might want to do feature detection. Or, leave the color property and do enough shadowing that it appears blurry anyway (demo).
```



## Custom Radio Buttons

***CSS***
```
#foo:checked::before,
input[type="checkbox"] {
    position:absolute;
    clip: rect(0,0,0,0);
    clip: rect(0 0 0 0);
}

#foo:checked,
input[type="checkbox"] + label::before {
    content: url('checkbox.png');
}

input[type="checkbox"]:checked + label::before {
    content: url('checkbox-checked.png');
}
```

```
#foo doesn't reference any particular element, it's there purely to prevent browsers from implementing the later selectors if it doesn't understand that (since most browsers will drop the entire selector if any part of it fails).
```


## Top Shadow

>Shadow along the top edge of the website, like this:

***CSS***
```
body:before {
          content: "";
          position: fixed;
          top: -10px;
          left: 0;
          width: 100%;
          height: 10px;

          -webkit-box-shadow: 0px 0px 10px rgba(0,0,0,.8);
              -moz-box-shadow: 0px 0px 10px rgba(0,0,0,.8);
                         box-shadow: 0px 0px 10px rgba(0,0,0,.8);

          z-index: 100;
}
```


## Multiple Columns

>Here is an example of a simple three-column class:

***HTML***
```
<p class="three-col">Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante. Donec eu libero sit amet quam egestas semper. Aenean ultricies mi vitae est. Mauris placerat eleifend leo. Quisque sit amet est et sapien ullamcorper pharetra. Vestibulum erat wisi, condimentum sed, commodo vitae, ornare sit amet, wisi. Aenean fermentum, elit eget tincidunt condimentum, eros ipsum rutrum orci, sagittis tempus lacus enim ac dui. Donec non enim in turpis pulvinar facilisis. Ut felis. Praesent dapibus, neque id cursus faucibus, tortor neque egestas augue, eu vulputate magna eros eu erat. Aliquam erat volutpat. Nam dui mi, tincidunt quis, accumsan porttitor, facilisis luctus, metus</p>
```

***CSS***
```
.three-col {
       -moz-column-count: 3;
       -moz-column-gap: 20px;
       -webkit-column-count: 3;
       -webkit-column-gap: 20px;
}
```

>Also note this demo and sample code is using moz and webkit vendor prefixes, should only work in Gecko (Firefox 1.5+, et al.) and Webkit (Safari 3+, Chrome, et al.) browsers. No native support in Internet Explorer or Opera yet that I know of.


#### All Related Properties

***CSS***
```
.three-col {
       -moz-column-count: 3;
       -moz-column-gap: 20px;
       -webkit-column-count: 3;
       -webkit-column-gap : 20px;
       -moz-column-rule-color:  #ccc;
       -moz-column-rule-style:  solid;
       -moz-column-rule-width:  1px;
       -webkit-column-rule-color:  #ccc;
       -webkit-column-rule-style: solid ;
       -webkit-column-rule-width:  1px;
}
```

```
You can also set the column-width (with prefixes) but it generally makes more sense to let it auto calculate that.

The rule ("rule", as in, a line) will split the gap down the middle. You can use the same values as you would a border.

Take care not to have your text blocks be so enormously tall that they are taller than a (fairly small) browser window, otherwise it's the same problem as text being wider than the browser window (scrolling back and forth to read = sucks). Also consider text-align: justify;
```

>For More Detail
https://alistapart.com/article/css3multicolumn



## CSS Diagnostics

***CSS***
```
/* Empty Elements */
div:empty, span:empty, li:empty, p:empty, td:empty, th:empty
{ padding: 20px; border: 5px dotted yellow !important; }

/* Empty Attributes */
*[alt=""], *[title=""], *[class=""], *[id=""], a[href=""], a[href="#"]
{ border: 5px solid yellow !important; }

/* Deprecated Elements */
applet, basefont, center, dir, font, isindex, menu, s, strike, u
{ border: 5px dotted red !important; }

/* Deprecated Attributes */
*[background], *[bgcolor], *[clear], *[color], *[compact], *[noshade], *[nowrap], *[size], *[start],
*[bottommargin], *[leftmargin], *[rightmargin], *[topmargin], *[marginheight], *[marginwidth], *[alink], *[link], *[text], *[vlink],
*[align], *[valign],
*[hspace], *[vspace],
*[height], *[width],
ul[type], ol[type], li[type]
{ border: 5px solid red !important; }

/* Proposed Deprecated Elements */
input[type="button"], big, tt
{ border: 5px dotted #33FF00 !important; }

/* Proposed Deprecated Attributes */
*[border], a[target], table[cellpadding], table[cellspacing], *[name]
{ border: 5px solid #33FF00 !important; }

```

#### Eric Meyer's version:

***CSS***
```
div:empty, span:empty,
li:empty, p:empty,
td:empty, th:empty {padding: 0.5em; background: yellow;}

*[style], font, center {outline: 5px solid red;}
*[class=""], *[id=""] {outline: 5px dotted red;}

img[alt=""] {border: 3px dotted red;}
img:not([alt]) {border: 5px solid red;}
img[title=""] {outline: 3px dotted fuchsia;}
img:not([title]) {outline: 5px solid fuchsia;}

table:not([summary]) {outline: 5px solid red;}
table[summary=""] {outline: 3px dotted red;}
th {border: 2px solid red;}
th[scope="col"], th[scope="row"] {border: none;}

a[href]:not([title]) {border: 5px solid red;}
a[title=""] {outline: 3px dotted red;}
a[href="#"] {background: lime;}
a[href=""] {background: fuchsia;}
```



## iPad-Specific CSS

***CSS***
```
@media only screen and (device-width: 768px) {
  /* For general iPad layouts */
}

@media only screen and (min-device-width: 481px) and (max-device-width: 1024px) and (orientation:portrait) {
  /* For portrait layouts only */
}

@media only screen and (min-device-width: 481px) and (max-device-width: 1024px) and (orientation:landscape) {
  /* For landscape layouts only */
}

```


## Multiple Backgrounds Syntax

```
Browsers that support multiple backgrounds (WebKit from the very early days, Firefox 3+) use a syntax like this:
```
***CSS***
```
#box {
  background: 
    url(icon.png) top left no-repeat, 
    url(texture.jpg), 
    url(top-edge.png) top left repeat-y;
}
```

```
They are comma separated values and there can be as many as you want with different URL's, positioning, and repeat values. You can even combine WebKit gradients into the mix:
```

***CSS***
```
#box {
	background: 
		url(../images/arrow.png) 15px center no-repeat,
		-webkit-gradient(linear,left top,left bottom,color-stop(0, #010101),color-stop(1, #181818));
}
```
```
Old school IE on the Mac would display the first background in the list, but other browsers that don't support it fail hard and just display no background. This makes it a hard case for progressive enhancement. That is, unless you use a tool like Modernizr to detect support for it and write a fallback selector which only declares one background for browsers that don't support it.
```



## Picross Style Buttons


#### CSS3 Technique

```
.btn {
  color: white;
  font-family: Helvetica, Arial, Sans-Serif;
  font-size: 20px;
  text-decoration: none;
  text-shadow: -1px -1px 1px #616161;
  position: relative;
  padding: 15px 30px;
  -webkit-box-shadow: 5px 5px 0 #666;
  -moz-box-shadow: 5px 5px 0 #666;
  -webkit-transition: all 0.3s ease;
  -moz-transition: all 0.3s ease;
  margin: 0 10px 0 0;
}

.btn:hover {
  -webkit-box-shadow: 0px 0px 0 #666;
  -moz-box-shadow: 0px 0px 0 #666;
  top: 5px;
  left: 5px;
}
```



#### jQuery Technique

>Smoother, but more markup and CSS needed.

***HTML***
```
<div class="rela">
  <a class="btn green btn1" href="index.html">Jack</a>
  <span class="shadow"></span>
</div>
```

***CSS***
```
.rela {
	display: block;
	width: 96px;
	height: 56px;
	position: relative;
	margin: 10px;
}
.btn {
	display: block;
	line-height: 56px;
	text-align: center;
	color: white;
	font-family: Helvetica, Arial, Sans-Serif;
	font-size: 20px;
	text-decoration:none;
	text-shadow: -1px -1px 1px #616161;
	position: relative;
}
.shadow {
	position: absolute;
	top:5px;
	left: 5px;
	background: #666;
	z-index: -1;
	width: 100%;
	height: 100%;
}
```

***JQuary***

```
$(".btn").hover(function(){
	$(this).stop().animate({ 
		top: "5",
		left: "5"
	}, 100 );
},
function(){
	$(this).stop().animate({ 
		top: 0,
		left: 0
	}, 100 );
});
```


## Style Links Depending on Destination


***CSS***

```
a[href^="http://"] {
        /* fully valid URL, likely external link */
}

a[href="http://google.com"] {
        /* link to specific website */
}

a[href^="/"], a[href^=".."] {
        /* internal relative link */
}

a[href^="mailto:"] {
        /* email link */
}

a[href$=".pdf"] {
        /* PDF file */
}

a[href$=".doc"] {
        /* Microsoft Word document */
}

a[href$=".mp3"] {
        /* Music file */
}

a[href$=".zip"] {
        /* Archive file */
}
```

## Flip an Image

```
You can flip images with CSS! Possible scenario: having only one graphic for an "arrow", but flipping it around to point in different directions.
```

***CSS***

```
img {
        -moz-transform: scaleX(-1);
        -o-transform: scaleX(-1);
        -webkit-transform: scaleX(-1);
        transform: scaleX(-1);
        filter: FlipH;
        -ms-filter: "FlipH";
}
```



## iPad Orientation CSS

***HTML***
```
<link rel="stylesheet" media="all and (orientation:portrait)" href="portrait.css">
<link rel="stylesheet" media="all and (orientation:landscape)" href="landscape.css"> 
```


## Text Dripping Blood

***HTML***
```
<h1 class="blood">Vampire!</h1>
```

***CSS***
```
.blood {
       color:silver;
       text-shadow:
       4px 4px 1px #300000,
       4px 6px 1px #400000,
       4px 8px 1px #500000,
       4px 10px 1px #600000,
       4px 12px 1px #700000,
       4px 14px 1px #800000,
       4px 16px 1px #900000,
       4px 18px 1px #A00000,
       4px 20px 1px #B00000,
       4px 22px 1px #C00000,
       4px 24px 1px #D00000,
       4px 26px 1px #E00000,
       4px 28px 1px #F00000,
       4px 30px 1px #FA0000,
       4px 32px 1px #FB0000,
       4px 34px 1px #FC0000,
       4px 36px 1px #FD0000,
       4px 38px 1px #FE0000,
       4px 40px 2px #FF0000;
}
```



## Remove Scrollbar from Textarea in IE

```
By default all versions of IE have a scrollbar on textareas, even when they are empty.


No other browsers do this, so if you want to remove it so IE can visually match other browsers, just:
```

***CSS***
```
textarea { overflow: auto; }
```

```
The scrollbar will return (rightfully) when the text in the textarea expands beyond it's bounds.
```



## Fancy Ampersand

```
Dan Cederholm has long used the Baskerville Italic ampersand, and tells us to Use The Best Ampersand Available (also here). For better or worse, this has gotten to be ridiculously popular. If you'd like to use this fancy ampersand:
```

***HTML***
```
Script <span class="amp">&amp;</span> Style
```

***CSS***

```
.amp {
font-family: Baskerville, 'Goudy Old Style', Palatino, 'Book Antiqua', serif;
font-style: italic;
font-weight: normal;
}
```



## Fixed Footer

***CSS***
```
#footer {
   position:fixed;
   left:0px;
   bottom:0px;
   height:30px;
   width:100%;
   background:#999;
}

/* IE 6 */
* html #footer {
   position:absolute;
   top:expression((0-(footer.offsetHeight)+(document.documentElement.clientHeight ? document.documentElement.clientHeight : document.body.clientHeight)+(ignoreMe = document.documentElement.scrollTop ? document.documentElement.scrollTop : document.body.scrollTop))+'px');
}
```



## Remove Margins for First/Last Elements

```
It can sometimes be desirable to remove the top or left margin from the first element in a container. Likewise, the right or bottom margin from the last element in a container. You can do this by manually applying classes to the HTML:
```

***CSS***

```
.first { margin-top: 0 !important; margin-left: 0 !important; }
.last { margin-bottom: 0 !important; margin-right: 0 !important; }
```

```
The "top"/"bottom" zeroing being useful with a vertical stack of elements, "left"/"right" zeroing being useful for horizontal rows (in general). But... this method is dependent on you adding classes to the HTML yourself. Pseudo-selectors can be a better less intrusive way to go:
```
```
* > :first-child { margin-top: 0 !important; margin-left: 0 !important; }
* > :last-child { margin-bottom: 0 !important; margin-right: 0 !important; }
```

```
You may want to replace the * with more specific selectors as per your needs.
```

#### "Every Third", etc.

```
Lets say you had a floated block of 9 elements, 3 by 3. It's very common that you might need to remove the right margin from the 3rd, 6th, and 9th items. The nth-child pseudo-selector might be able to help there:
```

***CSS***
```
* > :nth-child(3n+3) { margin-right: 0; }
```

```
The equation there, 3n+3, works like this:

(3x0)+3 = 3
(3x1)+3 = 6
(3x2)+3 = 9
etc.
```

#### jQuery

```
jQuery uses CSS3 selectors, which includes :first-child, :last-child, and :nth-child(). This means that in browsers with don't or don't fully support these selectors, they WILL work in jQuery, so you can substitute the CSS support with JavaScript support. For example:
```

>$("* > :nth-child(3n+3)").css("margin-right", 0);

#### Browser support

```
:first-child and :last-child works in the latest release from all major browsers, but not in IE 6. :first-child is supported in IE 7+. :nth-child works in Safari 3+, Firefox 3.5+, and Chrome 1+, but still doesn't work in IE8.
```


>For More Detail
https://css-tricks.com/snippets/css/remove-margins-first-element/



## CSS Only Image Preloading

```
One big reason to use image preloading is if you want to use an image for the background-image of an element on a mouseOver or :hover event. If you only apply that background-image in the CSS for the :hover state, that image will not load until the first :hover event and thus there will be a short annoying delay between the mouse going over that area and the image actually showing up.
```

 - Technique #1

 ```
 Load the image on the element's regular state, only shift it away with background position. Then move the background position to display it on hover.
```

***CSS***
```
#grass { background: url(images/grass.png) no-repeat -9999px -9999px; }
#grass:hover { background-position: bottom left; }
```

 - Technique #2

 ```
 If the element in question already has a background-image applied and you need to change that image, the above won't work. Typically you would go for a sprite here (a combined background image) and just shift the background position. But if that isn't possible, try this. Apply the background image to another page element that is already in use, but doesn't have a background image.
 ```

 ***CSS***
 ```
 #random-unsuspecting-element { background: url(images/grass.png) no-repeat -9999px -9999px; }
 #grass:hover { background: url(images/grass.png) no-repeat; }
 ```

 ```
The idea create new page elements to use for this preloading technique may pop into your head, like #preload-001, #preload-002, but that's rather against the spirit of web standards. Hence the using of page elements that already exist on your page.

I had the idea to try to and use the same element, only use the :after pseduo-class to load the image, so you didn't need to rely on there being enough extraneous background-free images on your page to work with, but for whatever reason didn't want to preload them properly.
```



## 
Compress CSS with PHP

```
Start your CSS files with this PHP (and name it style.php):
```

***CSS***
```
<?php
    ob_start ("ob_gzhandler");
    header("Content-type: text/css; charset: UTF-8");
    header("Cache-Control: must-revalidate");
    $offset = 60 * 60 ;
    $ExpStr = "Expires: " .
    gmdate("D, d M Y H:i:s",
    time() + $offset) . " GMT";
    header($ExpStr);
?>

body { color: red; }
```

```
Then call your CSS with the PHP file name:
```

***HTML***
```
<link rel='stylesheet' type='text/css' href='css/style.php' />
```


## Rounded Corners

- Standard:

***CSS***
```
-moz-border-radius: 10px;
-webkit-border-radius: 10px;
border-radius: 10px; /* future proofing */
-khtml-border-radius: 10px; /* for old Konqueror browsers */
```

- Individual Corners:

***CSS***
```
-moz-border-radius-topleft: 10px;
-moz-border-radius-topright: 20px;
-moz-border-radius-bottomright: 30px;
-moz-border-radius-bottomleft: 0;

-webkit-border-top-left-radius: 10px;
-webkit-border-top-right-radius: 20px;
-webkit-border-bottom-right-radius: 30px;
-webkit-border-bottom-left-radius: 0;
```

- Shorthand:

>-moz-border-radius: [top-left] [top-right] [bottom-right] [bottom-left]

***CSS***
```
-moz-border-radius: 10px 20px 30px 0;
```

 - Elliptical Rounding (Firefox 3.5+):

>-moz-border-radius-topleft: [horizontal radius] [vertical radius];


***CSS***
```
-moz-border-radius-topleft: 10px 40px;
```

- Elliptical Rounding Shorthand (Firefox 3.5+):

>-moz-border-radius: [horizontal radius] / [vertical radius];

***CSS***
```
-moz-border-radius: 10px / 40px;

-moz-border-radius: 10px 20px 30px 40px / 15px 30px 45px 60px;

Above is the same as:

-moz-border-radius-topleft: 10px 15px;
-moz-border-radius-topright: 20px 30px;
-moz-border-radius-bottomright: 30px 45px;
-moz-border-radius-bottomleft: 40px 60px;
```

 - WebKit Elliptical Rounding

 >All corners:

 ***CSS***
 
 ```
-webkit-border-radius: 36px 12px;
```

>Right corners only:

```
-webkit-border-top-right-radius: 50px 30px; 
-webkit-border-bottom-right-radius: 50px 30px;
```


## Quality Abbreviations

```
Slightly lighter color (assuming your text is black), dotted bottom border, and a question-mark cursor. This has become a somewhat standardized approach, which is always a good thing in design usability.
```

***CSS***
```
abbr {
 border-bottom: 1px dotted #222;
 color: #222;
 cursor: help;
}
```


## Fixed Positioning in IE 6

***CSS***
```
* { margin:0; padding:0; }
html, body {
   height: 100%;
}
body #fixedElement {
   position:fixed !important;
   position: absolute; /*ie6 and above*/
   top: 0;
   right: 0;
}
#page-wrap {
    width: 600px;
    margin: 0 auto; 
    font: 16px/2 Georgia, Serif;
}
```

```
The 100% height on the body and html stuff is in case you want to do fixed positioning along the bottom edge of the browser window.
```


## Remove Dotted Link Borders

```
Dotted borders around links are an accessibility feature most browsers have by default. It's for users who must or choose to navigate by keyboard, there is a visual style applied to those links when "tabbed" to. These borders also show up when the link is clicked (in it's "active" state), and can be an eyesore depending on the design (especially when using something like CSS image replacement, the borders span the length of the screen). You can remove them with this:
```

***CSS***
```
a:active {
    outline: none;
}

```

>NOTE: The advantage here is that the :focus style still will use the outlines, meaning that keyboard navigators will still have the focus styling/visual feedback.



## End Articles with Ivy Leaf

***CSS***
```
p:last-child:after {
       content: "\2766"; /* Here comes the ivy leaf */
       font-size: 150%; /* Makes the leaf larger than the normal text */
       padding-left: 10px; /* Leaf won't clash with the last letter of the text */
       float: right; /* Horizontal position is set to the right edge of the column */
       position: relative; /* This is just an homage to Albert Einstein */
       top: 15px /*Vertical distance from the last line of text */
}
```


## Center DIV with Dynamic Height

***HTML***
```
<div id="page">
       <div id="content_container">
               <div id="content">
                     <p>your content</p>
               </div>
       </div>
</div>
```

***CSS***
```
* { margin: 0; padding: 0; }
#page{display:table;overflow:hidden;margin:0px auto;}
*:first-child+html #page {position:relative;}/*ie7*/
* html #page{position:relative;}/*ie6*/

#content_container{display:table-cell;vertical-align: middle;}
*:first-child+html #content_container{position:absolute;top:50%;}/*ie7*/
* html #content_container{position:absolute;top:50%;}/*ie6*/

*:first-child+html #content{position:relative;top:-50%;}/*ie7*/
* html #content{position:relative;top:-50%;}/*ie6*/

html,body{height:100%;}
#page{height:100%;width:465px;}
```



## Internationalization Language CSS

***CSS***
```
/*Language-specific*/
:lang(af){quotes:'\201E' '\201D' '\201A' '\2019';}
:lang(ak){font-family:Lucida,"DejaVu Sans",inherit;}
:lang(ar){font-family:Tahoma 12,Nazli,KacstOne,"DejaVu Sans",inherit;}
:lang(bg){quotes:'\201E' '\201C' '\201A' '\2018';}
:lang(bn){font-family:FreeSans,MuktiNarrow,Vrinda,inherit;font-size:1.1em;line-height:1.4em;}
:lang(cs){quotes:'\201E' '\201C' '\201A' '\2018';}
:lang(da){quotes:'\00BB' '\00AB' '\203A' '\2039';}
:lang(de){quotes:'\201E' '\201C' '\201A' '\2018';}
:lang(el){font-family:"DejaVu Sans",inherit;quotes:'\00AB' '\00BB' '\2039' '\203A';}
:lang(en-GB){quotes:'\2018' '\2019' '\201C' '\201D';}
:lang(es){quotes:'\00AB' '\00BB' '\2039' '\203A';}
:lang(fa){font-family:Terafik,Traffic,Roya,Nazli,Nazanin,sans;font-size:1.5em;}
:lang(fi){quotes:'\201D' '\201D' '\2019' '\2019';}
:lang(fr){quotes:'\ab\2005' '\2005\bb' '\2039\2005' '\2005\203a';}
:lang(hr){quotes:'\00BB' '\00AB' '\203A' '\2039';}
:lang(is){quotes:'\201E' '\201C' '\201A' '\2018';}
:lang(ja){font-size:1.1em;}
:lang(km){font-family:"Khmer OS System","Khmer OS","Khmer Kampongtrach","CDT Khmer",inherit;line-height:2em;}
:lang(ko){font-size:1.1em;}
:lang(lt){quotes:'\201E' '\201C' '\201A' '\2018';}
:lang(nl){quotes:'\201E' '\201D' '\201A' '\2019';}
:lang(pl){quotes:'\201E' '\201D' '\201A' '\2019';}
:lang(ro){quotes:'\201E' '\201C' '\201A' '\2018';}
:lang(sk){quotes:'\201E' '\201C' '\201A' '\2018';}
:lang(sq){quotes:'\00AB' '\00BB' '\2039' '\203A';}
:lang(sr){quotes:'\201E' '\201C' '\201A' '\2018';}
:lang(sv){quotes:'\201D' '\201D' '\2019' '\2019';}
:lang(tr){quotes:'\00AB' '\00BB' '\2039' '\203A';}
:lang(vi){font-family:"Lucida Grande","Vu Phu Tho","DejaVu Sans",inherit;}
       :lang(vi) a:hover,:lang(vi) a:active{text-decoration:none;color:#606047;}
:lang(zh){font-size:1.5em;}
```



## Print URL After Links

***CSS***
```
@media print{
       a:after{content:" (" attr(href) ") ";font-size:0.8em;font-weight:normal;}
}
```


## PNG Hack/Fix for IE 6

***HTML***
```
img, .png {
       position: relative;
       behavior: expression((this.runtimeStyle.behavior="none")&&(this.pngSet?this.pngSet=true:(this.nodeName == "IMG" && this.src.toLowerCase().indexOf('.png')>-1?(this.runtimeStyle.backgroundImage = "none",
       this.runtimeStyle.filter = "progid:DXImageTransform.Microsoft.AlphaImageLoader(src='" + this.src + "', sizingMethod='image')",
       this.src = "images/transparent.gif"):(this.origBg = this.origBg? this.origBg :this.currentStyle.backgroundImage.toString().replace('url("','').replace('")',''),
       this.runtimeStyle.filter = "progid:DXImageTransform.Microsoft.AlphaImageLoader(src='" + this.origBg + "', sizingMethod='crop')",
       this.runtimeStyle.backgroundImage = "none")),this.pngSet=true));
}
```
>This requires a 1x1px transparent GIF image

***CSS***
```
.yourselector {
       width:200px;
       height:100px;
       background: url(/folder/yourimage.png) no-repeat;
       _background:none;
       _filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(src='/folder/yourimage.png',sizingMethod='crop');
}
```

>Cannot be used with repeating, needs fixed with and height.


## Cross-Browser hr Styling

- For regular browsers

***CSS***   
```
hr {
       border : 0;
       height : 15px;
       background : url(hr.gif) 50% 0 no-repeat;
       margin : 1em 0;
       }
```


- For IE < 8 (use conditional stylesheets)

***CSS***

```
hr {
       display : list-item;
       list-style : url(hr.gif) inside;
       filter : alpha(opacity=0);
       width : 0;
       }
```



## Remove Button Text in IE7

***HTML***
```
<input class="button" type="button" value="Go">

.. or ..

<button class="button">Go</button>
```

***CSS***
```
input.button { text-indent: -9000px; text-transform: capitalize; }
```

>Negative-indent alone unfortunately doesn't work to remove text from a button element in IE7, but add text-transform: capitalize; and presto!



## Style Override Technique

***CSS***
```
p { 
   font-size: 24px !important; 
}
```
>The !important rule at the end of a value will override any other style declarations of that attribute, including inline styles.


## CSS3 Zebra Striping a Table

***CSS***
```
tbody tr:nth-child(odd) {
   background-color: #ccc;
}
```


## CSS Font Families

```
#Sans-Serif
Arial, sans-serif;
Helvetica, sans-serif;
Gill Sans, sans-serif;
Lucida, sans-serif;
Helvetica Narrow, sans-serif;
sans-serif;

#Serif
Times, serif;
Times New Roman, serif;
Palatino, serif;
Bookman, serif;
New Century Schoolbook, serif;
serif;

#Monospace
Andale Mono, monospace;
Courier New, monospace;
Courier, monospace;
Lucidatypewriter, monospace;
Fixed, monospace;
monospace;

#Cursive
Comic Sans, Comic Sans MS, cursive;
Zapf Chancery, cursive;
Coronetscript, cursive;
Florence, cursive;
Parkavenue, cursive;
cursive;

#Fantasy
Impact, fantasy;
Arnoldboecklin, fantasy;
Oldtown, fantasy;
Blippo, fantasy;
Brushstroke, fantasy;
fantasy;

```


## All Stylesheet Media Types

***HTML***

```
<link rel="stylesheet" type="text/css" href="print.css" media="print">
```

- all	  - Used for all media type devices
- aural	  - Used for speech and sound synthesizers
- braille	  - Used for braille tactile feedback devices
- embossed  - Used for paged braille printers
- handheld	- Used for small or handheld devices
- print	  - Used for printers
- projection	  - Used for projected presentations, like slides
- screen	  - Used for computer screens
- tty	  - Used for media using a fixed-pitch character grid, like teletypes and terminals
- tv	- Used for television-type devices



## CSS Text Shadow

```
Regular text shadow:
```

***CSS***
```
p { text-shadow: 1px 1px 1px #000; }
```

>Multiple shadows:

```
p { text-shadow: 1px 1px 1px #000, 3px 3px 5px blue; }
```

```
The first two values specify the length of the shadow offset. The first value specifies the horizontal distance and the second specifies the vertical distance of the shadow. The third value specifies the blur radius and the last value describes the color of the shadow:

1. value = The X-coordinate
2. value = The Y-coordinate
3. value = The blur radius
4. value = The color of the shadow

Using positive numbers as the first two values ends up with placing the shadow to the right of the text horizontally (first value) and placing the shadow below the text vertically (second value).

The third value, the blur radius, is an optional value which can be specified but don’t have to. It’s the amount of pixels the text is stretched which causes a blur effect. If you don’t use the third value it is treated as if you specified a blur radius of zero.
```

>Also, remember you can use RGBA values for the color, for example, a 40% transparency of white:

```
p { text-shadow: 0px 2px 2px rgba(255, 255, 255, 0.4); }
```

## Cross Browser Inline-Block

***CSS***

```
li {
        width: 200px;
        min-height: 250px;
        border: 1px solid #000;
        display: -moz-inline-stack;
        display: inline-block;
        vertical-align: top;
        margin: 5px;
        zoom: 1;
        *display: inline;
        _height: 250px;
}
```

>For More Detail
https://css-tricks.com/snippets/css/cross-browser-inline-block/
https://blog.mozilla.org/webdev/2009/02/20/cross-browser-inline-block/



## Cross-Browser Min Height

***CSS***
```
div { 
   min-height: 500px; 
   height:auto !important; 
   height: 500px; 
}
```

>This works because (thankfully?) IE treats "height" how "min-height" is supposed to be treated.

#### Alternate Using Expressions (IE Only)

```
div {
   height: expression( this.scrollHeight < 501 ? "500px" : "auto" );
}
```

>Sets the minimum height in IE to be 500px. Make sure that this.scrollHeight < 501 is 1 px greater than the minimum height that you want or you will get some strange results.



## Removing Dotted Outline

***CSS***
```
a {
   outline: 0;
}
```
```
Be careful removing outline styles from links, as they are a usability feature. If you do, make sure to define clear focus styles.

If your problem is that the dotted outlines travel all the way to the left or right of the screen because they are floated, try setting the overflow to hidden.
```


## Change Text Selection Color


***CSS***
```
/* Mozilla based browsers */
::-moz-selection {
       background-color: #FFA;
       color: #000;
}

/* Works in Safari */
::selection {
       background-color: #FFA;
       color: #000;
}
```


## Meyer Reset

***CSS***
```
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, font, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td {
	margin: 0;
	padding: 0;
	border: 0;
	outline: 0;
	font-weight: inherit;
	font-style: inherit;
	font-size: 100%;
	font-family: inherit;
	vertical-align: baseline;
}
/* remember to define focus styles! */
:focus {
	outline: 0;
}
body {
	line-height: 1;
	color: black;
	background: white;
}
ol, ul {
	list-style: none;
}
/* tables still need 'cellspacing="0"' in the markup */
table {
	border-collapse: separate;
	border-spacing: 0;
}
caption, th, td {
	text-align: left;
	font-weight: normal;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: "";
}
blockquote, q {
	quotes: "" "";
}
```

***Condensed version:***

```
html,body,div,span,applet,object,iframe,a,abbr,acronym,address,big,cite,code,del,dfn,em,font,img,ins,kbd,q,s,samp,small,strike,strong,sub,sup,tt,var,dl,dt,dd,ol,ul,li,h1,h2,h3,h4,h5,h6,pre,form,fieldset,input,textarea,label,legend,p,blockquote,table,caption,tbody,tfoot,thead,tr,th,td{margin:0;padding:0;border:0;outline:0;font-weight:inherit;font-style:inherit;font-size:100%;font-family:inherit;vertical-align:baseline;}body{line-height:1;color:black;background:white;}:focus{outline:0;}table{border-collapse:collapse;border-spacing:0;}caption,th,td{text-align:left;font-weight:normal;}fieldset,img{border:0;}address,caption,cite,code,dfn,em,strong,th,var{font-style:normal;font-weight:normal;}ol,ul{list-style:none;}h1,h2,h3,h4,h5,h6{font-size:100%;font-weight:normal;}blockquote:before,blockquote:after,q:before,q:after{content:"";}blockquote,q{quotes:"" "";}abbr,acronym{border:0;}
```



## Not-Terrible Image Resizing in IE

***CSS***
```
img {
       -ms-interpolation-mode: bicubic;
}
```
```
If you scale down an image with width and/or height attributes, it's going to look terrible in IE unless you use this.
```


## Better Helvetica

***CSS***
```
body {
   font-family: "HelveticaNeue-Light", "Helvetica Neue Light", "Helvetica Neue", Helvetica, Arial, "Lucida Grande", sans-serif; 
   font-weight: 300;
}
```
>Might as well use the nicest Helvetica you can...




## Give Clickable Elements a Pointer Cursor

***CSS***
```
a[href], input[type='submit'], input[type='image'], label[for], select, button, .pointer {
       cursor: pointer;
}
```

>Some elements that are clickable mysteriously don't trigger a pointer cursor in browsers. This fixes that, and provides a default class "pointer" for applying it to other clickable things as needed.



## Exactly Center an Image/Div Horizontally and Vertically

***CSS***
```
.center {
   width: 300px;
   height: 300px;
   position: absolute;
   left: 50%;
   top: 50%; 
   margin-left: -150px;
   margin-top: -150px;
}
```

>Negative margins are exactly half the height and width, which pull the element back into perfect center. Only works with elements of a fixed height/width.



## Link Pseudo-Classes (In Order)

***CSS***
```
a:link {color: blue;}
a:visited {color: purple;}
a:hover {color: red;}
a:active {color: yellow;}
```

>Link, Visited, Hover, Active
L, V, H, A
LoVe, HAte




## Centering a Website

***HTML***
```
<body>
  <div id="page-wrap">
    <!-- all websites HTML here -->
  </div>
</body>
```

***CSS***
```
#page-wrap {
     width: 800px;
     margin: 0 auto;
}

```


## Standard CSS Image Replacement

***CSS***
```
h1#logo {
   width: 200px; // width of image
   height: 100px; // height of image
   background: url(../path/to/image.jpg); 
   text-indent: -9999px;
}
```

>This technique is credited to Mike Rundle and referred to as the Phark Method. There are many more techniques for CSS Image Replacement.

>For More Detail
https://css-tricks.com/css-image-replacement/

