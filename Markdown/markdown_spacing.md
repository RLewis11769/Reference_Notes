# Spacing

## HTML entities

### \&nbsp;
\&nbsp; will show as many spaces after as you want. Using it will show roughly 1 space &nbsp; on its own, although adding a space on either side will show roughly 3 spaces regardless of how many spaces after. This is because the spaces on either side are both shown.

Use it with a newline if you'd prefer
&nbsp;
visual breaks in your markdown.

Using &nbsp;&nbsp; 2 in a row will actually show 4 spaces. This is because there is a space on either side of the &nbsp markings for readability. 3 in a row with spacing between &nbsp; &nbsp; &nbsp; will show 7 spaces due to the added spacing etc.

### em space
An em space    is a wider space than usual. Just copy-paste it for easy visual

As you can see, \&emsp; &emsp; is the equivalent for &nbsp.

### en space
An en space   is half the width of em space. Just copy-paste it.

As you can see, \&ensp; &ensp; is the equivalent for &nbsp.

### **Guide to HTML Entities**

Here
&nbsp;
is an &nbsp.

Here
&ensp;
is an &ensp.

Here
&emsp;
is an &emsp.

## Math environment

### Dollar tilde dollar

Adding two $ with as many ~ as you would like between will show the same amount of spaces as ~.

For example 5 ~s $~~~~~$ shows 5 spaces.

This doesn't work for all markdown interpreters.

## pre

The pre tag, used with <> including an ending tag, retains all spacing although it removes any bold/italic design. It has a distinctive syling similar to a code block as seen here:

<pre>
Tell me, what is it you plan to do
with your one wild and precious life?
        Mary Oliver
</pre>

## \<br>

Using \<br> will show a newline as in HTML.

The following is a guide:

This
<br>
is similar to the singular line break tag in HTML.

This
<br />
is the recommended tag, more like an full HTML tag with a closing tag.

## \

Using an escape character\
at the end of a line will escape the newline character added.

## Two spaces

Two spaces
at the end of a line will remove the newline character.

## \&nbsp;

Adding an \&nbsp; entity with a newline after
&nbsp;

will include the line break.
