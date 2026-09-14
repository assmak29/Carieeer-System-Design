# System Architecture – Project Flow

Here is a quick walkthrough of how our system works and why we chose each component in the architecture.

## 1. Users and System Entry

Our system mainly serves two types of users: **HRs** and **Candidates**.

Considering our expected scale of around **1.3 billion users**, relying on a single server would create a major bottleneck and could eventually lead to system failure under heavy traffic.

To handle this large number of requests, we use **multiple servers** behind a **Load Balancer**.

The Load Balancer distributes incoming requests across the available servers, helping us achieve better **scalability, availability, and performance**.

---

## 2. API Gateway

After the Load Balancer, requests pass through the **API Gateway**.

Since different users have different permissions and roles, the API Gateway acts as the main entry point for our services.

It is responsible for handling things such as:

* Authentication
* Authorization
* Request routing
* Access control

For example, an HR should have access to candidate-related operations, while a candidate should only have access to the operations allowed for their role.

---

## 3. Microservices

Since our system contains different business domains, we decided to separate them into independent services.

Our main services are:

* **User Service** – handles users and their profiles.
* **Job Service** – manages job postings and job-related operations.
* **Application Service** – handles job applications and their status.
* **Notification Service** – manages notifications sent to users.

Separating these responsibilities allows each service to be developed, deployed, and scaled independently.

---

## 4. Search Engine

Now let's look at the searching process.

Suppose an HR wants to search for candidates. The request needs to reach our **Search Engine**.

Similarly:

* A candidate may search for jobs.
* An HR may search for candidates.
* Job postings need to be searchable as well.

Therefore, candidates, jobs, and applications can all be indexed in the Search Engine to provide fast and efficient searching.

Whenever the underlying data is updated, the changes are reflected in the main database and the corresponding search index can be updated accordingly.

---

## 5. Object Storage – Amazon S3

Some types of data are not suitable for storing directly inside a relational database.

For example, a candidate may have:

* A CV
* A profile picture
* Other uploaded files or media

Instead of storing these large files directly in the database, we use **Amazon S3 (Object Storage)**.

The database stores the relevant metadata or file URL, while the actual file is stored in S3.

This approach keeps the database smaller and makes file storage more scalable.

---

## 6. Caching – Redis

Jobs are expected to be one of the most frequent operations.Redis is implemented to cache job data. This significantly reduces the load on the primary SQL database and minimizes latency.
