DSA *(Data Structures & Algorithms)* is a core area of study within Computer Science and is fundamental to almost any aspect of computer science and software development. The goal here is to analyze how use of different Algorithms and Data Structures within computer programs effects the efficiency of the program. 

*Efficiency* becomes extremely important when developing programs processing large amounts of data, this will be the main concept kept in our mind as we study DSA.

> [!IMPORTANT] 
> **Measuring Efficiency & Big-O**
> The main way we express the *efficiency* of the program is via [[Time Complexity]] analysis. Big-O notation focuses only how the performance of different Data Structures and Algorithms *scales with magnitude.* As such is not the complete picture, however still a very important core concept to understand.

https://visualgo.net/en

--- 
#### Data Structures

**Linear**
[[Basic Array(s)]]
- [[Hash Table(s)]]
[[Linked List(s)]]
- [[Stack(s)]]
- [[Queue(s)]]

**Hierarchical**
[[Trees]]
- [[Binary-Search Tree(s)]]
	- [[AVL Trees]]
	- [[Red/Black Trees]]

---
#### Algorithms
Sorting: Inefficient ~ O(n$^2$)
- [[Insertion Sort]]
- [[Bubble Sort]]
- [[Selection Sort]]

Sorting: Efficient ~ O(n * log(n))
- [[Quick Sort]]
- [[Merge Sort]]

Searching:
- [[Linear Search]]
- [[Binary Search]]

- [[Cooperative Perception Algorithms]]
---
#### Examples of Data Sizes In Practice
These examples will be used in our study of different Data Structures and Algorithms.
*Last Updated:10/11/2025*
#### Web Graph Data (Google)
- **Websites indexed by google:** ~130 trillion  
- **Average Links:** ~100/page  
	- **Graph Edges:** ~10^16  

- *Source:* [Zyppy – How Big Is Google’s Index?](https://zyppy.com/seo/google-index-size/)
#### IoT/Sensor Data
- **Active Devices:** ~15 billion  
- **Data Generated:** 80 zettabyte(s)  

- *Source:* [IDC Global DataSphere Forecast 2025](https://www.idc.com/getdoc.jsp?containerId=US51042323)
#### Social Media (Facebook)
- **User Accounts:** ~3 billion  
- **Friend Connections:** ~400 billion  
- **Posts:** ~300 billion/day  

- **Storage Scale:** Multiple petabyte(s)  
- *Source:* [Meta Q1 2025 Earnings Report](https://investor.fb.com/)
#### E-Commerce (Amazon)
- **Product Listings:** ~500 million  
- **Reviews:** ~10 billion  
- **Transactions:** ~1.6 million/hour

- **Storage Scale:** Multiple terabyte(s)  
- *Source:* [Amazon Science Blog – AI & Data at Scale](https://www.amazon.science/)
#### Map/Geo Data (OpenStreetMap)
- **Intersections/Points (nodes):** ~8.5 billion  
- **Roads (ways):** ~1 billion  

- **File Size:** 120–150 gigabyte(s)  
- *Source:* [OpenStreetMap Wiki – Stats](https://wiki.openstreetmap.org/wiki/Stats)
#### Stock Market Data
- **Stocks:** ~6,000  
- **Trades:** ~millions/sec  
- **Records:** ~10 billion trades/day  

- **Storage Growth:** ~2 terabyte(s)/day  
- *Source:* [Nasdaq Market Data Products](https://www.nasdaq.com/solutions/market-data-products)
#### Natural Language Data
- **Wikipedia:** ~6.8 million articles  
- **Common Web Crawl:** ~250 terabyte(s)  

- *Source:* [Common Crawl Foundation Data](https://commoncrawl.org/the-data/)
#### DNA/Genome Data
- **Human genome:** ~3.2 billion base pairs  
- *Source:* [NCBI Human Genome Resources](https://www.ncbi.nlm.nih.gov/genome/)

>[!NOTE]
>In each of these domains, the scale of data directly influences which data structures and algorithms are preferable in practice. Understanding efficiency through Big-O notation is essential to designing systems that can handle data at these magnitudes, and each domain has there own aspects that make it unique

---
#### Resources
- https://www.geeksforgeeks.org/