<section name="f118" class=" section--body section--first section--last" score="
41.25
">Возможности ECMAScript 6 (ES6) можно разделить на три группы: те, которые являются чистым синтетическим сахаром (к примеру: классы), особенности которые улучшают JavaScript (к примеру: **import**) и те которые исправляют недостатки (к примеру: **let**). Большинство блогов и статей содержат в себе все три раздела и могут ошеломить новичков. Эта статья фокусируется исключительно на тех особенностях которые исправляют слабые места.

> **Я надеюсь, что после прочтения вы поймете, что даже используя несколько новшеств ES6, 
> таких как let или оператор “fat-arrow”, вы получите очень много в замен.
> **

**Начнем.**


#1.Область видимости.  

ES5 ограничивалась только областью видимости в пределах функции (к примеру вы могли обернуть код в функцию для формирования такой области) и это создавало много проблем. ES6 предоставляет “блочный”  уровень видимости (к примеру в пределах  фигурных скобок) при использовании “**let**” или “**const**” вместо “**var**”.

##  Ограничение доступности переменной вне области видимости . 


На картинке ниже показано, что переменная “bouns” не доступна вне блока “if” как и в большинстве языков программирования.


> Приметка: Вы можете нажать на изображение чтоб увеличить его
<figure name="be7d" id="be7d" class="graf--figure graf-after--blockquote" score="-12.5
">![][1]</figure>

##   Ограничение повторного декларирования переменной.
 ES6 не позволяет повторное объявление переменных если мы используем **“let” или “const”** в одной области видимости. Это очень помогает избегать дублирования функций при подключении различных библиотек (как в примере с функцией “add”  ниже).
<figure name="4c8d" id="4c8d" class="graf--figure graf-after--p" score="-12.5">
![][2]</figure>


##   Отменяет потребность в самовызывающихся функциях Immediately Invoked Function Expression (IIFE).
В случае с ES5 на примере ниже, нам нужно было использовать самовызывающуюся функцию, чтобы быть уверенными, что мы не “загрязняем” или переопределяем глобальную область видимости. В ES6  мы можем использовать фигурные скобки ({}) вместе с **const** или **let**, что бы получить тот же результат.
<figure name="8cbc" id="8cbc" class="graf--figure graf-after--p" score="-12.5">
![][3]</figure>

##Babel - инструмент для конвертации ES6 в ES5
> Нам необходима полная поддержка ES6 в текущих браузерах и самым популярным инструментом для конвертации ES6 в ES5 является [Babel][4]. Он имеет несколько интерфейсов включая командную строку, Node модуль и онлайн конвертер. Я использую Node модуль для моих приложений и [онлайн версию][5] для быстрой проверки отличий.  На изображении ниже видно как Babel изменяет имя переменной чтоб симулировать поведение для **“let” и “const”**! 

<figure name="2c58" id="2c58" class="graf--figure graf-after--blockquote"
score="-12.5
">![][6]<figcaption class="imageCaption">BabelJS.io renaming variables to
simulate let and const</figcaption></figure>

## Делает без проблемным использование функций внутри циклов
Если вы использовали в ES5 функцию внутри цикла (например: for(var i = 0; i < 3; i++) {…}), и эта функция пыталась получить доступ к переменной “i” из цикла, это было бы проблемой в связи с ее доступностью. В ES6 достаточно “**let**”, чтобы использовать функции без каких либо проблем. 
<figure name="a71a" id="a71a
" class="graf--figure graf-after--p" score="-12.5
">
![][7]</figure>

> Приметка: вы не можете использовать **const** поскольку константы работают только с новым типом циклов как  **for..of**.
>

#2. Лексический “this” (через стрелочные функции) 
В ES5, значение “this” отличалось в зависимости от того, “где” оно вызывалось и даже “как” оно вызывалось и это создавало много проблем для JS разработчиков. ES6 устраняет эти проблемы добавляя лексический “this”.

> Лексический “this” это особенность, которая фиксирует переменную “this” всегда указывать на объект где она была физически размещена. 
<figure
name="46b9" id="46b9" class="graf--figure graf-after--p" score="-12.5
">
![][8]<figcaption class="imageCaption">ES5 — the problem and two workarounds</
figcaption
></figure>

## Проблема и два пути решения в ES5:
На примере ниже мы пытаемся распечатать для пользователя firstName и salary. Но мы получаем данные для salary с сервера (симуляция). Обратите внимание, что когда возвращается ответ - “**this**” является “**window**” вместо объекта “person”. 

## Решение в ES6 
**Достаточно просто использовать стрелочную “fat-arrow” функцию fat-arrow => и вы получите лексический “this” автоматически.**
<figure name="9990" id="9990" class="graf--figure graf-after--p
" score="-12.5
">
![][9]<figcaption class="imageCaption">Line 16 shows how to use => function in
ES6</figcaption></figure>


> На примере ниже видно как Babel конвертирует “**fat-arrow**” функцию в обычную функцию ES5 таким образом, что она работает во всех текущих браузерах.
<figure name="d2b8" id="d2b8" class="graf--figure graf-after--blockquote"
score="-12.5
">![][10]<figcaption class="imageCaption">babel is converting fat-arrow to
regular ES5 function w/ workaround #2</figcaption></figure>

#3. Работа с “аргументами” 

В ES5 “аргументы” имеют вид массива (к примеру мы можем пропускать их через цикл), но на самом деле это не массив. Таким образом функции работы с массивом как sort, slice и другие не применимы к аргументам функций.   В ES6 мы можем использовать новую возможность которая называется “Rest” параметрами. Она представлена тремя точками и называется “**…args**”. “Rest” параметры являются массивом и таким образом мы можем применять к ним все методы работы с массивом данных. 
<figure name="4887" id="4887" class="graf--figure graf-after--p"
score="-12.5
">
![][11]<figcaption class="imageCaption">Picture shows ES6 “Rest” parameters</
figcaption
></figure>

#4. Классы

Концептуально, не существует такого понятия как “Класс” (отпечаток) в JS, как те которые мы привыкли так называть в других ОО языках, к примеру JAVA. Но разработчики долгое время относились к функциям (известным также как “конструкторы функции”) которые создают Объекты, когда мы используем их с ключом “new”, как к Классам.   

Поскольку JS не поддерживает “Классы” как таковые, только симулируя их через “прототипы”, их синтаксис был очень сбивающим с толку, как для разработчиков уже работающих с JS, так и для новичков которые хотели использовать их в традиционном понимании ОО программирования. **Это особенно явно для таких вещей как: создание подклассов, вызов функции в родительском классе и тп**.   

ES6 добавляет новый синтаксис который знаком с других языков программирования, упрощая этим всю ситуацию. Ниже приведен рисунок, который показывает сравнение классов в ES5 м ES6. 

> Приметка: Вы можете нажать на изображение чтоб увеличить его
<figure name="c335" id="
c335" class="graf--figure graf-after--blockquote" score="-12.5
">![][12]<figcaption class="imageCaption">ES5 Vs ES6 (es6-features.org)</
figcaption
></figure>

> **: АПДЕЙТ:  прочитайте: **
> [***Is “Class” In ES6 The New “Bad” Part?***][13]*** (after this)*** 

#5. Строгий режим

[Строгий режим][14] (“use strict”) помогает определить общие проблемы (или “плохие” места) и также помогает использовать [JavaScript более безопасно][15].

В ES5 данный режим опционален, но в ES6 он необходим для большинства его [особенностей][16]. Так большинство разработчиков и инструментов таких как Babel автоматически добавляют  “use strict” в самом начале файла, переводя весь код в строгий режим и вынуждая нас писать  JavaScript лучше.  

Вот так )) 

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