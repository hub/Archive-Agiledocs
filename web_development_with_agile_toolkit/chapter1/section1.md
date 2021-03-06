[Home](../readme.md "Home")

#### SECTION 1
----
## The history of “broken” PHP

Not many remember what web 1.0 applications were like. In early ‘90ties most of web sites on the Internet were static and not interactive. As demand increased Common Gateway Interface (CGI) and soon Perl were becoming incredibly popular.

Two major problems were getting in the way of web software: slow server speed and poor support for JavaScript in the browsers.

PHP3 was released as a promising language and quickly gained popularity. Even today PHP powers the majority of World Wide Web. Yet many consider PHP a poor choice for software development.

The initial versions of PHP language were mimicking C and Perl. A lot of emphasis was on the execution speed and diversity of built-in functionality in PHP. Objects were becoming more and more popular, but they always were optional,
just like C++ applications. What made PHP the most popular language and how to make it more attractive for professional developers? These were my goals in creating Agile Toolkit.

One of the main concepts of PHP is it’s ability to combine HTML and code. While it is appreciated by the novice developers, this feature is at fault for the poor practices in HTML and PHP separation in application.

Many developers today consider PHP a poor or “broken” language.

### Fixing PHP with Agile Toolkit Philosophy

Today there are too many ways to develop a web applications in PHP. What if we just agree on a single “best” way to do things, which would be sufficiently flexible and would fit 90% of the use-cases? That's what Agile Toolkit does philosophically. In the very core it defines the set of principles we use for application development. Agile Toolkit PHP code follows the principles and so will be your code.

If you are a manager of a project and you choose to use Agile Toolkit in your environment adopting the psychology, it will be much easier for new recruits to learn the toolkit. Your code will be consistent no matter how big your project is and it a developer with understanding of Agile Toolkit will be able to look inside any part of your website and instantly understand how it works.

What's more important, is that your developers can also look inside the framework itself, add-ons or any other software built on Agile Toolkit and understand it.

I myself participate as IT manager or consultant in several companies over a decade and this rule have helped us keep all our project in a very maintainable state.

So when PHP comes up with a set of features, we would carefully review them and decide if we want or don't want to use them in the toolkit and globally. Here are some of the features Agile Toolkit advises against using:

* Mixing up PHP and HTML with <?php/?> tags. Always use template engine.
* Static classes and constants. Those are not portable and not fully object-oriented. Use of singletons is also discouraged.
* Over-use of namespaces. We use name-spaces very mildly to separate the core code from add-ons. Avoid "use" keyword as it makes your source codes very confusing.
* Explicit includes. There is only one file you include with Agile Toolkit. The rest is being included automatically by converting class name into filename.
* Private properties and final classes. Unless in rare cases, you can't predict how your class will be used. Embrace extensibility and use "public $_prop" if you need to highlight that some property is public.
* Keep the size of your classes reasonable. Don't make classes longer than a thousands lines of code.
* Don't copy-paste your code. Remember to refactor it.

[Next Section](section2.md "Next Section")