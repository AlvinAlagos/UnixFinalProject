# UnixFinalProject
SCENARIO: For my final project, i will be developping a GNU/LINUX web server being runned on a VPS.
It will deploy websites online that will be based off my Internet Programming's final project.
I will be preforming basic sysadmin tasks such as creating users, SSH authentication,
etc. This readme file will be updated as i progress through the project

Now the solutions i have for hosting a web server is, i either use Apache2 or Nginx.

## NGINX

PROS:
  - Better at handling static content
  - Better Scalability
  - It was recommended for sites running on a VPS

CONS:
  - Less extensive list of modules

## Apache2

PROS: 
  - Greater selection of modules
  - Better Suited for shared hosting
  - Administrative console

Cons: 
  - Consumes more RAM under heavier load
  - Spawns new processes fore ach requeset making things less effective

## DECISION:
So i dedcided to go with NGINX because it terms of speed, NGINX  beats apache2 . For the webserver i prioritize more speed than a greater list of modules for this project. And i don't like that apache spawns new processses every time a request is made. NGINX will keep it at only one process
