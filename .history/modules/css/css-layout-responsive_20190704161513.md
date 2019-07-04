# Responsive CSS Layouts

We'll create a quite generic solution for this - a grid system. Essentially: imagine you have an element with an unknown number of children. Each of those children is some percentage of the width of parent such that they make equal rows, like 25% wide each for four columns, 33.33% wide each for three columns, etc. The goal is to fill the space of this "grid" evenly. There are an unknown number of children, so let's say you were going with 25% and there were 7 children, that would be 4 in the first row and 3 in the second.

## Grid system