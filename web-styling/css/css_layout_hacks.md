## Make a Div Fill Height of Remaining Space
```css
/* simple web page with header, main and footer */
[
/* body */
[header]

[main]

[footer]

]

*{
   margin:0
   padding:0
   box-sizing: border-box;
 }
 body{
    height:100vh
    display:flex
    flex-direction: column;

 }

 .header{
    background-color: white;
    height:60px;
 }
 .main{
     background-color: black;
     flex:1
 }
 .footer{
    background-color: white;
    height:40px;
 }
```