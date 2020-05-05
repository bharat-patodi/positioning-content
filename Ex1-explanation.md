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

Remember, in the box model chapter, we have discussed that, there always exist a small space between the inline-block element and how to get rid of that. So do not forget to remove that space. It may disturb the flow the content on a page.

## BLOCK-writeCode

### Exercise 1

1. Create a simple page having header, main content and a footer.

2. Inside the header keep the brand name to the left and all the navigation to the right.

3. Inside the main content take an article section having two columns. In the first column put a heading and some introductory text of the article and in the second column take an image.

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
