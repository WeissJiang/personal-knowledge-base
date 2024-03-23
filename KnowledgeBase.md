# Personal Knowledge Base

### Table of Contents
| No. | Questions |
| --- | --------- |  
| 1   | [What is SCSS](#what-is-scss)  |
| *   | [What is .NET Core](#what-is-net-core)  |
| *   | [What is Entity Framework Core](#what-is-entity-framework-core)  |
| *   | [What is CMS](#what-is-sitecore)  |
| *   | [What is Nextjs](#what-is-nextjs)  |
| *   | [Bundle and minify static assets in ASP.NET Core](#bundle-and-minify-static-assets-in-aspnet-core)
| *   | [What is IIS Express](#what-is-iis-express)  |
| *   | [What is ASP.NET MVC](#what-is-aspnet-mvc)  |


### What is SCSS?

#### Sass and SCSS
Sass (Syntactically Awesome Stylesheets) is a powerful CSS extension language that provides many useful features such as variables, nesting rules, mixins, inheritance, etc. to help you write CSS more efficiently.

SCSS is a syntax for Sass, and it is the latest version of Sass.SCSS is fully compatible with the CSS syntax, which means that any valid CSS code is valid SCSS code.SCSS files are usually saved with a .scss extension.
The older syntax of Sass (i.e., the "indentation syntax"), called Sass for short and with a .sass file extension, uses indentation rather than curly braces to separate blocks of code, and uses new lines rather than semicolons to separate rules.

#### Comparison of the two:
- CSS is the foundation; it's the standard language for styling web pages.
- Sass adds many programming features to CSS to make your CSS more dynamic and reusable.
- SCSS is a syntax model of Sass that is closer to CSS and is easier to understand and adopt.

#### Variables
Think of variables as a way to store information that you want to reuse throughout your stylesheet. You can store things like colors, font stacks, or any CSS value you think you’ll want to reuse. Sass uses the $ symbol to make something a variable. Here’s an example:

![image](images/scss-1.png)

#### Nesting
When writing HTML you’ve probably noticed that it has a clear nested and visual hierarchy. CSS, on the other hand, doesn’t.

Sass will let you nest your CSS selectors in a way that follows the same visual hierarchy of your HTML. Be aware that overly nested rules will result in over-qualified CSS that could prove hard to maintain and is generally considered bad practice.

With that in mind, here’s an example of some typical styles for a site’s navigation:

![image](images/scss-2.png)

#### Modules

You don’t have to write all your Sass in a single file. You can split it up however you want with the @use rule. This rule loads another Sass file as a module, which means you can refer to its variables, mixins, and functions in your Sass file with a namespace based on the filename. Using a file will also include the CSS it generates in your compiled output!

![image](images/scss-3.png)

#### Mixins

Some things in CSS are a bit tedious to write, especially with CSS3 and the many vendor prefixes that exist. A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. It helps keep your Sass very DRY. You can even pass in values to make your mixin more flexible. Here’s an example for theme.

![image](images/scss-4.png)

#### Extend/Inheritance

Using @extend lets you share a set of CSS properties from one selector to another. In our example we’re going to create a simple series of messaging for errors, warnings and successes using another feature which goes hand in hand with extend, placeholder classes. A placeholder class is a special type of class that only prints when it is extended, and can help keep your compiled CSS neat and clean.

![image](images/scss-5.png)

#### Operators

Doing math in your CSS is very helpful. Sass has a handful of standard math operators like +, -, *, math.div(), and %. In our example we’re going to do some simple math to calculate widths for an article and aside.

![image](images/scss-6.png)

**[⬆ Back to Top](#table-of-contents)**

### What is .NET Core?

### What is Entity Framework Core? 

### What is CMS? 
A CMS, short for content management system, is a software application that allows users to build and manage a website without having to code it from scratch, or know how to code at all.

![image](images/cms-in-the-market.png)

![image](images/cms-in-the-market-2.png)

**[⬆ Back to Top](#table-of-contents)**

### What is Nextjs? 

Next.js is a React-based web framework that provides several features to help you build server-rendered React applications.

**[⬆ Back to Top](#table-of-contents)**

### Bundle and minify static assets in ASP.NET Core

Bundling and minification primarily improve the **first page request** load time. Once a web page has been requested, the browser ***caches the static assets*** (JavaScript, CSS, and images). So, bundling and minification **don't improve performance** when requesting the same page, or pages, on the same site requesting the **same assets**. If the **expires header** isn't set correctly on the assets and if bundling and minification isn't used, the browser's freshness heuristics mark the assets stale after a few days. 

#### Configure Bundles using bundleconfig.json File

![bundling-and-minification-tool](images/bundling-and-minification-2.png)

![bundling-and-minification](images/bundling-and-minification-1.png)

````
[
  {
    "outputFileName": "wwwroot/css/site.min.css",
    "inputFiles": [
      "wwwroot/lib/bootstrap/dist/css/bootstrap.css",
      "wwwroot/css/site.css"
    ]
  },
  {
    "outputFileName": "wwwroot/js/site.min.js",
    "inputFiles": [
      "wwwroot/js/site.js"
    ],
    "minify": {
      "enabled": true,
      "renameLocals": true
    },
    "sourceMap": false
  }
]
````

**outputFileName**: This is a required option and this specifies the name of the output bundle file. It can contain a relative path from the bundleconfig.json file.

**inputFiles**: This is an array of files we want to bundle together and it can also contain relative paths from the bundleconfig.json file. This option is not required so if you will not specify any input file, an empty output file will be generated.

**minify**: This is another **optional** setting and it specifies whether we want to enable minification or not. The default value is enabled: true.

**sourceMap**: This option indicates whether a source map for the bundled file should be generated or not. The default value is false. If this option is set to true, an additional `.map` file containing the mapping information between the original source files and the compressed file will be generated during the process of compressing and combining files.

![bundline-and-minification-setup](images/bundling-and-minification-3.png)

#### Environment-based Bundling and Minification

The Environment Tag Helper only renders its contents when the application is running in specific environments. The following code snippet shows how to use environment tag helper to render non-bundled files in the Development environment and bundled files when the environment is not Development such as Production or Staging.

![bundline-and-minification-environment-tag](images/bundling-and-minification-5.png)

You can change your environment from Development to Production using the project properties dialog as shown in the following screenshot.

![bundline-and-minification-set-environment](images/bundling-and-minification-6.png)


**[More Details](https://www.ezzylearning.net/tutorial/a-step-by-step-guide-to-bundling-and-minification-in-asp-net-core)**


#### Cache busting

![bundline-and-minification-caching-busting](images/bundling-and-minification-4.png)

`v=@GetHashCodeAsString()`

`v=@GetHashCodeAsString()` 是一种在资源链接后添加一个查询字符串的方法，这里 GetHashCodeAsString() 应该是一个方法调用，可能是自定义的，用于生成一个哈希值或版本号。当浏览器请求带有查询参数的资源时，如果查询字符串改变了，浏览器会认为这是一个全新的资源，从而去服务器上重新下载它，而不是从缓存中加载。

`asp-append-version="true`

`asp-append-version="true"` 是一个ASP.NET Core的特定属性，它自动为静态文件的URL添加一个唯一的版本号，这个版本号是该文件内容的哈希值。当文件内容改变时，哈希值会随之改变，导致生成的URL改变，这样浏览器就会加载新版本的文件，而不是从缓存中加载旧版本。

使用 asp-append-version="true" 时，ASP.NET Core 会自动处理版本字符串的生成和添加，你不需要手动指定版本号。

**结合使用**
通常，`v=@GetHashCodeAsString()` 和 `asp-append-version="true"` 不需要一起使用。它们都是解决同一问题（缓存破坏）的不同方法：

如果你在使用ASP.NET Core，`asp-append-version="true"` 是一个简单且自动的方式来确保你的静态文件如CSS和JavaScript被正确地缓存破坏。
`v=@GetHashCodeAsString()` 这种方法更为手动，通常用在没有自动化机制的环境中，或者你需要特定的缓存控制逻辑时。

因此，一般来说，你会选择其中一种方法来实现你的需求。如果你在ASP.NET Core环境中工作，推荐使用 `asp-append-version="true"`。

**[⬆ Back to Top](#table-of-contents)**

### What is IIS Express



### What is ASP.NET MVC