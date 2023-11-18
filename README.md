
1) Overview :
This project consists of a log ingestor system and a query interface for efficiently handling vast volumes of log data. The logs are ingested via an HTTP server running on port 3000, and the query interface provides full-text search and specific field filters.

3) System Design :
The system is built using python programming for both the log ingestor and query interface. The Flask framework is used for the HTTP server, and Elasticsearch is employed for efficient log storage and retrieval.

4) Features Implemented :
(a) Log Ingestor:
  • Mechanism to ingest logs in the specified format.
  • Scalability considerations for handling high volumes of logs.
  • Mitigation of potential bottlenecks, including I/O operations and database write speeds.

(b) Query Interface :
  • Web UI for full-text search across logs.
  • Filters based on level, message, resourceId, timestamp, traceId, spanId, commit, and metadata.parentResourceId.
  • Efficient and quick search results.

(c) Bonus Features :
  • Search within specific date ranges.
  • Utilization of regular expressions for search.
  • Ability to combine multiple filters.

4) How to Run the Project :
(a) Clone the repository: `git clone [repository_url]`
(b) Install dependencies: `[dependency_installation_command]`
(c) Run the log ingestor: `python log_ingestor.py`
(d) Run the query interface: `python log_query_interface.py`
(e) Access the query interface in a web browser at `http://localhost:3001`

5) Sample Queries :
Execute the sample queries for validation
