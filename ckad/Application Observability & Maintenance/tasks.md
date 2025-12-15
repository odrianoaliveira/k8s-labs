## Mock Exam – Application Observability & Maintenance (CKAD)

### **Task 1 – Inspect Pod Health and Logs**

**Namespace:** `observability`

1. A Pod named ` is running in the `observability` namespace.
2. Inspect the Pod and determine:

   * The container restart count
   * Whether the Pod is Ready
3. Retrieve the **last 20 lines** of logs from the main container.
4. Save the logs to `/tmp/api-pod.log`.

✔️ **Skills tested**

* `kubectl describe`
* `kubectl logs`
* Understanding Pod status & restarts

---

### **Task 2 – Debug a Failing Pod**

**Namespace:** `maintenance`

1. A Pod named `payment-service` is in `CrashLoopBackOff`.
2. Identify the reason for the failure using logs.
3. Fix the issue by:

   * Updating the container command to sleep for 3600 seconds
4. Ensure the Pod is running and stable.

✔️ **Skills tested**

* CrashLoopBackOff debugging
* Editing live resources
* Container command overrides

---

### **Task 3 – Add Liveness and Readiness Probes**

**Namespace:** `probes`

1. A Deployment named `web-app` exists with **no health probes**.
2. Add:

   * A **livenessProbe** using HTTP GET on `/healthz`, port `8080`
   * A **readinessProbe** using HTTP GET on `/ready`, port `8080`
3. Set:

   * `initialDelaySeconds: 10`
   * `periodSeconds: 5`
4. Apply the changes and verify the Pod becomes Ready.

✔️ **Skills tested**

* Probes configuration
* Deployment updates
* Rolling updates

---

### **Task 4 – Monitor Resource Usage**

**Namespace:** `metrics`

1. Identify the Pod consuming the **most CPU** in the namespace.
2. Output the result to `/tmp/high-cpu.txt`.

✔️ **Skills tested**

* `kubectl top pod`
* Basic metrics interpretation

📌 *Assume metrics-server is installed (as in the real exam).*

---

### **Task 5 – Fix a Misconfigured Environment Variable**

**Namespace:** `config`

1. A Pod named `backend` fails because it expects an environment variable `APP_MODE=production`.
2. Update the Pod (or its controller) to define this variable.
3. Verify the Pod starts successfully.

✔️ **Skills tested**

* Env var troubleshooting
* Pod vs controller awareness
* Config-driven failures

---

### **Task 6 – Debug a Service Connectivity Issue**

**Namespace:** `networking`

1. A Service named `frontend-svc` is not routing traffic to Pods.
2. Identify the issue and fix it.

   * Hint: Check **labels and selectors**
3. Verify endpoints are correctly populated.

✔️ **Skills tested**

* Service selectors
* Label consistency
* `kubectl get endpoints`

---

### **Task 7 – Perform a Rolling Restart**

**Namespace:** `maintenance`

1. Perform a rolling restart of the Deployment `user-api`.
2. Confirm:

   * No downtime (Pods replaced gradually)
   * All Pods are running after the restart

✔️ **Skills tested**

* `kubectl rollout restart`
* Rollout status inspection

---

### **Task 8 – Investigate Events**

**Namespace:** `observability`

1. Identify recent warning or error events in the namespace.
2. Find which object generated the most recent warning.
3. Save the event details to `/tmp/events.txt`.

✔️ **Skills tested**

* Kubernetes events
* Cluster troubleshooting workflow

