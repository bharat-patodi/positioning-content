## BLOCK-readText

### Positioning Content

Over the last few chapter we have been creating boxes and manipulating their size and spaces around them. So far we have been only looking the layouts where contents are flowing vertically, means single column layouts. But when it comes to creating a real website, the layout can be complex. It's not only about creating boxes or working with single column layout, but more about place your content in more digestible way.

To create layout and represent our content in a more beautiful way CSS provide usability to position our content and elements in any imaginable way. In this chapter we are going to look into multicolumn layouts. We will be learning how to create reusable layouts.

#### Positioning with inline-block

Usually to create outline for any section or division we will be working with block-level elements. And the block-level element always start from a new line taking whole available width, that we know from the previous chapter. One of the approach we can take to make block-level elements line up one after another, is overwrite it's display property value to `inline-block`. We have already seen how to work with inline-block level elements.

```
  <!-- HTML -->
  <header>..........</header>
  <aside>.........</aside><!--
  --><section>.........</section>
  <footer>............</footer>

  <!-- CSS -->
  header, aside, section, footer {
    background: green;
    padding: 50px;
    box-sizing: border-box;
  }
  section, aside {
    display: inline-block;
    margin: 32px 1.5%;
  }
  aside {
    width: 30%;
  }
  section {
    width: 63%;
  }
```

In this example we want the header at the top and footer at the bottom of the page. In between we have a sidebar on the left and a section on same line. That means we have two column layout. So to make aside and section come in a single line we overwritten its display property value to `inline-block`. So that they accept all the box model properties and will line up one after another on the same line.

> ##### The Universal Selector
>
> As you see in the above code I used `border-box` value to the `box-sizing` for every element.
> Generally the best `box-sizing` value to use is `border-box`, this we know from the previous chapter ["Box Model"](https://github.com/AltCampus/AC-STYLE-box-model/blob/master/Ex1-explanation.md).
> The `border-box` value makes our math much easier. And that's the best practice to make every element as `border-box`. This will be helpful while working with percentage unit.
> To select every element on a document there is universal selector in CSS.
>
> ```
>   *, *:before, *:after {
> 	  box-sizing: border-box;
>   }
>
> ```
>
> The `*` is a universal selector, which target each and every elemnt in the document.
> The `*:before` and `*:after` is a pseudo element which I have mentioned below.

Remember, in the box model chapter, we have discussed that, there always exist a small space between the inline-block element and how to get rid of that. So do not forget to remove that space. It may disturb the flow the content on a page.

## BLOCK-writeCode

### Exercise 1

1. Create a simple page having header, main content and a footer.

2. Inside the header keep the brand name to the left and all the navigation to the right.

3. Inside the main content take an article section having two columns. In the first column put a heading and some introductory text of the article and in the second column take an image.

## BLOCK-readText

#### Positioning with floats

Another way we can position the elements on a page is with the `float` property. Floats let the element to position side by side. It removes the element from the normal flow of the page and position it to the left or right of the parent element. And all other upcoming element will then flow around the floated elements.

The float comes with three different values: `left, right, and none`. Left and right value position the element to the left and right of the parent element respectively. If the elements are not wrapped inside the parent then the element will be aligned to the left and right of the window. And the last value `none` has no effect on the element. This is the default value, if the element has no float property then it will be considered as floated none.

```

  <!-- HTML -->
  <img src="https://altcampus.io/images/student-image.svg" alt="">
  <p>
    Float property removes the element from the normal flow of the page and position it to the left or right of the parent element.
  </p>

  <!-- CSS -->

  img {
    float: left;
  }

```

![Float Basic Example](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/positioning-content/float-image.png)

Here in the above example the image is floated left. Therfore the paragrphs(upcoming element) are are wrapping around the image as necessary.

The float property is pretty versatile. Applying it on multiple element at the same time, allows element to come to or opposite each other. Multiple column layout can be created easily with floats. From here we can start giving the real website like structure to our layout.

Nowadays we have some other specifications like `Flexbox and CSS-Grid` which have been introduced recently. These new specifications have almost replaced the float based layouts. In modern websites, you'll find such specifications has been used to style the layouts. But still, we will cover the floats, because this is the foundation which has been used in the majority of the websites.

#### Use of Floats

Let's create the similar layout that we made above with inline-block positioning. But this time with float. We have header at the top, aside and section in center and the footer at the bottom.

```

  <!-- HTML -->
  <header>..........</header>
  <aside>.........</aside>
  <section>.........</section>
  <footer>............</footer>

  <!-- CSS -->

  header, aside, section, footer {
    padding: 50px;
    box-sizing: border-box;
  }
  aside {
    float: left;
  }
  section {
    float: right;
  }

```

If you experiment above code, you will get header at the top, but few things you will find which may not be friendly. The aside and section, being a block-level element, instead of stacking on top of each other, they are sitting opposite to each other. Also the aside and section element instead of taking whole availabe width, is covering the space according tot the content it wraps or the amount of padding it has.

You will also find the footer is sitting in between the aside and section element.

According to above the discussion the aside and section element are out of the normal flow of the page. They are positioned to the left and right side of the page, opposite to each other. The float property causes the element to take space according to the content. However, you can apply width to both the element according to the need. Also margin, so that they do not touch each other.

As all upcoming element will flow around the floated element, that's why the footer is in gutter between the aside and section. To get rid of this we can apply `clear: both` on footer. The `clear` property, we will cover soon in the next section.

```

  <!-- HTML -->
  <header>..........</header>
  <aside>.........</aside>
  <section>.........</section>
  <footer>............</footer>

  <!-- CSS -->

  header, aside, section, footer {
    padding: 50px;
    background: green;
    box-sizing: border-box;
  }
  aside {
    float: left;
    width: 30%;
    margin: 32px 1.5%;
  }
  section {
    float: right;
    width: 63%;
    margin: 32px 1.5%;
  }
  footer {
    clear: both;
  }

```

> #### Floats May Changes the Display Property
>
> When we float any element then it is removed from the normal flow of the page which also alters the default display property of the element.
> A block elements may start covering the space according to the content it wraps.
> To fix this behavior we can apply some fixed width according to the need.
>
> ```
>  section {
>    float: left;
>    width: 600px;
>  }
>  aside {
>   float: right;
>    width: 300px;
>  }
> ```
>
> An inline-level element for example `<span>` ignores `height` and `width` property.
> However, it may accept `height` and `width` if floated.
>
> ```
>  span {
>    float: left;
>    width: 300px;
>    height: 300px;
>  }
> ```

#### Clearing and Containing the floats

We have seen how the floats affect the normal flow of elements on a page. We saw how the rest of the elements bleed into the floated elements.

Originally, the float was introduced to float an image and the rest of the content will automatically will flow around it. It was never intended to build layout or position content. But slowly it's use started to design complex layouts with multiple columns.

To design layout with float, there are some pitfalls that we have already seen in above example. Sometimes you may find the proper styles are not rendering. To get rid of those pitfalls and bring back the content into the normal flow of the page we can clear or contain floats.

##### Clearing the floats

The `clear` property in CSS accept three different values, `left, right and both`.
The `left` value will clear the left floats and `right` will clear right floats. `Both` value will clear both the right and left floats and it is more safer to apply.

```

  div {
    clear: left;
  }
  div {
    clear: right;
  }
  div {
    clear: both;
  }

```

The clear property must be applied to the element appeared after the floated element to return the element into normal flow of the page. As we have applied clear property to the `footer` in the above example.

```

  <!-- HTML -->
  <header>..........</header>
  <aside>.........</aside>
  <section>.........</section>
  <footer>............</footer>

  <!-- CSS -->

  header, aside, section, footer {
    padding: 50px;
    background: green;
    box-sizing: border-box;
  }
  aside {
    float: left;
    width: 30%;
    margin: 32px 1.5%;
  }
  section {
    float: right;
    width: 63%;
    margin: 32px 1.5%;
  }
  footer {
    clear: both;
  }

```

#### Containing the floats

However, clearing floats won't return each and everything back to normal. One of the most popular problems you may encounter with a parent containing floated elements. For example, let's wrap the floated element from above, inside a parent div and apply some background color it.

```

  <!-- HTML -->
  <header>..........</header>
  <div class="parent">
    <aside>.........</aside>
    <section>.........</section>
  </div>

  <footer>............</footer>

  <!-- CSS -->

  header, aside, section, footer {
    padding: 50px;
    background: green;
    box-sizing: border-box;
  }
  .parent {
    background-color: orange;
  }
  aside {
    float: left;
    width: 30%;
    margin: 32px 1.5%;
  }
  section {
    float: right;
    width: 63%;
    margin: 32px 1.5%;
  }
  footer {
    clear: both;
  }

```

If you checkout the result of the above code, you wont see background-color of the parent.
Now inspect your element and checkout the `height` of the parent, it will be `0`. But the parent element must be having some height, because it is wrapping `section` and `aside`. So to bring back everything to the normal flow even the parent's styles, we contain the floats instead of clearing.

To contain floats there are different approaches. The most popular are: placing an empty div with `clear: both` styles, overflow technique, Clearfix technique, etc.

##### Placing an empty div.

In this case, we place an empty `div` before the closing tag of the parent element and set its style to `clear: both`.

```

  <!-- HTML -->
  <header>..........</header>
  <div class="parent">
    <aside>.........</aside>
    <section>.........</section>
    <div class="clear"></div>
  </div>

  <footer>............</footer>

  <!-- CSS -->

  header, aside, section, footer {
    padding: 50px;
    background: green;
    box-sizing: border-box;
  }
  .parent {
    background-color: orange;
  }
  aside {
    float: left;
    width: 30%;
    margin: 32px 1.5%;
  }
  section {
    float: right;
    width: 63%;
    margin: 32px 1.5%;
  }
  .clear {
    clear: both;
  }

```

Containing floats in this way is not semantically correct. On a page, we can have number of floated elements at numerous places. So we will have to place empty div as many times as we have used float on a page, which is contextually not correct.

##### Overflow technique

In this technique, we use CSS `overflow` property to the parent containing floated elements and set the value auto. Overflow property comes with a few different values, most popular are auto, hidden, scroll, etc.

```

  <!-- HTML -->
  <header>..........</header>
  <div class="parent">
    <aside>.........</aside>
    <section>.........</section>
  </div>

  <footer>............</footer>

  <!-- CSS -->

  header, aside, section, footer {
    padding: 50px;
    background: green;
    box-sizing: border-box;
  }
  .parent {
    background-color: orange;
    overflow: auto;
  }
  aside {
    float: left;
    width: 30%;
    margin: 32px 1.5%;
  }
  section {
    float: right;
    width: 63%;
    margin: 32px 1.5%;
  }

```

The parent will gain back its height and all the styles applied to it. The overflow method also comes with few drawback. This to be worked in internet explorer 6 we will have to specify some fix height or width.

Also, `overflow: auto` may add a scrollbar to the element in internet explorer on an Apple Computer. So instead we apply `overflow: hidden`. But the problem with hidden is that few styles like box-shadow may cut off outside the parent. It's just that different browsers treat overflow property differently.

##### Cleafix Technique

One of the most effective ways to contain floats is the clearfix method. The clearfix technique is more preferable and has advantages over other techniques.

In this method, we define some sort rules in CSS to the parent element containing floated elements .

```

  <!-- HTML -->
  <header>..........</header>
  <div class="parent">
    <aside>.........</aside>
    <section>.........</section>
  </div>
  <footer>............</footer>

  <!-- CSS -->

  header, aside, section, footer {
    padding: 50px;
    background: green;
    box-sizing: border-box;
  }
  .parent {
    background-color: orange;
  }
  aside {
    float: left;
    width: 30%;
    margin: 32px 1.5%;
  }
  section {
    float: right;
    width: 63%;
    margin: 32px 1.5%;
  }
  .parent:before, .parent:after {
  content: "";
    display: table;
  }
  .parent:after {
    clear: both;
  }

```

The above code might be a little bit confusing, few things are here which we are seeing for the first time. Actually, this method consists of `:before` and :`after` pseudo elements which is bringing back our page into normal flow.

`:before` and `:after` pseudo elements creates dynamic content above and below the elemnt wherever we apply. Here, in this case, the content is empty but if we put anything inside the content(content: "pseudo") we can see the dynamic content will appear on our page. We will cover this topic(before and after) again in our `complex selector` chapter.

The before and after pseudo element will create a hidden element above and below the parent class. We created a table-cell using `display: table` to the the pseudo elements. This is to make block-level element so that it should take full available width above and below the element. The `display: block` would also work fine, but `display: table` will ensure consistency for the older version of internet explorer

The pseudo elements area now a block-level element. It will start from the left end and will go till the right end. This will work as a wall above and below the elements to prevent above and below margin from collapsing and will contain the floating affect inside the box.

At the end to the `:after` pseudo-element, we also applied clear: both. This is to clear floats so that the next upcoming element does not get wrapped around the floated elements.

This method is known as "clearfix", just because you may find these rules might be associated with the "clearfix" or "cf" class. The "clearfix" class is more popular so we call it clearfix method, you can take any class value.

This class name is also more modular. Just define clearfix rules once under `clearfix` class in your CSS and use it on different parent elements containg floated elements. No nedd to define the rules for different parents again and again.

```

  <!-- HTML -->
  <header>..........</header>
  <div class="parent clearfix">
    <aside>.........</aside>
    <section>.........</section>
  </div>
  <footer>............</footer>

  <!-- CSS -->

  header, aside, section, footer {
    padding: 50px;
    background: green;
    box-sizing: border-box;
  }
  .parent {
    background-color: orange;
  }
  aside {
    float: left;
    width: 30%;
    margin: 32px 1.5%;
  }
  section {
    float: right;
    width: 63%;
    margin: 32px 1.5%;
  }
  .clearfix:before, .clearfix:after {
    content: "";
    display: table;
  }
  .clearfix:after {
    clear: both;
  }

```

This is how we generally work with "floats and clearfix". Now suppose we have three or more columns instead of two in a row. Then how should we take the approach?

To position multi-columns in a row, we will `float: left` all the columns instead of floating one to the left another to right. Then according to the column size we can apply width to the floated elements.

```

  <!-- HTML -->
  <header>......</header>
  <section class="parent clearfix">
    <div class="col">......</div>
    <div class="col">......</div>
    <div class="col">......</div>
  </section>
  <footer>.......</footer>

  <!-- CSS -->

  header, .parent, .col, footer {
    bacground: #bada55;
    padding: 50px;
    box-sizing: border-box;
  }
  .parent {
    margin: 32px 0;
  }
  .col {
    float: left;
    width: 30%;
    margin: 0 1.5%;
  }
  .clearfix:before, .clearfix:after {
    content: "";
    display: table;
  }
  .clearfix:after {
    clear: both;
  }

```

All these methods to clear and contain floats works fine. Which approach you should take totally upon you. At the end it all matters you need to bring back the content into normal flow of the page if you use float.

## BLOCK-writeTextAnswer

1. What are the different ways to position the elements in a page?

2. Which way will you prefer to position the elements in a row and why?

3. What are different values does float property accepts?

4. Float makes the element goes out of the flow, how can we fix the problem to get back into the normal flow?

5. What are the disadvantages if we use clearing method to bring the element back to the normal flow?

6. Explain overflow technique to contain floats as well disadvantages of it.

7. Explain the clearfix method.

## BLOCK-writeCode

### Exercise 2

1. Create a simple page having header, main content and a footer.

2. Inside the header keep the brand name to the left and all the navigation to the right.

3. Inside the main content crate three columns. In each column take one image and a paragraph below the image.

## BLOCK-readText

#### Creating Reusable and Flexible Layouts

To build layouts whether you take `inline-block` or `float` positioning, it's open to you. Take any method whatever works better for you.

However, there are some new CSS specification to position content. For example Flex and Grid`based properties. But I want you to first learn about the foundation part, that's why we discussed`floats and inline-block` positioning.

Anyway whatever approach you take to position the contnet, your layout must be reusable and flexible.

##### Reusable Layout

A reusable layout consits of modular classes, and that classes can be reuse again and again. We have already learned taking same class on multiple elements, also multiple class on on same element in the chapter [Getting-to-know-more-about-html-and-css](https://github.com/AltCampus/AC-STYLE-getting-to-know-more-about-html-and-css/edit/master/Ex3-explanation2.md). It is always best practice to write modular styles and reuse it again and again. We will see an example to create reusable layout. But before that we will learn about flexible layout, flexible container. Thereafter we will combine all these things to create a reusable and flexible layout.

##### Flexible Layout

A flexible layout consists of flexible units(relativ units such as percentage). The benefit of flexible layouts are that it adjust its size according to the size of screens.

At some point we need to make our layout responsive, that we will learn "Responsive Web Design". And the foundation of "Responsive Web Desing" is based on flexible layouts. So why not start the foundation part from here only.

In flexible layout usually there is `flexible container` and the columns are created using percentage. Therefore the layout can have flexibility in every size of the screen.

#### Working With Percentages

Percentages are a relative unit in CSS represented by % unit notation on of the most helpful unit to create flexible lauyouts. Percentage unit work in relation to another object in a layout. For example, let's say we have a column of width 50% in our page.

```

  <section>
    <div class="column">......</div>
  </section>

  section {
    width: 1200px;
  }
  .column {
    width: 50%;
  }

```

Here, the column's width is 50%, so it will look for its parent width in which it is nested and then it's width will be calculated. The section's width is 1200px, so the column width will be 600px. If the section's width decreases or increases accordingly the column's width will also decrease or increase but it will always remain 50% of its parent.

Percentage units are always based on the parent element's size. So whenever we define the things in percentage it will always look for its parent.

#### Creating a flexible container

Container sometimes also known as wrapper and sometimes container and wrapper are considered as different two different elments on page. It's a debatable topic, depends upon developer how they take it. But according to my understanding a container or a wrapper is an element that wraps everything else on the page.

We define a class with container or wrapper with some set of rules which will wrap the content on the page.

Here is an example of container.

```

  .container {
    max-width: 990px;
    margin: 0 auto;
    padding: 0 30px;
  }

```

##### Width Vs Max-Width

The container element will take some specified width. And the content will remain within the specified width.

Here instead of using `width`, we used `max-width` property. The `max-width` property will keep the container flexible, so when browser window is narrower the layout will automatically adjust according to the device size. It is important for making a site usable for smaller devices.

Using just `width` property, you will get horizontal scroll bar when the browser window is narrower. For example:

```

  .container {
    width: 990px;
    margin: 0 auto;
    padding: 0 32px;
  }

```

The `margin: 0 auto` value will keep the container horizontally center of the window. This keeps the alignment of content in sections uniform. The `0` value provide top and bottom margin 0. Th `auto` value is for auto margin from left and right, thus the container remains horizontally center.

We also applied `padding: 0 30px` on container. It is to to provide breathing space from left and right to our content. This doesn't make much sense for larger devices. But good for mobile devices. So, whenever our layout opens in smaller devices the content will not exactly stick to the edges of the screen with no breathing space.

The container class can be applied on sections.

```
  <!-- HTML -->
  <body>
    <section>
      <div class="container">......</div>
    </section>
    <section>
      <div class="container">......</div>
    </section>
  </body>
```

The container class can be used on any element. Usually we apply container class on sections or the div inside the container. If each sections on a page is having different background-color and the background-color is flowing from the left edge to the right edge of the window, then you should define container class on div nesting inside the section.

#### Reusable and Flexible Layouts in Practice

Now that we have knowledge of flexible layout and flexible container, it's time to combine them and create a reusable layout.

As we know a reusable layout consits of modular classes. Let's create three column layout and each column same width with similar styles.

```
  <!-- HTML -->
  <section class="container clearfix">
    <div class="col-1-3">......</div>
    <div class="col-1-3">......</div>
    <div class="col-1-3">......</div>
  </section>

  <!-- CSS -->
  .container {
    max-width: 992px;
    margin: 0 auto;
    padding: 0 30px;
  }
  .col-1-3 {
    float: left;
    width: 30%;
    margin: 1.5%;
  }
  .clearfix:before, .clearfix:after {
    content: "";
    display: table;
  }
  .clearfix:after {
    clear: both;
  }
```

To create three column we have taken `col-1-3` a modular and applied on three `divs` inside a section. The `col-1-3` class will apply similar styles on each divs (`float: left; width: 30%; margin: 1.5%;`). That is what is known as modular class, with just one class we set the styles for three divisions. The `container` class on section will wrap all three division inside it and `clearfix` will contain float inside it.

Now if need another section having three column similar to above on our page the we can use the same code again.

```
  <body>
    <section class="container clearfix">
      <div class="col-1-3">......</div>
      <div class="col-1-3">......</div>
      <div class="col-1-3">......</div>
    </section>
    ......
    <section class="container clearfix">
      <div class="col-1-3">......</div>
      <div class="col-1-3">......</div>
      <div class="col-1-3">......</div>
    </section>
  </body>
```

This is the benefit of creating a reusable layout, you can use it as many time as you want. This will help you in saving your time as well as will prevent you from repeating.

Learning positioning content on a page is one of the great challange, and we did it. I know there might confusion but that's fine. To master the topic just need few times practice.
Mastering the topic will be huge step towards mastering the two languages(HTMl & CSS).

## BLOCK-writeTextAnswer

1. What are the benefits of using reusable and flexible layout?

2. Howw does the percentage unit work in CSS?

3. What is the universal selector?

4. What is the use of margin: 0 auto;? explain.
