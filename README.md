Step Grid
=========

Step Grid is a Sass-powered, responsive grid that should be used in situations where you need known column widths. It breaks most "best practice" conventions of responsive sites today, so realistically you should be using a grid system like [Susy](http://susy.oddbird.net/) or [Unsemantic](http://unsemantic.com/).

Unlike most responsive grid systems, where the container is generally a percentage of the window width, Step Grid allows you to configure a set of specific breakpoints to shrink your container, while the columns will maintain the proportions of the original grid.

The use case that led to this grid was that within a responsive site we were embedding non-responsive content that required a server-side call to re-generate at a new size. By using a set of known breakpoints, we were able to trigger the server-side call when the viewport width passed one of the defined breakpoints.

## Using Step Grid
First include all the grid files in your project:

- `grid.scss:` This will set default variables and import the required grid files
- `/grid/_container.scss:` Functions to generate the grid's container
- `/grid/_columns.scss:` Functions to generate the grid's columns
- `/grid/_functions.scss:` Misc. required functions for the grid

You can view the default settings in `grid.scss`. The grid will default to a center-aligned 1170px wide grid, with 70px columns and 30px gutters. The following variables can be set to override that:

### Grid Variables
- `$grid-columns:` The number of columns in your grid
- `$grid-column-width:` The width of each column
- `$grid-margin-width:` The margins between each column
- `$left-layout:` Set to `true` if the site will be left-aligned (optional).

### Responsive Variables
- `$breakpoints:` A comma delimited list of the breakpoints you would like to use (e.g., `1200px, 960px, 768px, 480px`)
- `$fluid-breakpoint:` If at some point you would like your columns to become fluid and span 100% of the viewport, set it here (generally this would be done at a mobile level breakpoint)
- `$outside-margin:` If you'd like some buffer around where your breakpoint snaps, set it here - it will cause the breakpoint to actually happen at this value above your breakpoints.

## Using presentational classes
Once again, this breaks "best practice" conventions, which today are to use semantic names for elements in your HTML (i.e., `article` `nav`, etc.), and then apply your grid classes to those elements in the CSS. However, if you require grid-specific classes, use `@include step-grid;` after you have defined your grid variables and imported the grid files.