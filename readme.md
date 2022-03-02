# Wes Bos' CSS Grid Course Solutions
Solutions for the [CSSgrid.io](https://cssgrid.io/) course. Following along with 25 videos to take my CSS Grid Skills to the next level.  The course is free - shout out to Mozilla Firefox for sponsoring it!

## Table of Contents

- [Starter Files and Tooling Setup](#Starter Files and Tooling Setup)
- [CSS Grid Fundamentals](#CSS Grid Fundamentals)
- [CSS Grid Dev Tools](#CSS Grid Dev Tools)
- [CSS Grid Implicit vs Explicit Tracks](#CSS Grid Implicit vs Explicit Tracks)
- [CSS grid-auto-flow Explained](#CSS grid-auto-flow Explained)
- [Sizing tracks in CSS Grid](#Sizing tracks in CSS Grid)
- [CSS Grid repeat function](#CSS Grid repeat function)
- [Sizing Grid Items](#Sizing Grid Items)
- [Placing Grid Items](#Placing Grid Items)
- [Spanning and Placing Cardio](#Spanning and Placing Cardio)
- [auto-fit and auto-fill](#auto-fit and auto-fill)
- [Using minmax() for Responsive Grids](#Using minmax() for Responsive Grids)
- [Grid Template Areas](#Grid Template Areas)
- [Naming Lines in CSS Grid](#Naming Lines in CSS Grid)
- [grid-auto-flow dense Block Fitting](#grid-auto-flow dense Block Fitting)
- [CSS Grid Alignment + Centering](#CSS Grid Alignment + Centering)
- [Re-ordering Grid Items](#Re-ordering Grid Items)
- [Nesting Grid with Album Layouts](#Nesting Grid with Album Layouts)
- [CSS Grid Image Gallery](#CSS Grid Image Gallery)
- [Flexbox vs CSS Grid](#Flexbox vs CSS Grid)
- [Recreating Codepen](#Recreating Codepen)
- [Bootstrappy Grid with CSS Variables](#Bootstrappy Grid with CSS Variables)
- [Responisve Website](#Responisve Website)
- [Full Bleed Blog Layout](#Full Bleed Blog Layout)

## Starter Files and Tooling Setup

### What I learned
- I've been applying box-sizing all wrong. "Correct" way as follows
    `html{
        box-sizing: border-box;
    }
    *, *:before, *:after {
        box-sizing: inherit;
    }`

** Apparently this is a bit better than applying box-sizing: border-box; directly to the `*` selector **

## CSS Grid Fundamentals

### What I learned
- Number of columns/row defined based on values entered. eg:
          `grid-template-columns: 100px 100px 100px;`
            results in 3 columns 100px wide
            avoid repetitive typing: `repeat(3, 100px)`

- Padding/margin replaced with `grid-gap:[value]`

## CSS Grid Dev Tools

### What I learned
- FireFox grid dev tools: 
    F12 > checkbox under Layout tab. 
    Toggle on element by element basis. 
    Can change guide colors, toggle line numbers, names, etc.

- Grid tools visual cues: 
    dashed = area/track explicitly created in css
    dotted = area/track implicitly created by the browser

- Column/row are called "tracks"

## CSS Grid Implicit vs Explicit Tracks

### What I learned
- Explicit Tracks:
        defined within css
        ex: grid with two rows and two columns:
            `grid-template-columns: 200px 400px;
            grid-template-rows:50px 100px;`

- Implicit Tracks:
    created by browser to accommodate child items beyond explicit grid
    ex: grid with two defined rows/columns but 8 child elements
    `grid-auto-rows:200px 500px;` = any child elements outside of the explicit grid will be in rows 200px and 500px tall.

- FireFox bug has been fixed as of 2/20/22 to allow for multi-definition within `grid-auto-rows`

## CSS grid-auto-flow Explained

### What I learned
- `grid-auto-flow` = defaults to row
- `grid-auto-columns:200px;` = any implicit cols will be 200px wide

## Sizing tracks in CSS Grid

### What I learned
- Remember that `grid-gap` size is ADDED to size of columns
    Avoid percentage based measurements

- Use fr unit instead
    `grid-template-columns: 200px 1fr 1fr;` = divide space evenly between the last two cols.
    `grid-template-columns: 200px 1fr 2fr;` = divide space evenly between the last two cols, but make last col twice as large as the middle col. 

- `grid-template-columns: auto;` = col as wide as largest content.

## CSS Grid repeat function

### What I learned
- Repeat Function
    two arguments, # to repeat, col sizes
    `grid-template-columns: repeat(4, 1fr 2fr);` = create cols of 1fr and 2fr 4 times.
    can get crazy pants with it: `grid-template-columns: 100px repeat(4, 1fr 2fr) 200px repeat(2, 5fr);`

## Sizing Grid Items

### What I learned
 - Emet syntax: create 30 divs with class of item, item# and enter # as text
    `.item.item${$}*30`

- `grid-???: span 2;` 
    like flex-grow for items to expand to multi col/row
    item will drop to next row to span full col space if larger than area available
    item will cause implicit cols/rows to be created if larger than defined grid space 

## Placing Grid Items

### What I learned
-`grid-column-start:2` = start at 2nd column
    will move the item out of normal flow

-`grid-column-end:5` = end at start of 5th column

-`grid-column: 2/5;` = shorthand for start/end cols
    item starts on col 2, ends before col 5
    spans 3

-`grid-column: 2/ span 3;` = can mix start/end and spans
    same result as above 
    
-`grid-column: 1/-1;` = spans full width of grid 
    will only work if rows explicitly defined

## Spanning and Placing Cardio

### What I learned
- `grid-row-start: 4; grid-row:span 3;` is NOT the same as `grid-row:4/span 3;`

## auto-fit and auto-fill

### What I learned
- auto-fill
    have the browser determine number of cols/rows based on size of items
    ex: if 4 child items @150px, add extra cols to fit remaining parent area.
    useful for having an item stick to end of row, regardless of browser size.

- auto-fit 
    only number of cols/rows based on number of items
    ex: if only 4 child items @150px, grid ends at col 4, regardless of remaining area in parent. 

## Using minmax() for Responsive Grids

### What I learned
- `minmax(minValue, maxValue)`
    will wrap to next row w/out a media query

- gtc + tab = grid-template-columns

- `fit-content(value)`
    shorthand for `width: auto; min-width: min-content; max-width:max-content;`
    (css-tricks.com article)[https://css-tricks.com/fit-content-and-fit-content/] on how it works

## Grid Template Areas

### What I learned
- `grid-template-areas: "sidebar-1 content sidebar-2"  "sidebar-1 content sidebar-2" "footer footer footer";`
    place content with `grid-area:footer;` etc
    don't need spans, start/end
    @media - swap `grid-template-area` NAMES
    will create grid without defined size for cols/rows

## Naming Lines in CSS Grid

### What I learned
- place names in [line-name] BEFORE grid value
    `grid-template-columns: [site-left] 1fr [site-right];`
- place content as before
    `grid-column: content-start;`    

## grid-auto-flow dense Block Fitting

### What I learned
- `grid-auto-flow: dense;` = fit items regardless of item order

## CSS Grid Alignment + Centering

### What I learned
- 6 properties
    row/x-axis
        justify-items
        justify-content
        justify-self

    col/y-axis
        align-items 
        align-content
        align-self

- (css-tricks.com reference)[https://css-tricks.com/snippets/css/complete-guide-grid/]  

- `place-items:center center` to define x/y at same time

- Top Tip: set items to `display:grid; justify-content:center; align-items:center` 
    better than flex-box due to `justify-self`

## Re-ordering Grid Items

### What I learned
- Will mess with accessability
    nav/log is fine, but content could be messy
    selection issues as well 
    
- Order starts at 0

## Nesting Grid with Album Layouts

### What I learned
- Key Learnings
    Nested Grids
    Auto-fit 
    MinMax 

- 0 media queries used 

## CSS Grid Image Gallery

### What I learned
- setting `object-fit: cover;` works like `background-size:cover`;
- setting object to have a 1x1 grid allows for item to be placed over another

## Flexbox vs CSS Grid
### What I learned

## Recreating Codepen
### What I learned
- exercise in recreating codepen layout

## Bootstrappy Grid with CSS Variables
### What I learned
- grid has a quirk where children of grid item will expand to fit content rather than adhering to a strict 12 col layout.
    Fix this by using `grid-template-columns: repeat(12, minmax(0, 1fr));` on grid parent
    On grid child add `min-width: 0; width:100%;`

## Responisve Website
### What I learned
- exercise in recreating taco restaurant layout

## Full Bleed Blog Layout
### What I learned
- exercise in recreating blog layout