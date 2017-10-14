---
title: "CSS Grid Layout Module"
date: 2017-10-10T16:44:40-07:00
tags: ["CSS", "HTML"]
draft: false
---

# About the new CSS Grid Layout Module aka CSS Grid

CSS Grid is a new method of using a grid concept to lay out content in an HTML page. It provides a mechanism for developers to divide available space for layout into columns and rows using a set of predictable sizing behaviours. CSS Grid will not only make it easy for developers to layout the most complicated designs but also, will make it possible to create designs that could not be implemented through other available solutions, such as Flexbox.

Another main feature about CSS Grid is how easy it will be to adopt a new layout to different screens sizes by repositioning items using Query Strings. 

The first time I heard about CSS Grid was in March 2017, in an article published by Morten Rand-Hendriksen. By that time only 6.8% of the browsers supported CSS Grid. According to the website ["Can I Use?"](http://caniuse.com/#feat=css-grid) 68.14% of the browsers currently fully support the use of CSS Grid worldwide. 

## How to define a grid in CSS

To define a Grid use "display:grid" or "display:inline-grid" on the parent element. You can then create a grid using the grid-template-columns and grid-template-rows properties.

```css
.wrapper {
  display: grid;
  grid-template-columns: 25% 50% 25%;
  grid-template-rows: 75px;
  grid-gap: 1px;
  background-color: #fff;
  width: 50%;
  margin: auto;
}
```
In the example above, we declare a wrapper class that creates a grid with three columns with a percentage based width and percentage and with a pixel base height.

```html
<div class="wrapper">
  <div class="box a">A</div>
  <div class="box b">B</div>
  <div class="box c">C</div>
  <div class="box d">D</div>
  <div class="box e">E</div>
  <div class="box f">F</div>
</div>
```

The result:

<div class="wrapper">
  <div class="box a">A</div>
  <div class="box b">B</div>
  <div class="box c">C</div>
  <div class="box d">D</div>
  <div class="box e">E</div>
  <div class="box f">F</div>
</div>

## Elements placement in CSS Grid

In CSS Grid you place elements inside the defined grid by using the grid-column and grid-row properties. As noted by Morten Rand-Hendriksen, CSS Grid allows developers to think the same way designers do while creating layouts by drawing a grid and placing the page elements inside it. 

Bellow is an example of a ten by ten grid where page elements are distributed within the grid with different sizes:

<div class="wrapper2">
  <div class="box head">Head</div>
  <div class="box aside">Aside</div>
  <div class="box highlight">Highlight</div>
  <div class="box content1">Content 1</div>
  <div class="box content2">Content 2</div>
  <div class="box content3">Content 3</div>
  <div class="box content4">Content 4</div>
  <div class="box footer">Footer</div>
</div>

Like other CSS elements, CSS Grid also offers a short notation for its properties.

Below is the code for the classes used in the example:

CSS Source
```css
.head, .footer {
  grid-column: 1 / 10;
}

.aside {
  grid-column: 2 / 4;
  grid-row: 2 / 10;
}

.highlight {
  grid-column: 5 / 9;
  grid-row: 3 / 5;
}

.content1 {
  grid-column: 5 / 7;
  grid-row: 6 / 7;
}
.content2 {
  grid-column: 7 / 9;
  grid-row: 6 / 7;
}
.content3 {
  grid-column: 5 / 7;
  grid-row: 8 / 9;
}
.content4 {
  grid-column: 7 / 9;
  grid-row: 8 / 9;
}
```

HTML Source
```html
<div class="wrapper2">
  <div class="box head">Head</div>
  <div class="box aside">Aside</div>
  <div class="box highlight">Highlight</div>
  <div class="box content1">Content 1</div>
  <div class="box content2">Content 2</div>
  <div class="box content3">Content 3</div>
  <div class="box content4">Content 4</div>
  <div class="box footer">Footer</div>
</div>
```

CSS Grid provides another advantage when building the layouts for different screen sizes and devices. For the other screen sizes, all you need to do is combine the use of CSS Grid and media queries using the classes you applied in your main layout. For instance, in the design above I may want to display the aside content below the header followed by the highlight and each content. I would need to rewrite the CSS for each class repositioning my elements inside the grid accordingly.

CSS Source
```css
@media (max-width: 700px) {
  .aside, .highlight, .content1, .content2, .content3, .content4 {
    grid-column: 1 / 10;
  }
  .aside {
    grid-row: 2;
  }
  .highlight {
    grid-row: 3;
  }
  .content1 {
    grid-row: 4;
  }
  .content2 {
    grid-row: 5;
  }
  .content3, .content4 {
    grid-row: 6;
  }
  .content4 {
    grid-row: 7;
  }
}
```

As you can see, compared to the old Flex Grid solution CSS Grid has many advantages such as: 

- Uses a simple syntax easy to read and write code
- Puts the development closer to the design
- Gives a more efficient solution to design for different screen sizes
- Allows the easy build of complex designs that otherwise were hard or impossible to implement with a simple solution

In this post, I used some common properties of the Grid Element. I suggest reading the [W3C CSS Grid Layout Specification](https://www.w3.org/TR/css3-grid-layout/) to view all the properties and syntax offered by CSS Grid.

## References

- [W3C Org::](https://www.w3.org/TR/css3-grid-layout/) Date Accessed: 2017-10-03
- [caniuse::](http://caniuse.com/#feat=css-grid) Date Accessed: 2017-10-03
- [css-grid-next-evolution-web-layout](https://www.linkedin.com/pulse/css-grid-next-evolution-web-layout-morten-rand-hendriksen?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_recent_activity_details_shares%3BVcMxADMXTa2w84JBTA7QyQ%3D%3D&licu=urn%3Ali%3Acontrol%3Ad_flagship3_profile_view_base_recent_activity_details_shares-original_share_object) Date Accessed: 2017-10-13	
- [mor10.com::](https://mor10.com/wceu2017/) Date Accessed: 2017-10-03
- [smashingmagazine.com](https://www.smashingmagazine.com/2017/06/building-production-ready-css-grid-layout/?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_recent_activity_details_shares%3BVcMxADMXTa2w84JBTA7QyQ%3D%3D) Date Accessed: 2017-10-13
- [Grid by Example](https://gridbyexample.com/) Date Accessed: 2017-10-13


