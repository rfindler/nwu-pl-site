# nwu-pl-site

## Introduction and Builds

This site is built using Jekyll, please refer to the [Jekyll Documentation](https://jekyllrb.com/docs/) for in depth information on how to use Jekyll. Before you begin working on this project you'll want to set up Jekyll following the guide for your OS found [here](https://jekyllrb.com/docs/installation/). Once you've successfully insalled Jekyll, you should be able to run `jekyll serve` in the root directory of this project to see live changes you make on `http://localhost:4000`. If for some reason you don't want to run your the local server, you can build the site each time you make changes. The process for this is a little more involved:

1. Make a local file in the root directory called `_config_local.yml` (this is already in `.gitignore`).
2. In this file you need one property, called `url`. It should be the absolute path in your file system to this directory with `/_site`, for me on Windows it looks like this: `url: file:///C:/Users/aowens/projects/nwu-pl-site/_site`. This must be done so links work in your locally built site.
3. Run `jekyll clean` and then `jekyll build --config _config.yml,_config.local` (copy and paste this, spaces matter for the comma separated flag arguments) from the root of this project.
4. You should see a new directory `_site`, in your project directory, inside it is the static site you can view your changes to.

Jekyll doesn't use a database for site data, but rather a construct called [Collections](https://jekyllrb.com/docs/collections/) for static data. On this site there are 3 collections we focus on: **_people**, **_publications**, and **_dissertations**, and each has a corresponding directory containing Markdown files (the individual records). Adding data to a collection is pretty simple, but records do have to conform to a structure so the site can display them properly.

Jekyll use metadata at the beginning of collection records, called [Front Matter](https://jekyllrb.com/docs/front-matter/), to organize the information that each record holds. After the Front Matter comes the actual content of the markdown file, which for this site should just be plain text. Each type of collection has a different use for the content.

The rest of this guide will cover working with each type of data on the site. While reading through the guide, it may be helpful to view the `example_data` directory of the project, which has a sample record of each type.

## People

The **_people** collection is located in the `_people` directory of the project. A record in this collection depends on three required pieces of metadata and two optional pieces:

* `name` - The name of the person in the form "FirstName LastName"
* `role` - The role of the person, which can be: "Student", "Professor", or "Past Student". This is used to sort the members of the group.
* `image_url` - The path to the image of the person that they want displayed on the site. This path is relative to the root directory of the project, and since all images are stored in `assets/img/`, it will be of the form `assets/img/filename.extension`. **Note:** The image should be in a portrait resolution, as it will be scaled down to 160px by 200px, otherwise it will look stretched.
* `email` (optional) - The email of the person, included in a link that will be displayed on the "People" page.
* `twitter` (optional) - The twitter username of the person. Should just be the username, as the page will build the actual link itself.

The content of a **_people** record is the bio for the person, which is displayed beside their photo on the "People" page.

## Publications

The **_publications** collection is located in the `_publications` directory of the project. A record in this collection depends on two required pieces of metadata and one optional piece:

* `title` - The title of the paper
* `authors` - The author(s) of the paper as one string of comma-separated names
* `link` (optional) - A link to a PDF or other document file of the paper. Will only be shown if provided.

The content of a **_publications** record is the abstract for the paper, which is displayed under the paper's title and authors on the "Research" page.

## Dissertations

The **_dissertations** collection is extremely similar to the above and is located in the `_dissertations` directory of the project. This distinction is only made for display order and formatting on the research page. A record in this collection depends on two required pieces of metadata and one optional piece:

* `title` - The title of the dissertation
* `author` - The name of the author in the form "FirstName LastName"
* `link` (optional) - A link to a PDF or other document file of the paper. Will only be shown if provided.

The content of a **_dissertations** record is the abstract for the dissertation, which is displayed under the title and author on the "Research" page.