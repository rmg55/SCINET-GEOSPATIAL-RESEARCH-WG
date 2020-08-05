#README: How to edit/add content to this website
=======
This branch was created with the ```--orphan``` command so it is independent of the *master* branch. 

Then,  the files from the evanwill - [https://github.com/evanwill/workshop-template-b](https://github.com/evanwill/workshop-template-b) worshop template were added. 

To modify and update this webpage:

1. Fork the repo to your github account
2. download to your local system like
   ```
   git clone local_repo_url
   ```
3. Work on the gh-pages branch
   ```
   git checkout gh-pages
   ```
2. Modify contents in the *content* folder.
3. add changes and commit locally like:
   ```
   git add /path/to/changed/file
   git add /path/to/changed/file
   git add /path/to/changed/file
   git commit
   ```
4. Push changes to your local branch.
   ```
   git push origin gh-pages
   ```
5. Make a pull request to the main repo


Other Information:

When creating content pages:

- to include a page in the header and footer navigation, add nav: true to the file's yml front matter.
- the title: value will appear in the nav, sorted in the order of filenames. For simplicity use leading numbers in the lesson page filenames to create correct order.
- the default layout does not add title to the page, so it can be a short for the nav. Thus, add a title in the Markdown content.


Using figure include:

- put all images in the images directory.
- figures will be centered, and can optionally be given a caption and percentage width.
- in a markdown file where you want the image to appear, use the figure.html include on its own line.
    - pattern: {% include figure.html img="my-cat.jpg" alt="cat" caption="My cat" width="50%" %}

Basic style customization:

- the custom.scss in the assets/css folder exposes variables that can customize the basic style of website.
- Give a tiny splash of color on the header and footer borders by tweaking the $top-border
    - $link-color colors links
    

Repository does not include a Gemfile because it is a very simple project. Originally built using Ruby 2.5+ and Jekyll 3.7+; most recently used Jekyll 4.0.0.
