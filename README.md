# DSA Pattern Recognition Cheat Sheet
 
> **How to use this:** Read the problem, spot the *signal* in the left column, jump straight to the *pattern*. Stop guessing, start pattern-matching.
 
---
 
## 1. Arrays / Subarrays
 
| Signal in problem | Pattern | Key idea |
|---|---|---|
| Subarray/substring with sum/condition, **contiguous**, all positive | **Sliding Window (fixed/variable)** | Expand right, shrink left when condition breaks |
| "Longest/shortest subarray with at most K distinct / sum ≤ K" | **Variable Sliding Window** | Two pointers, shrink while invalid |
| Subarray sum = K (can have negatives) | **Prefix Sum + HashMap** | `map[prefixSum - K]` |
| Max/min of every window of size K | **Monotonic Deque** | Deque stores indices, pop useless ends |
| Find pair/triplet with target sum, **sorted array** | **Two Pointers (opposite ends)** | left++/right-- based on sum vs target |
| 3Sum/4Sum | **Sort + Two Pointers + fix outer loops** | Skip duplicates |
| Next greater/smaller element | **Monotonic Stack** | Stack keeps decreasing/increasing order |
| Find missing/duplicate number in range [1,n] | **Cyclic Sort / XOR / Sum formula** | Index = value placement |
| Merge overlapping intervals | **Sort by start + linear merge** | Compare `curr.start` vs `prev.end` |
| Kth largest/smallest, top K elements | **Heap (size K)** | Min-heap for Kth largest, max-heap for Kth smallest |
| Median of stream | **Two Heaps (max-heap left, min-heap right)** | Balance sizes |
| Rotated sorted array search | **Modified Binary Search** | Check which half is sorted |
| "Search in sorted/rotated/answer space" | **Binary Search on Answer** | `feasible(mid)` monotonic check |
| Product/sum of array except self | **Prefix × Suffix arrays** | Two passes |
| In-place array manipulation, O(1) space | **Cyclic Sort / Index marking (negate values)** | |
 
---
 
## 2. Strings
 
| Signal | Pattern |
|---|---|
| Anagram / permutation check | **Frequency array/HashMap (size 26)** |
| Longest substring without repeating chars | **Sliding Window + HashSet/Map** |
| Palindrome check/count | **Two Pointers** or **Expand Around Center** |
| Longest palindromic substring | **Expand Around Center** or **DP** |
| Pattern matching (needle in haystack) | **KMP / Rabin-Karp / Z-function** |
| Word break / can form string from dict | **DP + HashSet** |
| Group anagrams | **HashMap<sortedString, List>** |
| Min window substring containing all chars of T | **Sliding Window + char count map** |
 
---
 
## 3. Linked List
 
| Signal | Pattern |
|---|---|
| Detect cycle / find middle | **Fast & Slow Pointers (Floyd's)** |
| Find cycle start / duplicate number (array as list) | **Floyd's Cycle → reset one pointer to head** |
| Reverse list / reverse in groups of K | **Iterative pointer reversal (prev/curr/next)** |
| Merge K sorted lists | **Min-Heap** or **Divide & Conquer merge** |
| Nth node from end | **Two Pointers (gap of N)** |
| Check palindrome list | **Fast/slow to find mid + reverse second half** |
 
---
 
## 4. Trees
 
| Signal | Pattern |
|---|---|
| Level-by-level processing | **BFS (Queue)** |
| Path sum / root-to-leaf | **DFS + backtracking, carry running sum** |
| Diameter / height / balanced check | **Post-order DFS returning height** |
| LCA (Lowest Common Ancestor) | **Recursive DFS (return node when found on both sides)** |
| Serialize/Deserialize | **Preorder DFS with null markers, or BFS** |
| BST validate / kth smallest | **Inorder Traversal (gives sorted order)** |
| Construct tree from traversals | **Recursion + index map (HashMap for inorder)** |
| Vertical order / boundary traversal | **BFS with (row,col) tracking or DFS with column map** |
| Max path sum (any node to any node) | **DFS returning max single-branch gain + global max update** |
 
---
 
## 5. Graphs
 
| Signal | Pattern |
|---|---|
| Shortest path, **unweighted** | **BFS** |
| Shortest path, **weighted, non-negative** | **Dijkstra (Priority Queue)** |
| Shortest path, **negative weights** | **Bellman-Ford** |
| All-pairs shortest path | **Floyd-Warshall** |
| Connected components / islands | **DFS/BFS flood fill** |
| Cycle detection (undirected) | **DFS with parent tracking / Union-Find** |
| Cycle detection (directed) | **DFS with recursion stack (colors: white/gray/black)** |
| Course schedule / dependency ordering | **Topological Sort (Kahn's BFS or DFS)** |
| Minimum Spanning Tree | **Kruskal (Union-Find) or Prim (Heap)** |
| Group/merge related items, dynamic connectivity | **Union-Find (Disjoint Set)** |
| Grid problems (islands, rotting oranges, flood fill) | **BFS/DFS on grid, treat cell as node** |
| Word Ladder / shortest transformation | **BFS with implicit graph (word variations)** |
| Bipartite check | **BFS/DFS 2-coloring** |
 
---
 
## 6. Dynamic Programming
 
| Signal | Pattern |
|---|---|
| "Count ways" / "min/max cost to reach" | **1D/2D DP, dp[i] built from dp[i-1], dp[i-2]...** |
| 0/1 Knapsack (pick or skip, limited capacity) | **DP table [items][capacity], each item used once** |
| Unbounded Knapsack (coin change, rod cutting) | **DP where item can repeat** |
| Longest Common Subsequence / Edit Distance | **2D DP over two strings** |
| Longest Increasing Subsequence | **DP O(n²) or Binary Search O(n log n)** |
| Partition into two equal subsets | **Subset-sum DP (boolean dp[sum])** |
| Matrix path (min/max path sum, unique paths) | **2D grid DP** |
| Interval DP (burst balloons, matrix chain mult.) | **dp[i][j] over ranges, split point k** |
| Bitmask DP (TSP, assign tasks to workers) | **dp[mask][i], mask = subset visited** |
| Tree DP | **DFS returning dp values from children** |
| Digit DP (count numbers with property ≤ N) | **dp[pos][tight][state]** |
| State machine (buy/sell stock with cooldown/fee) | **dp[day][state] transitions** |
 
---
 
## 7. Backtracking
 
| Signal | Pattern |
|---|---|
| All permutations/combinations/subsets | **Backtracking: choose → recurse → un-choose** |
| N-Queens, Sudoku, constraint placement | **Backtracking + pruning/validity check** |
| Combination sum (reuse allowed/not allowed) | **Backtracking with start index (+1 if no reuse)** |
| Generate valid parentheses | **Backtracking with open/close counters** |
| Word search in grid | **DFS + backtracking with visited marking** |
 
---
 
## 8. Greedy
 
| Signal | Pattern |
|---|---|
| Interval scheduling (max non-overlapping) | **Sort by end time, pick greedily** |
| Minimum platforms / meeting rooms | **Sort start & end separately, sweep** |
| Jump game / min jumps to reach end | **Track farthest reachable index** |
| Gas station / can complete circuit | **Track running total + reset start point** |
| Huffman encoding / task scheduling | **Greedy + Heap** |
| Assign cookies / fractional knapsack | **Sort both arrays, greedy match** |
 
---
 
## 9. Binary Search (beyond sorted array)
 
| Signal | Pattern |
|---|---|
| "Minimize the maximum" / "maximize the minimum" | **Binary Search on Answer + feasibility check** |
| Search in infinite/unknown-size array | **Exponential/Galloping search then binary search** |
| Find peak element | **Binary search using neighbor comparison** |
| Allocate books/painters/ship capacity (min-max) | **Binary search on answer space, greedy feasibility** |
 
---
 
## 10. Stack / Queue Specific
 
| Signal | Pattern |
|---|---|
| Valid parentheses / matching brackets | **Stack** |
| Next greater/smaller, stock span | **Monotonic Stack** |
| Sliding window max | **Monotonic Deque** |
| Design LRU/LFU cache | **HashMap + Doubly Linked List** |
| Evaluate expression (infix/postfix) | **Stack-based evaluation / Shunting Yard** |
| Implement queue using stacks / min-stack | **Two stacks (aux stack tracks min)** |
 
---
 
## 11. Bit Manipulation
 
| Signal | Pattern |
|---|---|
| Find single number among duplicates | **XOR all elements** |
| Count set bits | **Brian Kernighan's `n & (n-1)` in loop** |
| Subsets of a set | **Bitmask iterate 0 to 2^n - 1** |
| Power of two check | **`n & (n-1) == 0`** |
 
---
 
## 12. Quick Trigger Words → Pattern
 
- **"contiguous subarray/substring" + sum/length condition** → Sliding Window / Prefix Sum
- **"sorted array" + pair/triplet** → Two Pointers
- **"kth largest/smallest / top K"** → Heap
- **"all combinations/permutations/subsets"** → Backtracking
- **"minimum/maximum number of ways"** → DP
- **"shortest path"** → BFS/Dijkstra
- **"connected components / islands"** → DFS/BFS/Union-Find
- **"scheduling/interval/non-overlap"** → Greedy + Sort
- **"next greater/smaller element"** → Monotonic Stack
- **"in a stream / online"** → Heap or Two Heaps
- **"minimize the maximum" / "capacity to ship"** → Binary Search on Answer
- **"union of groups / friend circles"** → Union-Find
---
 
## 13. Complexity Cheat Reference
 
| Data Structure | Access | Search | Insert | Delete |
|---|---|---|---|---|
| Array | O(1) | O(n) | O(n) | O(n) |
| HashMap | - | O(1)* | O(1)* | O(1)* |
| Sorted Array (Binary Search) | O(1) | O(log n) | O(n) | O(n) |
| BST (balanced) | O(log n) | O(log n) | O(log n) | O(log n) |
| Heap | O(1) top | O(n) | O(log n) | O(log n) |
| Linked List | O(n) | O(n) | O(1)** | O(1)** |
 
\* amortized, \** with pointer
 
---
 
### One-line mental checklist before coding
1. Is it **contiguous**? → sliding window / prefix sum.
2. Is it **sorted**? → two pointers / binary search.
3. Is it **"count ways / optimize"**? → DP.
4. Is it **graph/grid connectivity**? → BFS/DFS/Union-Find.
5. Is it **"all possible ___"**? → Backtracking.
6. Is it **"next/previous greater-smaller"**? → Monotonic stack.
7. Is it **top-K / streaming**? → Heap.



------------------------------//------------------------------------------------------------------------


# System Design Cheat Sheet — "Need X → Use Y"

A quick-reference mapping common system needs to the tech usually used for them in real-world, large-scale applications.

---

## 1. Client ↔ Server Entry Points

| Need | Common Tech |
|---|---|
| Load balancing traffic | Nginx, HAProxy, AWS ELB/ALB, Envoy |
| API Gateway (routing, auth, rate limit) | Kong, AWS API Gateway, Apigee, Envoy |
| DNS / global traffic routing | Route53, Cloudflare DNS |
| CDN (static assets, images, video) | Cloudflare, Akamai, AWS CloudFront, Fastly |
| Reverse proxy / TLS termination | Nginx, Envoy, Traefik |

---

## 2. Core Backend

| Need | Common Tech |
|---|---|
| Web/app servers | Node.js (Express/NestJS), Spring Boot (Java), Django/FastAPI (Python), Go (Gin/Fiber) |
| Microservices communication (sync) | REST, gRPC |
| Service discovery | Consul, Eureka, Kubernetes DNS |
| API contracts | OpenAPI/Swagger, Protobuf (for gRPC) |
| Background/async jobs | Celery, Sidekiq, BullMQ, Temporal |

---

## 3. Messaging / Async Communication

| Need | Common Tech |
|---|---|
| Event streaming / high-throughput pub-sub | **Apache Kafka**, Redpanda |
| Simple task queues | RabbitMQ, AWS SQS, BullMQ |
| Pub/Sub for real-time fan-out | Redis Pub/Sub, Google Pub/Sub, NATS |
| Event-driven architecture backbone | Kafka + Kafka Streams / Flink |
| Delayed/scheduled jobs | SQS with delay, Redis + BullMQ, cron + queue |

**Pattern:** `Producer service → Kafka topic → Consumer service(s)` for decoupling, buffering spikes, and enabling multiple downstream consumers (analytics, notifications, audit log) off a single event.

---

## 4. Caching

| Need | Common Tech |
|---|---|
| In-memory key-value cache | **Redis**, Memcached |
| Application-level cache (DB query result cache) | Redis (with TTL) |
| CDN edge caching | Cloudflare, CloudFront |
| Local/in-process cache | Caffeine (Java), lru-cache (Node) |
| Session store | Redis |
| Rate limiting counters | Redis (INCR + TTL), Redis + Lua scripts |
| Distributed lock | Redis (Redlock), Zookeeper |

**Pattern:** `Client → App Server → Redis (cache-aside) → DB (on cache miss)`

---

## 5. Databases

| Need | Common Tech |
|---|---|
| Relational / transactional data | PostgreSQL, MySQL |
| High write-throughput, flexible schema | MongoDB, Cassandra |
| Wide-column, huge scale, time-series-ish | Cassandra, ScyllaDB, HBase |
| Key-value at massive scale | DynamoDB, Redis |
| Graph relationships | Neo4j, Amazon Neptune |
| Time-series data (metrics, IoT) | InfluxDB, TimescaleDB, Prometheus |
| Search / full-text search | **Elasticsearch**, OpenSearch, Algolia |
| Analytics / OLAP / data warehouse | Snowflake, BigQuery, Redshift, ClickHouse |
| Object/blob storage (files, images, videos) | AWS S3, GCS, MinIO |

**Pattern:** Read-heavy → add read replicas. Write-heavy/huge scale → shard/partition. Polyglot persistence is normal (Postgres for core data + Elasticsearch for search + Redis for cache).

---

## 6. Data Consistency & Scaling Patterns

| Need | Common Tech / Pattern |
|---|---|
| DB replication (read scaling) | Primary-replica (Postgres streaming replication, MySQL replicas) |
| DB sharding (write scaling) | Vitess, Citus (Postgres), app-level sharding |
| Distributed transactions | Saga pattern, 2-phase commit (rare), outbox pattern |
| Strong consistency across services | Distributed consensus — Zookeeper, etcd, Raft |
| Eventual consistency | Event-driven sync via Kafka + CQRS |
| CQRS (separate read/write models) | Write to Postgres, project to Elasticsearch/Redis for reads |

---

## 7. Search

| Need | Common Tech |
|---|---|
| Full-text search, filters, facets | Elasticsearch, OpenSearch |
| Typo-tolerant instant search (e.g. e-commerce) | Algolia, Meilisearch |
| Vector/semantic search (AI/embeddings) | Pinecone, Weaviate, Milvus, pgvector |

---

## 8. Real-Time Features

| Need | Common Tech |
|---|---|
| Real-time chat / live updates | WebSockets (Socket.io), Server-Sent Events |
| Presence / online status | Redis (with TTL keys) |
| Notifications (push) | Firebase Cloud Messaging, APNs, OneSignal |
| Live collaborative editing | WebSockets + CRDT/OT (e.g. Yjs) |
| Video/audio streaming | WebRTC, Agora, Twilio |

---

## 9. Observability

| Need | Common Tech |
|---|---|
| Metrics collection | Prometheus |
| Dashboards | Grafana |
| Centralized logging | ELK Stack (Elasticsearch, Logstash, Kibana), Loki |
| Distributed tracing | Jaeger, Zipkin, OpenTelemetry |
| Error tracking | Sentry, Rollbar |
| Alerting | Prometheus Alertmanager, PagerDuty, Opsgenie |

---

## 10. Security & Auth

| Need | Common Tech |
|---|---|
| Authentication | OAuth2, JWT, Keycloak, Auth0, Firebase Auth |
| Authorization | RBAC/ABAC, OPA (Open Policy Agent) |
| Secrets management | HashiCorp Vault, AWS Secrets Manager |
| API rate limiting / abuse prevention | Redis-based limiter, Kong plugins, Cloudflare |
| DDoS protection | Cloudflare, AWS Shield |

---

## 11. Infrastructure / Deployment

| Need | Common Tech |
|---|---|
| Containerization | Docker |
| Orchestration | Kubernetes (K8s), ECS |
| CI/CD | GitHub Actions, Jenkins, GitLab CI, ArgoCD |
| Infrastructure as Code | Terraform, Pulumi, CloudFormation |
| Service mesh | Istio, Linkerd |
| Config management | Consul, etcd, K8s ConfigMaps |

---

## 12. Common End-to-End Flow (Typical Web App)

```
Client
  │
  ▼
CDN (static assets) ── Cloudflare / CloudFront
  │
  ▼
Load Balancer ── Nginx / ALB
  │
  ▼
API Gateway ── Kong / AWS API Gateway
  │
  ▼
App Servers (stateless) ── Node.js / Spring Boot / Django
  │
  ├──► Cache (read-through) ── Redis
  ├──► Primary DB ── PostgreSQL / MySQL
  ├──► Search index ── Elasticsearch
  ├──► Async events ── Kafka → Consumers (email service, analytics, audit log)
  └──► Object storage ── S3 (images, files)

Observability sidecar throughout: Prometheus + Grafana + ELK + Jaeger
```

---

## 13. Quick "Which One Do I Pick" Rules of Thumb

- **Need to decouple services / handle spikes / multiple consumers of one event** → Kafka (or RabbitMQ/SQS if simpler queueing is enough)
- **Need to speed up repeated reads / reduce DB load** → Redis cache-aside
- **Need full-text or fuzzy search** → Elasticsearch
- **Need strong ACID transactions** → PostgreSQL/MySQL
- **Need massive horizontal write scale, flexible schema** → Cassandra/DynamoDB/MongoDB
- **Need real-time bidirectional updates** → WebSockets + Redis pub/sub
- **Need to store files/images/videos** → S3-compatible object storage + CDN in front
- **Need to know what's happening in prod** → Prometheus + Grafana + ELK + Sentry

---

*Rule of thumb: don't reach for Kafka/Cassandra/Elasticsearch on day one unless you actually have the scale problem — Postgres + Redis + a simple queue covers a huge percentage of real systems.*
