<section name="f118" class=" section--body section--first section--last" score="
41.25
">ECMAScript 6 (ES6) features can be divided into features that are pure
syntactic sugar (like:**class**), features that enhance JavaScript (like **
import**) and features that fix some of JS’s “bad” parts (like **let **keyword
). Most blogs and articles combine all 3 types and can overwhelm new comers. So 
I am writing a blog that talks about just the features that fix “bad” parts.

> **I hope that by the end of this blog you’ll realize that by using just a
> couple ES6 features like let, fat-arrow etc, you’ll get massive returns.
>**
OK, Let’s get started.

ES5 only had “function-level scope” (i.e. you wrap code in functions to
create scope) and caused a lot of issues. ES6 provides “block”-level scoping(i.e
curly-braces to scope) when we use
“**let**” or “**const**” instead of “**var**”.

Below picture shows that the variable “bonus” is not hoisted outside of the
“if” block making work as most programming languages.

> Note: You can click on the pictures to zoom and read<figure name="be7d" id="
be7d" class="graf--figure graf-after--blockquote" score="-12.5
">![][1]</figure>

ES6 doesn’t allow duplicate declaration of variables when we declare them
using**“let” or “const” in the same scope**. This is very helpful in avoiding
duplicate function expressions coming from different libraries (like the “add” 
function expression below
).<figure name="4c8d" id="4c8d" class="graf--figure graf-after--p" score="-12.5
">

![][2]</figure>

In ES5, in cases like below, we had to use Immediately Invoked Function
Expression (IIFE) to ensure we don’t not pollute or overwrite the global scope. 
In ES6, we can just use curly braces ({}) and use**const** or **let** to get
the same effect.<figure name="8cbc" id="8cbc" class="graf--figure graf-after--p
" score="-12.5
">

![][3]</figure>

> We need to ultimately run ES6 in a regular browser. [Babel][4] is the most
> popular tool used to convert ES6 to ES5. It has various interfaces like a CLI, 
> Node-module and also an online converter. I use the node module for my apps and 
> use the
>[online version][5] to quickly see the differences.
> Below picture shows how Babel renames the variables to simulate “let” and
> “const
> ”!<figure name="2c58" id="2c58" class="graf--figure graf-after--blockquote"
score="-12.5
">![][6]<figcaption class="imageCaption">BabelJS.io renaming variables to
simulate let and const</figcaption></figure>

In ES5, if you had a function inside a loop (like for(var i = 0; i < 3; i
++) {…}), and if that function tried to access the looping variable “i”, we’d be
in trouble because of hoisting. In ES6, if you use
“**let**”, you can use functions without any issue.<figure name="a71a" id="a71a
" class="graf--figure graf-after--p" score="-12.5
">

![][7]</figure>

> Note: You can’t use **const **because it is **constant **unless you are using
> the new for..of loop.
>
In ES5, “this” can vary based on “where” it is called and even “how
” it is called and has caused all sorts of pains for JS developers. ES6 
eliminates this major issue by “lexical” this.

> Lexical “this” a feature that forces the variable “this” to always
> point to the object where it is
>**physically** located within.
In the below picture, we are trying to print a user’s firstName and salary.
But we are getting the salary from the server (simulated). Notice that when the 
response comes back, “this” is “window” instead of the “person” object.<figure
name="46b9" id="46b9" class="graf--figure graf-after--p" score="-12.5
">

![][8]<figcaption class="imageCaption">ES5 — the problem and two workarounds</
figcaption
></figure>

**Simply use the fat-arrow function => and you get the lexical “this”
automatically.**<figure name="9990" id="9990" class="graf--figure graf-after--p
" score="-12.5
">

![][9]<figcaption class="imageCaption">Line 16 shows how to use => function in
ES6</figcaption></figure>

> The below picture shows how Babel converts fat-arrow function into regular
> ES5 function w/ workaround so that it works in current browsers.
><figure name="d2b8" id="d2b8" class="graf--figure graf-after--blockquote"
score="-12.5
">![][10]<figcaption class="imageCaption">babel is converting fat-arrow to
regular ES5 function w/ workaround #2</figcaption></figure>

In ES5, “arguments” acts like an Array (i.e. we can loop over it), but is
not an Array. So, all the Array functions like sort, slice and so on are not 
available.

In ES6, we can use a new feature called “Rest” parameters. It’s
represented with 3 dots and a name like
 **…args. **Rest parameters is an Array and so we can use all the Array
functions.<figure name="4887" id="4887" class="graf--figure graf-after--p"
score="-12.5
">

![][11]<figcaption class="imageCaption">Picture shows ES6 “Rest” parameters</
figcaption
></figure>

Conceptually, there is no such thing as a “Class”(i.e. blueprint) in JS
like it is in other OO languages like Java. But people for a long time have 
treated the “function” (aka “function constructors”) that creates Objects when 
we use the “new” keyword as Classes.

And since JS doesn’t support the “Classes” and just simulates it via “
prototypes”, it’s syntax has been very confusing for both existing JS developers
and new comers who wants to use it in a traditional OO fashion.**This is
especially true for** **things like: creating subclasses, calling functions in
parent class and so on.**

ES6 brings a new syntax that’s common in various programming languages and
makes the whole thing simple. Below picture shows a side-by-side comparison of 
ES5 and ES6 classes.

> Note: You can click on the picture to zoom and read<figure name="c335" id="
c335" class="graf--figure graf-after--blockquote" score="-12.5
">![][12]<figcaption class="imageCaption">ES5 Vs ES6 (es6-features.org)</
figcaption
></figure>

> **UPDATE: Be sure to read: **
> [***Is “Class” In ES6 The New “Bad” Part?***][13]*** (after this)*** 
[Strict Mode][14](“use strict”) helps identify common issues (or “bad”
parts) and also helps with[“securing” JavaScript][15]. In ES5, the Strict Mode
is optional but in ES6, it’s needed for many[ES6 features][16]. So most people
and tools like babel automatically add “use strict” at the top of the file 
putting the whole JS code in strict mode and forcing us to write better 
JavaScript.

That’s it! 🙏

*🎉🎉🎉 ****If you like this post, please 1. ***❤❤❤* ****it below on Medium and 2
. please share it on Twitter. You may retweet the below card****🎉🎉🎉*<figure
name="1809" id="1809" class="graf--figure graf--iframe graf-after--p" score="-13.
75
"></figure>

**Thanks for reading!!**😀🙏</section>

 [1]: img/1*_sSmBGUVfnTNPbmDCcSYXQ.png
 [2]: img/1*0hlaggfnV34FjyrqTiNibQ.png
 [3]: img/1*yU9z2vrCpQ2N1Z-dNtlzbA.png
 [4]: http://babeljs.io/
 [5]: http://babeljs.io/repl/
 [6]: img/1*z8AcAGsYEgh5Sxtt6rev2w.png
 [7]: img/1*dsRnyw5CBwCZjyAjDi55Xg.png
 [8]: img/1*2UoDXLLTVcHTKfIEeE8Aow.png
 [9]: img/1*iJ1CK-Na-KTtfKkh69_NYA.png
 [10]: img/1*4RDvh0kMnYAE2dxNIYY31Q.png
 [11]: img/1*N4UibXqU1KkTkWb6icv5Qw.png
 [12]: img/1*QtHnKOR06KK8Z_LQ-QIwzA.png

 [13]: https://medium.com/@rajaraodv/is-class-in-es6-the-new-bad-part-6c4e6fe1ee65#.4hqgpj2uv

 [14]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode

 [15]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode#Securing_JavaScript
 [16]: http://www.ecma-international.org/ecma-262/6.0/#sec-strict-mode-code