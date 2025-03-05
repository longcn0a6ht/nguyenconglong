**Possible issue 1: Incorrect NGINX settings causing high memory usage.**

**Steps to Troubleshoot**

Check nginx Configuration:

Check value of the settings like worker_connections and worker_rlimit_nofile. Ensure these values are not too high for your traffic.

Ex:

grep worker_connections /etc/nginx/nginx.conf

grep worker_rlimit_nofile /etc/nginx/nginx.conf

Check current connections:

netstat -an | grep ESTABLISHED | wc -l

Compare this with the configured worker_connections value on /etc/nginx/nginx.conf file.

**Check Logs:**

tail -f /var/log/nginx/error.log

journalctl -fu nginx

**Possible Causes:**
Incorrect NGINX settings causing high memory usage.


**Impacts:**
High memory usage can slow down or crash the server.
Requests may fail due to insufficient resources.

**Recovery Steps:**
Adjust NGINX settings based on traffic:

sudo systemctl restart nginx


**Possible Issue 2: Memory Leaks or Inefficient Resource Handling**

**Steps to Troubleshoot**

Run the following command to see which processes are using memory.

htop
ps -aux

Check if NGINX workers are consuming too much memory.

Check journal log:

journalctl -fu nginx

Inspect Keepalive Settings:

grep keepalive /etc/nginx/nginx.conf

Ensure they are not causing too many open connections.

**Possible Causes:**
Keepalive settings causing too many open connections.
Memory leaks in NGINX or its modules.

**Impacts:**
VM runs out of memory, causing service interruptions.

Increased latency for users.

**Recovery Steps:**

Adjust keepalive settings.

Disable caching or compression if necessary.

Restart nginx service:

sudo systemctl restart nginx
