# Project Description

For Capstone, my final project of CS50's Web Programming with Python and JavaScript, I have decided to create my own dynamic and mobile-responsive personal website with HTML, CSS, Python, SQLite, and JavaScript using Django. 

Pages include ```About Me```, ```Projects```, ```Résumé```, ```Blogs```, and ```Contact```. Features include contacting me via a form that uses an external API, commenting/replying (with nested replies to comments supported) on any blog, pagination for blogs and projects, markdown to HTML conversion using django-markdown, as well as a search bar for blogs and projects.

The website uses JavaScript to dynamically create and update projects, blogs, and comments/replies via AJAX. Furthermore, it uses Bootstrap to enhance the aesthetics, user-friendliness, and mobile responsiveness of the website.

The website also uses user authentication to tell whether the current user is an admin of the website or not, and if they are, the website supports creating blogs and projects dynamically using fetch() calls.

Lastly, the website uses various CSS animations on multiple different elements of the site, such as links, projects, blogs, and even comment boxes, to enhance the user's experience.

# Distinctiveness and Complexity

## Distinctiveness

I believe that this project is sufficiently distinct from the other projects I have built during this course as no other project focuses on building a personal website. As a matter of fact, this project actually uses and implements many of the concepts and ideas from past lectures and projects (such as pagination, animations, mobile-responsiveness, Django models, AJAX, dynamic updates without needing to refresh using JavaScript. and user interfaces).

## Complexity

I believe that this project is sufficiently complex compared to the other projects I have built during this course for the following reasons:

1. As mentioned before, this project implements a lot of the concepts and ideas from past lectures and projects, meaning it uses a combination of the many features implemented from past projects.

2. The project contains many features such as dynamic commenting/replying including support of nested replies, dynamic creation of projects and blogs, and project/blog search with the support of substrings.

3. The project is very mobile responsive and adaptive. For example, when wanting to reply on mobile, instead of showing a nested reply comment box, which will go out-of-bounds of the mobile screen, it instead shows a pop-up box which makes replying on mobile much easier, and the ability to contact me when submitting a form (which uses an external API to send submission to my mailbox). Furthermore, the CSS animations used in this project take into account of events such as line breaks and line wraps, which in turn make the animations work as intended even on smaller devices.

4. The project uses four Django models for Badges, Projects, Blogs, and Comments, which includes using relationships such as ManyToMany.

5. The project has its own API implemented, which supports project creation, blog creation, comment/reply creation, project retrieval, blog retrieval, and comment/reply retrieval all using fetch() and AJAX. Some features, such as replies, use nested fetch() calls to properly format the comment section.

6. The project extensively uses CSS across every page and element of the website to enhance the aesthetics, design, and feel.

# File and Directory Contents

**Note: Only notable and important files that I have created/modified will be shown. This essentially means that files that are automatically generated by Django and other unimportant files will not be explored.**

- ```personal_website```: Main directory of the Django project.

    - ```settings.py```: This is the only file worth mentioning inside this directory, as I have added the ```MARKDOWNIFY``` object, which contains a list of all the white-listed HTML tags to ensure proper markdown-to-HTML conversion when using django-markdownify.

- ```website```: Main directory of the website app, the only application of the project.

    - ```static/website```: Contains all the static files of the app.

        - ```images```: Contains all the images used in the app.

        - ```blog.js```: JavaScript file used to dynamically show comments, show comment/reply forms, and create replies for a specific blog via AJAX. This file acts as a script inside ```templates/website/blog.html```.

        - ```blogs.js```: JavaScript file used to render the corresponding results based on a search query on the search bar on the blogs page (```templates/website/blogs.html```).

        - ```create-blog.js```: JavaScript file used to create a blog using fetch() call. This file uses information from a form located at ```templates/website/create-blog.html```.

        - ```create-project.js```: JavaScript file used to create a project using fetch() call. This file uses information from a form located at ```templates/website/create-project.html```.

        - ```projects.js```: JavaScript file used to render the corresponding results based on a search query on the search bar as well as help render all the corresponding badges for each project (using fetch() call) on the projects page (```templates/website/projects.html```).

        - ```styles.css```: The only CSS file used for this project and is used to style various elements and pages of the website.

    - ```templates/website```

        - ```blog.html```: HTML file that defines the structure of each blog. This includes the title, blog features (i.e. author, approximate length, date), blog content, and comments section. This HTML file also uses JavaScript to dynamically render any new comment made from the main comment box shown just under the "Comments Section" header.

        - ```blogs.html```: HTML file that defines the structure of the blogs page, the page that shows all the current active blogs. This includes the search bar, all the blogs, and buttons for "Next" and "Previous" page(s). The file uses flexbox as a container for each blog to make the page mobile-responsive as well as pagination using Django paginator.

        - ```contact.html```: HTML file that defines the structure of the contact form. The contact form uses "formsubmit", an external API that allows for each submission to be sent directly to my mailbox.

        - ```create-blog.html```: HTML file that defines the structure of the blog creation form only to be accessed by administrators of the website.

        - ```create-project.html```: HTML file that defines the structure of the project creation form only to be accessed by administrators of the website.

        - ```index.html```: HTML file that defines the structure of the main (About Me) page of the website.

        - ```js.html```: HTML file that defines the structure of a secret JavaScript poem :).

        - ```layout.html```: HTML file that defines the overall layout of every page of the website. Including the navbar and links on the bottom (Email, GitHub, LinkedIn, Resume).

        - ```projects.html```: HTML file that defines the structure of the projects page, the page that shows all the currently active projects. This includes the search bar, all the projects, and buttons for "Next" and "Previous" page(s). The file uses flexbox as a container for each project to make the page mobile-responsive as well as pagination using Django paginator.

    - ```admin.py```: Python file in which I have registered all the models to be accessed inside the Django admin console.

    - ```models.py```: Python file where I have created the four models used in the website: Badge, Comment, Project, and Blog.

    - ```urls.py```: Python file where I have defined all the urls for both the actual web routes as well as all the routes for the API that I have created.

    - ```views.py```: Python file that contains all application views (redirect links to appropriate HTML files) as well as all the logic needed for the API to function (there are functions for creating projects, getting all projects, creating blogs, getting all blogs, getting replies, etc.).

- ```requirements.txt```: File which contains all the necessary libraries needed to install in order for this website to run properly.

# Running the Application

1. In a terminal, ```git clone``` the contents of ```https://github.com/me50/ImRyzon/tree/web50/projects/2020/x/capstone```.

2. Ensure all the necessary packages from the ```requirements.txt``` file are installed properly.

3. In a terminal, ```cd``` into the main directory.

4. Run ```python manage.py makemigrations website``` to make migrations for the app.

5. Run ```python manage.py migrate``` to apply migrations to your database.

6. Run ```python manage.py runserver``` to run the server.