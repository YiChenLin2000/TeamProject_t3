# INFO6205 Web Crawler Project
This project implements a web crawler that collects and processes URLs, saving them into a Neo4j graph database. The crawler extracts and processes URLs from the web, follows links, and stores data on each visited page. The project uses the Jsoup library for HTML parsing and Neo4j for graph database management. 

## New Modules Added

### 1. final_project Folder (under src/main/java/edu/neu/coe/info6205)
Purpose: A new folder was created to organize the web crawling functionality, containing the core classes for crawling and benchmarking.

#### -- WebCrawler.java: 
This class is the main component of the crawler and is responsible for initiating the crawling process, handling URL extraction, and storing crawled data in the Neo4j database.

#### -- WebCrawlerBenchmark.java: 
This class was added to benchmark the performance of the web crawler, comparing different crawling strategies (e.g., different queue sizes, depth settings) to evaluate the efficiency of the crawler.

### 2. final_project_test Folder(under src/test/java/edu/neu/coe/info6205)

#### -- WebCrawlerTest.java: 
The test class used to mock interactions with Neo4j and verify that URLs are processed correctly. It ensures that methods are being called properly.

# WebCrawler.java Class
## Purpose:
The WebCrawler class is the core of the project. It manages the crawling process, starting from a given URL and recursively crawling up to a specified depth. It uses a priority queue to manage URLs based on their priority, which is calculated based on the URL content.

## Features:
#### 1. URL normalization to handle various URL formats.
#### 2. Crawling with breadth-first search (BFS) up to a configurable maximum depth (MAX_DEPTH).
#### 3. Priority-based URL processing using a priority queue.
#### 4. Links are extracted using the Jsoup library and filtered to ensure they are not already visited or invalid.
#### 5. URL data is saved in a Neo4j graph database, including URL, depth, and in-degree (number of incoming links).
## In-degree Handling: 
#### In our web crawler, we keep track of in-degree for each crawled URL in the Neo4j database. 
When a URL is processed and links are found, the method saveLinkToGraph() is invoked to create a relationship between the "from" URL and the "to" URL.

Each time a relationship is added, the in-degree for the target page (the "to" URL) is incremented by 1 in the database.

## Heuristic-based URL Prioritization:
#### In order to prioritize certain URLs over others during the crawling process, the WebCrawler class uses a heuristic approach.

Priority Calculation: URLs are assigned a priority score based on keywords present in the URL or its content.

Priority 1 (Highest Priority): URLs containing .edu and including the keyword “graduate”.

Priority 2 (Mid Priority): URLs related to admissions for Boston universities.

Priority 10 (Low Priority): URLs that are less important (e.g., help or policy pages).

Default Priority 5: For all other URLs.


