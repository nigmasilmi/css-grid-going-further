# Dev Notes

## From start to advanced.

## Disclaimer: this is going to be long!

## CSS Grid Terminology

- Grid Container: element with display property set to grid
- Grid Item: element that is direct descendant of the grid container
- Gride line: Horizontal (row) or Vertical (column) line separating the grid into sections
  - Are referenced by number 1 => n, respects the writing configuration (right to left or left to right), also can be named
- Grid cell: intersection between a grid row and a grid column --effectively, the same as a table cell
- Grid track: the space between two or more adjecent grid lines
  - Row tracks: horizontal
  - Column tracks: vertical
- Grid area: rectangular area between four specified grid lines
  - can cover one ore more cells
- Grid gap: the empty space between grid tracks, commonly called a gutters

## Grid Firefox tools

- Clicking on the grid icon adjacent to the container rule, we can see rules, layout and other visual aids to analize and project our grids

## grid-template-columns, grid-template-rows

[grid-template](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template)
[grid-template-columns](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns)
[grid-template-rows](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows)
