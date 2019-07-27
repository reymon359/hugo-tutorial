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



