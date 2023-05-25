# Sveta's Blog Technical Documentation

## Introduction

Sveta's Blog is a Django-based blogging platform that allows authorized users to create and edit posts. 
The site is designed for teenagers and adults to share their thoughts and ideas through blog posts.

## Pages and Functionality

Main Page: The main page displays all the posts in a chronological order. Each post includes the author's name, date of publication, title, and text.

![image](https://github.com/MironovaSveta/my-first-blog/assets/104065509/a77f361e-b532-4e80-a6f2-bde02a3259bb)

Add a Post Page: This page allows authorized users to create a new blog post. Users can enter a title and the content of the post, and upon submission, the post will be saved and displayed on the main page.

![image](https://github.com/MironovaSveta/my-first-blog/assets/104065509/a1fa7815-2f1d-4903-9b7f-b1321e4b0d8a)

Edit Post Page: Authorized users can access this page to edit their existing blog posts. They can modify the title and content of the post and save the changes.

![image](https://github.com/MironovaSveta/my-first-blog/assets/104065509/8a08b397-946f-4755-a3de-73903ef82a09)

Authorization Page: This page provides a form for users to enter their username and password to log in to the site. Only registered and authorized users can add or edit posts.

![image](https://github.com/MironovaSveta/my-first-blog/assets/104065509/4518e87f-e9bf-45b6-b3c3-e985c8659d9b)

![image](https://github.com/MironovaSveta/my-first-blog/assets/104065509/e2ef110c-56fe-4e90-8c04-eefd3f7d699f)

View Post Page: This page displays a specific blog post with its complete details, including the author's name, date of publication, title, and text. Non-authorized users can view the posts but cannot perform any editing actions.

![image](https://github.com/MironovaSveta/my-first-blog/assets/104065509/50a3e585-c8a3-45a9-871c-9ec2e8642700)

## Authorization Process

To gain authorization to add or edit posts, users need to register an account by contacting the admin. 
Once registered, they can log in using their username and password on the Authorization Page. 
After successful authentication, users will be granted access to the Add a Post Page and Edit Post Page.

## Design and Layout

The site has an orange header with a clickable "Sveta's Blog" logo that redirects to the main page. 
The overall layout follows a clean and minimalistic design with a white background.

## Security Considerations

To ensure security, the site implements Cross-Site Request Forgery (CSRF) protection. 
When adding a new post, the server generates and verifies a CSRF token to protect against unauthorized requests.

## Performance and Deployment

The site has been tested on laptops and mobile devices to ensure compatibility and responsiveness. 
Currently, the site is hosted on PythonAnywhere and will remain accessible at this location for the next three months. 
After that period, the site will only be available on the localhost.

## Customization and Configuration

There are no additional customization or configuration options available to the users or administrators beyond the provided functionality.

This technical documentation provides an overview of Sveta's Blog, its pages, functionality, authorization process, design, security considerations, and deployment information. If you have any further questions or need additional assistance, please don't hesitate to ask.
