## BLOCK-readText

### Positioning Content

Over the last few chapter we have been creating boxes and manipulating their size and spaces around them. So far we have been only looking the layouts where contents are flowing vertically, means single column layouts. But when it comes to creating a real website, the layout can be complex. It's not only about creating boxes or working with single column layout, but more about place your content in more digestible way.

To create layout and represent our content in a more beautiful way CSS provide usability to position our content and elements in any imaginable way. In this chapter we are going to look into multicolumn layouts. We will be learning how to create reusable layouts.

#### Positioning with inline-block

Usually to create outline for any section or division we will be working with block-level elements. And the block-level element always start from a new line taking whole available width, that we know from the previous chapter. One of the approach we can take to make block-level elements line up one after another, is overwrite it's display property value to `inline-block`. We have already seen how to work with inline-block level elements.

```
  <header>..........</header>
  <aside>.........</aside><!--
  --><section>.........</section>
  <footer>............</footer>

  section, aside {
    display: inline-block;
    margin: 0 1.5%;
  }
  aside {
    margin: 0 1.5%;
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
