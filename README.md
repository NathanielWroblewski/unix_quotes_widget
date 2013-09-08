Dashing Daily Unix
=
Description
-

A [Dashing](http://shopify.github.com/dashing) widget to display daily nuggets of [Unix Philosophy](http://en.wikipedia.org/wiki/Unix_philosophy) courtesy of [Eric S. Raymond](http://en.wikipedia.org/wiki/Eric_S._Raymond).

Preview
-
![Screen Shot](http://i.imgur.com/6GXHHVZ.png "Screen Shot")

Useage
-
To use this widget, copy `unix.coffee`, `unix.html`, and `unix.scss` into the `/widgets/unix` directory of your Dashing app.  This directory does not exist in new Dashing apps, so you may have to create it.  Then, copy the `unix.rb` file into your `/jobs` folder.

To include the widget in a dashboard, add the following to your dashboard layout file:

#####dashboards/sample.erb

```HTML+ERB
...
  <li data-row="1" data-col="1" data-sizex="2" data-sizey="1">
    <div data-id="unix" data-view="Unix"></div>
  </li>
...
```

Code
-
#####widgets/unix/unix.coffee

```coffee

class Dashing.Unix extends Dashing.Widget

```

#####widgets/unix/unix.html

```HTML
<h3 class="maxim" data-bind="quote[0] | raw"></h3>
<p class="content" data-bind="quote[1] | raw"></p>

<p class="updated-at" data-bind="updatedAtMessage"></p>
```

#####widgets/unix/unix.scss

```SCSS
$background-color:  #030C22;
$full-color:  rgba(255, 255, 255, 1);
$light-color: rgba(255, 255, 255, 0.7);
$really-light-color: rgba(255, 255, 255, 0.4);

.unix {
  background-color: $background-color;
  .maxim {
    margin-bottom: 20px;
  }
  .content {
    color: $light-color;
    font-size: 18px;
    text-align:justify;
  }
  .updated-at {
    color: $really-light-color;
  }
}
```

#####jobs/unix.rb

```rb
principles = [
  [ 'Rule of Modularity',
    'Developers should build a program out of simple parts connected by '    +
    'well-defined interfaces, so problems are local, and parts of the '      +
    'program can be replaced in future versions to support new features. '   +
    'This rule aims to save time on debugging code that is complex, long, '  +
    'and unreadable.'],
  [ 'Rule of Clarity',
    'Developers should write programs as if the most important '             +
    'communication is to the developer, including him- or herself, who '     +
    'will read and maintain the program rather than the computer. This '     +
    'rule aims to make code readable and comprehensible for whomever works ' +
    'on the code in the future.'
    ],
  [ 'Rule of Composition',
    'Developers should write programs that can communicate easily with '     +
    'other programs.  This rule aims to allow developers to break down '     +
    'projects into small, simple programs rather than overly complex, '      +
    'monolithic programs.'
    ],
  [ 'Rule of Separation',
    'Developers should separate the mechanisms of the programs from the '    +
    'policies of the programs; one method is to divide a program into a '    +
    'front-end interface and back-end engine that interface communicates '   +
    'with.  This rule aims to let policies be changed without '              +
    'destabilizing mechanisms and consequently reducing the number of bugs.'
    ],
  [ 'Rule of Simplicity',
    'Developers should design for simplicity by looking for ways to break '  +
    'up program systems into small, straightforward, cooperating pieces. '   +
    'This rule aims to discourage developers\' affection for writing '       +
    '"intricate and beautiful complexities" that are in reality bug prone '  +
    'programs.'
    ],
  [ 'Rule of Parsimony',
    'Developers should avoid writing big programs.  This rule aims to '      +
    'prevent overinvestment of development time in failed or suboptimal '    +
    'approaches caused by the owners of the program\'s reluctance to throw ' +
    'away visibly large pieces of work. Smaller programs are not only '      +
    'easier to optimize and maintain; they are easier to delete when '       +
    'deprecated.'
    ],
  [ 'Rule of Transparency',
    'Developers should design for visibility and discoverability by '        +
    'writing in a way that their thought process can lucidly be seen by '    +
    'future developers working on the project and using input and output '   +
    'formats that make it easy to identify valid input and correct output. ' +
    'This rule aims to reduce debugging time and extend the lifespan of '    +
    'programs.'
    ],
  [ 'Rule of Robustness',
    'Developers should design robust programs by designing for '             +
    'transparency and discoverability, because code that is easy to '        +
    'understand is easier to stress test for unexpected conditions that '    +
    'may not be foreseeable in complex programs. This rule aims to help '    +
    'developers build robust, reliable products.'
    ],
  [ 'Rule of Representation',
    'Developers should choose to make data more complicated rather than '    +
    'the procedural logic of the program when faced with the choice, '       +
    'because it is easier for humans to understand complex data compared '   +
    'with complex logic.  This rule aims to make programs more readable '    +
    'for any developer working on the project, which allows the program '    +
    'to be maintained.'
    ],
  [ 'Rule of Least Surprise',
    'Developers should design programs that build on top of the potential '  +
    'users\' expected knowledge; for example, \'+\' should always mean '     +
    'addition in a calculator program.  This rule aims to encourage '        +
    'developers to build intuitive products that are easy to use.'
    ],
  [ 'Rule of Silence',
    'Developers should design programs so that they do not print '           +
    'unnecessary output. This rule aims to allow other programs and '        +
    'developers to pick out the information they need from a program\'s '    +
    'output without having to parse verbosity.'
    ],
  [ 'Rule of Repair',
    'Developers should design programs that fail in a manner that is easy '  +
    'to localize and diagnose or, in other words, "fail noisily". This '     +
    'rule aims to prevent incorrect output from a program from becoming '    +
    'an input and corrupting the output of other code undetected.'
    ],
  [ 'Rule of Economy',
    'Developers should value developer time over machine time, because '     +
    'machine cycles as of the year 2013 are relatively inexpensive '         +
    'compared to prices in the 1970s.  This rule aims to reduce '            +
    'development costs of projects.'
    ],
  [ 'Rule of Generation',
    'Developers should avoid writing code by hand and instead write '        +
    'abstract, high-level programs that generate code.  This rule aims '     +
    'to reduce human errors and save time.'
    ],
  [ 'Rule of Optimization',
    'Developers should prototype software before polishing it.  This rule '  +
    'aims to prevent developers from spending too much time for marginal '   +
    'gains.'
    ],
  [ 'Rule of Diversity',
    'Developers should design their programs to be flexible and open. '      +
    'This rule aims to make programs flexible, allowing them to be used '    +
    'in other ways than their developers intended.'
    ],
  [ 'Rule of Extensibility',
    'Developers should design for the future by making their protocols '     +
    'extensible, allowing for easy plugins without modification to the '     +
    'program\'s architecture by other developers, noting the version of '    +
    'the program, and more. This rule aims to extend the lifespan and '      +
    'enhance the utility of the code the developer writes.'
    ],
]

SCHEDULER.every '24h', first_in: 0 do

  quote = principles.sample

  send_event('unix', { quote: quote })
end

```
