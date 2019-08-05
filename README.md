## [Ramón Morcillo](https://www.ramonmorcillo.com/) notes from


# Hugo - Static Site Generator | Tutorial


## by Mike Dane. [Course Link](https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOnyRlyS-liKL5ReHDcj4G3)



## Table of Contents

  - [Introduction to Hugo](#introduction-to-hugo)
  - [Installing Hugo on Windows](#installing-hugo-on-windows)
  - [Creating a New Site / Directory Structure](#creating-a-new-site--directory-structure)
  - [Installing & Using Themes](#installing--using-themes)
  - [Creating & Organizing Content](#creating--organizing-content)


## Introduction to Hugo

Hugo is a **Static Site Generator** which is **written in Go** which makes it go really **fast** when generating static sites. Hugo is really flexible, you can either use some templates already created by the community and not write a single line of code or you can touch the html and css as much as you want. Also it is an **open source free** project with a big community.


## Installing Hugo on Windows

We created a new folder named **Hugo** to store all the Hugo stuff and inside it we create another folder called **bin**. Then we will download it from its [Github releases section](https://github.com/gohugoio/hugo/releases), I will download the windows64 version.

After downloading it, we extract the files into the bin folder. Now we can open a terminal and go to the bin directory and execute it. The **problem** is if we want to execute it in **another place** and to solve this we will edit the **windows path variable** and add the hugo executable file to the path variable. We opened the **Path** variable version and edited it adding the bin folder path where the hugo.exe is located. And now we can use hugo from anywhere, just try to type `hugo version` in the console.

By the way, [here is the video](https://www.youtube.com/watch?v=WvhCGlLcrF8&list=PLLAZ4kZ9dFpOnyRlyS-liKL5ReHDcj4G3&index=3)  to install it on **mac**.

## Creating a New Site / Directory Structure

We use the command `hugo new site first_site` to create a new site. Then inside it we can see already some folders structure. 



*   **Archetypes**. In this folder you can define the data about the content.
*   **Content**. Where you will store all the website content.
*   **Data**. Folder which acts as a database. 
*   **Layouts**. Where you define the website layouts patterns.
*   **Static**. To store all the static elements of the website: images, js, css, …
*   **Themes**. Where you put the themes you already downloaded.
*   **Config.toml**. Configure the settings for the site.


## Installing & Using Themes

You can either **create your own** or just **use one from the community** which you can find in [https://themes.gohugo.io/](https://themes.gohugo.io/). When you select a theme you can either view a demo, download it or go to its site; Every hugo theme is a **Github repository.** In this course we will use a custom theme from **GiraffeAcademy** that we can find [here](https://github.com/giraffeacademy/ga-hugo-theme). Then we clone it with git on the themes folder or download and extract it on the themes folder. We change the name of the folder from ga-hugo-theme-master to **ga-hugo-theme**. Then, in the config.toml we add a new line `theme = "ga-hugo-theme"`.

Now inside the first_site folder we type in the console `hugo server` and go to **localhost:1313** to see the site.


## Creating & Organizing Content

Any kind of content like a post or an article you have to store in the **content** folder creating a **content file**. To create a file we go to the project folder and type in the console `hugo new a.md` where **a.md** is the name of the file. We can also create the files directly in to a **folder** `hugo new dir1/b.md`

By default Hugo sets the files **draft to true** and when we do `hugo server` we can not see them. To see the draft files we have to add **-D** like this `hugo server -D`. Now if we go to **localhost:1313** we will see the files on the site. We can see that the url reflects the location of the file.

There are **2 types** of content in Hugo: **Single content** and **List content.**

*   **List content**. Content that lists other content on the site. In the example the home page is a list page because it lists other pages or contents.
*   **Single content**. It just displays information.

When we create a directory with files inside the content folder Hugo **automatically creates a list page** for that directory. But just for the ones that are at the **root level.** If we have a directory inside another directory and we want the second one to have a list page we have to create it manually and call it **_index.md** `hugo new dir1/dir2/_index.md`. If you want to **override** the list pages on the root level directories just create an _index.md on them `hugo new dir1/_index.md`.


## Front Matter

Front matter is what you call **metadata** so it is **data about our content files.** Inside a file they are **key value pairs** that provide us information about the file. Front Matter can we written in **3 languages: YAML, TOML and JSON**. While JSON is more popular YAML is the default one in hugo files and comes inside 3 hyphens `--- title: “Hello” ---`. 

You can add variables like `author: “Ramón”` and others so it is a very useful way to organize and describe the content.


## Archetypes

An archetype is the **template** that is being used in the **front matter** when Hugo creates a new content file. We can create archetypes for specific directories just **naming it with the directory name.** Then when Hugo creates a new file if there is an archetype for the file directory it will use it to create the front matter but if there is any then it will use the **default archetype**. 


## Shortcodes

Shortcodes are basically predefined **chunks of HTML** that you can insert into your markdown files. Hugo comes with a bunch of **predefined shortcodes** and you can also **create your own**. For example, if you want to add a video to your file instead of adding an html iframe you simply add `{{< youtube videoID >}}` . If you want to know more about shortcuts [here](https://gohugo.io/content-management/shortcodes/) are the Hugo docs for them.


## Taxonomies

Taxonomies in Hugo define **how we group content together**. Hugo provides us with 2 default ones which are: **Tags** and **Categories**. The way we declare the taxonomies is in the **Front Matter**. For example to **add some tags** we create an **array** in the front matter like this `tags: ["tag1", ``"tag2", "tag3"]` and the same goes for **categories** `categories: ["cat1"]`. 

So now if we head to the site and click on the **categories or tags links** of the pages it will redirect to a list page **automatically created** with all the single content files that contain that category or tag.

You can also add **custom taxonomies** but as they are not the default ones ( tags and categories ) you have to tell Hugo about them in the **config.toml**. 

So if for example we want to add a new taxonomy called **moods** `moods: ["Happy", "Upbeat"]` we will have to add in the **config.toml** and array with **all the taxonomies**, including the default ones with the **singular and plural** name of it: 

```
[taxonomies]
    tag = "tags"
    category = "categories"
    mood = "moods"
```

## Templates

When we talk about templates in Hugo we talk about **html templates**. A Hugo theme is made up of Hugo templates. All of the list and single content pages use html templates. Any template in Hugo goes inside the **layouts folder inside the theme folder**. Then inside the **_default folder** are the list and single html files which have some pieces of code to render the content.

### List Page Templates

The list page templates are the templates that lists files use. We can also **overwrite** the templates creating our **custom ones** and to do so we go to the layout folder of the site ( not the one in the theme ), create a folder called _default and inside of it a list.html file.

Then inside that html file we **display the content using hugo variables** like this  `{{.Content}}`. But if we want to show the content of all the single pages in our list page we use **hugo functions**.

```html

<!-- to list all the content from the single files -->

{{.Content}}

{{ range .Pages }}

    {{.Title}} <br>

<!-- closing hugo function tag -->

{{end}}

```	

We can also use other variables like `{{.URL}}` which lists the **url locations**. For example we can create a navigation menu:

```html

  {{.Content}}

    <ul>

        {{ range .Pages }}

        <li><a href="{{.URL}}">{{.Title}}</a></li>

    </ul>

    {{end}}

```

### Single Page Templates

These one are used for the single pages and like the list page templates we can **overwrite** the theme ones with our custom just creating a **single.html** file in a **_default folder inside a layouts one**.

```html

<!DOCTYPE html>

<html lang="en">

<head>

    <meta charset="UTF-8">

    <title>Document</title>

</head>

<body>

    <h1>Header</h1>

    <hr>

    <!-- Using front matter info -->

    <h3>{{.Title}}</h3>

    <h4>{{.Date}}</h4>

    {{.Content}}

    <hr>

    <h1>Footer</h1>

</body>

</html>

```

### Home Page Templates

There is a third template we can use inside Hugo apart from the list and single page templates which is the **Home Template**. To overwrite a theme template with a custom one we have to create an **index.html** file inside our layouts folder.


### Section Templates

Imagine that we want a different template in some of our single pages. To do so we have to create our custom section template by creating a **new folder** inside the page **layouts folder** and **naming it with the section name** we want to create the template for. Now inside this folder we can create new list and single html templates that will overwrite the ones used by default in all the site.


### Base Templates & Blocks

This is a more advanced way of organizing the layout of a site. We create a **baseof.html** file inside a _default folder inside the site layouts one. This baseof.html is going to act as the **overarching template for our entire hugo site**. Every single page of the site is going to be implemented first with this template.

Inside of this template we will use a **block** to define that all the main

```html

<!DOCTYPE html>

<html lang="en">

<head>

    <meta charset="UTF-8">

    <title>Document</title>

</head>

<body>

    Top of baseof

    <hr>

    <!-- This means that the main site block will go here -->

    {{ block "main" . }}

    {{ end }}

    <hr>

    Bottom of baseof

</body>

</html>

```

And then in the list.html and single.html we write another block.

```html

{{ define "main" }}

    This is the list template

{{ end }}

```

We can also use blocks to define **other site modules** like the footer and in the end using blocks makes our templates more powerful and layouts more modular.

### Partial Templates

Partial templates are used to **encompass various elements** of our website making it **more modular** like writing a footer or navigation bar. To use them we create a **partials** folder inside the layouts folder and a new html file. Partial templates should be html files. Example:

```html

<!-- Partial template -->

<h1>{{.Title}}</h1>

<p>{{.Date}}</p>

<hr>

<br>

```

To use it, in the single or list html file we have to pass in the **scope of the current file** `{{ partial "header" . }}` where the `.` represents the scope of all the variables I have access to. In other words, when we put a dot we are passing all the variables to the partial so it can access to them. We can also create and pass a dictionary to them `{{ partial "header" ( dict “myTitle” “myCustomTytle” ) }}` and in the partial access them with `<h1>{{.myTitle}}</h1>`


### Shortcode Templates

Shortcodes are **little pieces of code** that you put inside your markdown files and can use them across **multiple** files.  To use them we go to the layout folder and create a **shortcodes** folder and a new myshortcode.html file with a text `This is the shortcode text`.

Now to access it we go to a markdown file inside the content folder and write `{{< myshortcode >}}`. We can pass variables to it like `{{< myshortcode color="blue" >}}` and to access them in the shortcode we use **.Get** `<p style="color:{{.Get `color`}}">This is the shortcode text</p>`. 

We can also pass **positional parameters** `{{< myshortcode blue  >}}` and then use `<p style="color:{{.Get 0}}">This is the shortcode text</p>` where the 0 means that it will use the parameter in the first position.

There are also **multiple tags shortcodes**. And to access the text passed we use **.Inner** `<p style="background-color: yellow">{{ .Inner }}</p>`** **in the shortcode.

```

<!-- Multiple tags shortcode -->

{{< myshortcode >}}

    This is the text inside the shortcode tags

{{< /myshortcode >}}

```

Finally if we want to pass markdown text we use `%`

```

{{% myshortcode %}}

    **bold text**

{{% /myshortcode %}}

```

## Variables

Variables in Hugo are basically **pieces of information** about either your pages or your website that we can use **inside our templates**. You can **only** use variables inside of **templates or inside the layouts folder**. Some of the basic variables from Hugo are:



*   `{{ .Title }}` To access the title of the page.
*   `{{ .Date }}` To display the date.
*   `{{ .URL }}` It shows the Url of the page

We can create our **custom variables** inside the **Front Matter** of a page. For example, if we add a `myVar: "myValue"` variable in the Front Matter we access it writing in the template `{{ .Params.myVar }}`. Furthermore, we can create custom variables on the template itself using `{{ $myVarName := "aString" }}` and then show it with just `{{ $myVarName }}`. We can declare **strings, numbers and booleans**. 

To learn more about variables [here is the official documentation.](https://gohugo.io/variables/)


## Functions

In Hugo functions are **pre-written pieces of code** that you can call to **do specific things**. Like it happened with the variables, we can **only access them in the templates on the layouts folder**. 

The way to call a function is `{{ funcName param1 param2 }}`. Some examples of functions are:


*   `{{ truncate 10 “This is a really long string” }}` It truncates the string to just show the first 10 characters. It will display like: `This is a ...`
*   `{{ add 1 5 }}` Adds 2 numbers. It will display a `6`.
*   `{{ sub 1 5 }}` Substracts 2 numbers. It will display a `-4`.
*   `{{ singularize “dogs” }}` Changes to the singular name. It will display `dog`.

Another useful	 function would be **range**. We use it in a list template to go through all the pages and access their variables.

```html

{{ range .Pages }}

    {{.Title}} <br>

{{end}}

```

To learn more about functions [here is the official documentation.](https://gohugo.io/functions/)


## Conditionals. If statements

They are just if-else statements that	allows you to **control the execution flow** of a program. We use them writing in a template file inside the layouts folder an **if** then an **operator** and finally a **condition** `{{ if operator condition }}`. There are a lot of operators to use and you use them in two character code. For example:



*   `eq` Equal to
*   `lt` Less than
*   `le` Less than equal to
*   `gt` Greater than
*   `ge` Greater than equal to
*   We can add the `not` keyword to them which will negate any of them

Also we can add an `{{ else }}` statement.

```

{{ $var1 := “dog” }}

{{ $var2 := “cat” }}

{{ if eq $var1 $var2 }}

    True

{{ else }}

    False

{{ end }}

```

This will display `False` in the page. If we would like to **negate the condition** we have to write a **not** and wrap it inside **parenthesis** `{{ if not (eq $var1 $var2) }}`. You can also add an `and` or `or` operator. If $var1 is less than $var2 and $var1 is less than $var3:

```

{{ $var1 := 4 }}

{{ $var2 := 3 }}

{{ $var3 := 2 }}

{{ if and (lt $var1 $var2) (lt $var1 $var3) }}

    True

{{ else }}

    False

{{ end }}

```

## Data Files

Data in Hugo is stored in the **data folder** like a _mini-data-base_ with JSON, TOML or YAML files. So we added a states.json file and now we will access it this way with `.Site.Data.filename`:

```html

<!-- accesing data →

{{range .Site.Data.states}} 

    {{.name}} <br>

{{end}}

```




