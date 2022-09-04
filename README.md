# facebook_scrapping_service_using_fastAPI
A dockerized facebook scrapping service using fastAPI as well as the database.

- This project is an API meant to scrape posts from Facebook public pages using either page id or page name then store the posts into a mongo-db database. Posts have a unique ID named post_id in the database and can be a good way to identify posts in the database.
- The API is built using fastAPI, the Facebook scraping functionality is thanks to facebook_scraper python library, and the connection to mango-db is made by pymongo.
- This repository contains a requirement.txt file that contains the required python libraries needed for this project, a main.py containing the project's code, a facebook cookies extracted form google chrome browser using get cookies extension , a Dockerfile that can be used to build a docker for the API and a docker-compose file to setting up a MongoDB container.
- 
# Usage 
To build a docker named “fb_scraper” for the API please run this command in the same directory as main.py, Dockerfile, and requirements.txt:


 
 ```
  sudo docker build -t fb_scraper .
```
