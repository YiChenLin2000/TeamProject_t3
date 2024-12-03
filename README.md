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
The test class used to mock interactions with Neo4j and verify that URLs are processed correctly. It ensures that methods such as saveUrlToGraph() and saveLinkToGraph() are being called properly.
