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

Any kind of content like a post or an article you have to store in the **content** folder creating a **content file**.



