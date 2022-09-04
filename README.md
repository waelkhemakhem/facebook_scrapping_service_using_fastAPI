# facebook_scrapping_service_using_fastAPI
A dockerized facebook scrapping service using fastAPI as well as the database.

- This project is an API meant to scrape posts from Facebook public pages using either page id or page name then store the posts into a mongo-db database. Posts have a unique ID named post_id in the database and can be a good way to identify posts in the database.
- The API is built using fastAPI, the Facebook scraping functionality is thanks to facebook_scraper python library, and the connection to mango-db is made by pymongo.
- This repository contains a requirement.txt file that contains the required python libraries needed for this project, a main.py containing the project's code, a facebook cookies extracted form google chrome browser using get cookies extension , a Dockerfile that can be used to build a docker for the API and a docker-compose file to setting up a MongoDB container.

# Usage 
To build a docker named “fb_scraper” for the API please run this command in the same directory as main.py, Dockerfile, and requirements.txt:


 
 ```
  sudo docker build -t fb_scraper .
```

Next, we need to create a directory called “database” inside the “mongodb” directory to map to the database location of the container. This will enable local access to the database. We use the -pv operator to create those parent folders.

 ```
  mkdir -pv database
```

Now,go to the “mongodb” folder and run the docker-compose up command to start the MongoDB container. The -d operator runs the detached container as a background process.


 ```
  sudo docker-compose up -d
```




# Guide

This is a quick guide for using the API routes that are made in the script:

/scrap/ : This route is used for scraping data from Facebook and storing it in the database, please give it the following arguments:

- page : page_id or page_name

- limit (optional, default=2): limit the number of pages of posts to scrape from that page (preferably limit >1 because a lower value might give no results depending on the page)

- save (optional, default=False): if True, the scraped posts would be saved in the database, otherwise they would be just shown on the screen.

/post/ : This is used to retrieve a post from the database using its post_id. Only needed argument is post_id

/load/: This is used to retrieve 1 or multiple posts from the database, you can use any of the possible keys of the schema as arguments.



# Test API


To start a docker server instance run:

 ```
sudo docker-compose up
```


Please find below some tests you can try after making the API work:

http://localhost:8000/scrap/?page=theartidote

The above request would scrap posts from the page “The Artidote”

http://localhost:8000/scrap/?page=theartidote&save=True

The above request would scrap and save the posts in the database

http://localhost:8000/post/?post_id=2657553427872738

The above request would find the post with the id 2657553427872738 in the database

http://localhost:8000/load/?page_id=742359879214163

This request would give you all posts of the page having page_id=742359879214163




