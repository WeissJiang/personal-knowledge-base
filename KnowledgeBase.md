# Personal Knowledge Base

### Table of Contents
| No. | Questions |
| --- | --------- |  
| 1   | [What is SCSS](#what-is-scss)  |
| *   | [What is DotNet Core](#what-is-dotnet-core)  |
| *   | [What is Entity Framework Core](#what-is-entity-framework-core)  |
| *   | [What is CMS](#what-is-sitecore )  |
| *   | [What is Nextjs](#what-is-nextjs )  |

### What is SCSS?

**Sass and SCSS**
Sass (Syntactically Awesome Stylesheets) is a powerful CSS extension language that provides many useful features such as variables, nesting rules, mixins, inheritance, etc. to help you write CSS more efficiently.

SCSS is a syntax for Sass, and it is the latest version of Sass.SCSS is fully compatible with the CSS syntax, which means that any valid CSS code is valid SCSS code.SCSS files are usually saved with a .scss extension.
The older syntax of Sass (i.e., the "indentation syntax"), called Sass for short and with a .sass file extension, uses indentation rather than curly braces to separate blocks of code, and uses new lines rather than semicolons to separate rules.

**Comparison of the two:**
- CSS is the foundation; it's the standard language for styling web pages.
- Sass adds many programming features to CSS to make your CSS more dynamic and reusable.
- SCSS is a syntax model of Sass that is closer to CSS and is easier to understand and adopt.

**Variables**
Think of variables as a way to store information that you want to reuse throughout your stylesheet. You can store things like colors, font stacks, or any CSS value you think you’ll want to reuse. Sass uses the $ symbol to make something a variable. Here’s an example:

![image](images/scss-1.png)

**Nesting**
When writing HTML you’ve probably noticed that it has a clear nested and visual hierarchy. CSS, on the other hand, doesn’t.

Sass will let you nest your CSS selectors in a way that follows the same visual hierarchy of your HTML. Be aware that overly nested rules will result in over-qualified CSS that could prove hard to maintain and is generally considered bad practice.

With that in mind, here’s an example of some typical styles for a site’s navigation:

![image](images/scss-2.png)

**Modules**

You don’t have to write all your Sass in a single file. You can split it up however you want with the @use rule. This rule loads another Sass file as a module, which means you can refer to its variables, mixins, and functions in your Sass file with a namespace based on the filename. Using a file will also include the CSS it generates in your compiled output!

![image](images/scss-3.png)

**Mixins**

Some things in CSS are a bit tedious to write, especially with CSS3 and the many vendor prefixes that exist. A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. It helps keep your Sass very DRY. You can even pass in values to make your mixin more flexible. Here’s an example for theme.

![image](images/scss-4.png)

**Extend/Inheritance**

Using @extend lets you share a set of CSS properties from one selector to another. In our example we’re going to create a simple series of messaging for errors, warnings and successes using another feature which goes hand in hand with extend, placeholder classes. A placeholder class is a special type of class that only prints when it is extended, and can help keep your compiled CSS neat and clean.

![image](images/scss-5.png)

**Operators**

Doing math in your CSS is very helpful. Sass has a handful of standard math operators like +, -, *, math.div(), and %. In our example we’re going to do some simple math to calculate widths for an article and aside.

![image](images/scss-6.png)

**[⬆ Back to Top](#table-of-contents)**

### What is DotNet Core?

### What is Entity Framework Core? 

### What is CMS? 
A CMS, short for content management system, is a software application that allows users to build and manage a website without having to code it from scratch, or know how to code at all.

![image](images/cms-in-the-market.png)

![image](images/cms-in-the-market-2.png)

**[⬆ Back to Top](#table-of-contents)**

### What is Nextjs? 

Next.js is a React-based web framework that provides several features to help you build server-rendered React applications.

**[⬆ Back to Top](#table-of-contents)**
