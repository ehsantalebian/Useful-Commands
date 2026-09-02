# 🛠️ Jira Infrastructure Management Runbook

---

### 🔵 Section 1: Port Configuration Discovery

* **Check Configured Tomcat Connector Port:**
  ```bash
  grep -E "<Connector|port=" /data/atlassian/jira/conf/server.xml
  ```

---

### 🟩 Section 2: Quick Node Health Check

* **Query Local Node Health Endpoint:**
  ```bash
  curl -s http://localhost:8080/status | jq .
  ```
* **Expected Healthy Response:**
  ```json
  {
    "state": "RUNNING",
    "alive": true
  }
  ```

---

### 🚀 Section 3: Service & Process Lifecycle Control

* **Start Jira Service:**
  ```bash
  /data/atlassian/jira/bin/start-jira.sh
  ```

* **Gracefully Stop Jira Service:**
  ```bash
  /data/atlassian/jira/bin/stop-jira.sh
  ```

* **Check Systemd Service Status:**
  ```bash
  systemctl status jira
  ```

* **Identify Active Jira Process ID (PID):**
  ```bash
  pgrep -f "atlassian.*jira"
  ```

* **Emergency Force-Kill (Hung Node Only):**
  ```bash
  kill -9 $(pgrep -f "atlassian.*jira")
  ```

---

### 📙 Section 4: Real-Time Log Streaming

* **Tail Active Application Logs (Runtime Errors & App Events):**
  ```bash
  tail -f /data/atlassian/application-data/jira/log/atlassian-jira.log
  ```

* **Tail Web Server & Startup Logs (Tomcat Crashes & JVM Locks):**
  ```bash
  tail -f /data/atlassian/jira/logs/catalina.out
  ```

---

### 🟥 Section 5: Log Diagnostics & Error Searching

* **Search Recent Exceptions & Fatal Errors:**
  ```bash
  grep -iE "ERROR|FATAL|Exception" /data/atlassian/application-data/jira/log/atlassian-jira.log | tail -n 50
  ```

* **Search Startup Crashes & Out-of-Memory (OOM) Errors:**
  ```bash
  grep -iE "OutOfMemoryError|SEVERE|Java heap space" /data/atlassian/jira/logs/catalina.out | tail -n 30
  ```

* **Inspect Garbage Collection (GC) Stop-The-World Pauses:**
  ```bash
  grep -i "Full GC" /data/atlassian/jira/logs/atlassian-jira-gc-*.log | tail -n 20
  ```

---

### ⚡ Section 6: Cluster & Network Port Diagnostics

* **Verify Node Health Endpoint:**
  ```bash
  curl -s http://localhost:8080/status | jq .
  ```

* **Inspect Active Java Listening Ports (HTTP & Hazelcast 40001):**
  ```bash
  ss -tulpn | grep java
  ```

* **Verify Active HTTP Connector Port in Configuration:**
  ```bash
  grep -E '<Connector.*port=' /data/atlassian/jira/conf/server.xml
  ```

* **Check Cluster Node Join & Synchronization Logs:**
  ```bash
  grep -i "cluster" /data/atlassian/application-data/jira/log/atlassian-jira.log | tail -n 30
  ```

---

### 🧠 Section 7: JVM Performance & Thread Analysis

* **Verify Heap Limits & Active GC Flags:**
  ```bash
  ps aux | grep java | grep -E "Xms|Xmx|UseG1GC"
  ```

* **Generate Java Thread Dump (Diagnose 100% CPU or Thread Locks):**
  ```bash
  jstack $(pgrep -f "atlassian.*jira") > /tmp/jira_thread_dump_$(date +%F_%H%M).txt
  ```

* **Inspect Memory Allocation Histogram (Top Live Objects):**
  ```bash
  jmap -histo:live $(pgrep -f "atlassian.*jira") | head -n 25
  ```

---

### 🟪 Section 8: NFS Storage & Index Disk Monitoring

* **Check NFS Shared Storage Space & Mount Status:**
  ```bash
  df -hT /nfs-data/sharedhome
  ```

* **Verify Active System NFS Mount Parameters:**
  ```bash
  mount | grep nfs
  ```

* **Check Shared Lucene Index Snapshot Disk Usage:**
  ```bash
  du -sh /nfs-data/sharedhome/caches/indexes/snapshots/*
  ```

* **Check Local Lucene Index Disk Usage per Node:**
  ```bash
  du -sh /data/atlassian/application-data/jira/caches/indexes/
  ```

---

### 🟨 Section 9: Network & Database Connectivity

* **Test TCP Port Connectivity to Alibaba Cloud MySQL RDS:**
  ```bash
  nc -zv rm-gs5464il85rao7bse.mysql.singapore.rds.aliyuncs.com 3306
  ```

* **Inspect Active Connection Pool & Database Endpoint Configuration:**
  ```bash
  cat /data/atlassian/application-data/jira/dbconfig.xml | grep -E "pool-min-size|pool-max-size|url"
  ```
