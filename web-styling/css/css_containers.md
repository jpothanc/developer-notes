## Flex

Flexbox is a one-dimensional layout method for laying out items in rows or columns. Items flex to fill additional space and shrink to allow extra items.

### Flex Cheat Sheet

```css
/* display flex items horizontally */
|[][][]|
.container{
    display:flex;
}
/* display flex items vertically */
|
[]
[]
[]
|
.container{
    display:flex;
    flex-direction:column;
}

/* align horizontally */
| [][][] |
.container{
    display:flex;
    justify-content:center;
}

/* align vertically */
| 

[][][] 

|
.container{
    display:flex;
    align-items:center;
}

/* wrap flex items when window size changes */
|
[][][][]
[][][]
| 
.container{
    display:flex;
    flex-wrap:wrap;
}

/* leaves a gap between each flex item 
   use row-gap for leaving gap between rows.
   use gap if you want to leave gap between columns and rows.
*/
|[] [] []| 
.container{
    display:flex;
    column-gap:20px;
}

/* align-self is used by the flex children to align itself with in the flex container. 
*/
|
[][] 
    [] 
| 

.box-3{
    display:flex;
    align-self:end;
}

/* align right most flex item to extreme right  */
|[][]   []| 
.box-3{
    display:flex;
    margin-left:auto;
}

/* sizing flex items propotionally */
|[1][ 2 ][ 3 ]|

.box-1{
    flex:1
}
.box-2{
    flex:2
}
.box-3{
    flex:3
}
```



