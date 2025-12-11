# CKAD Mock Exam — Application Design & Build (12 Questions)

**Instructions (same style as the actual exam):**

* Perform all tasks using **kubectl**.
* Unless otherwise specified, work in the **default** namespace.
* Use the shortest possible commands and YAML manifests.
* Assume an empty cluster unless otherwise stated.

## 1. Create a Pod with Environment Variables

Create a Pod named **app-env** using the image `nginx:1.25`.
Set the environment variables:

* `APP_MODE=production`
* `APP_VERSION=1.0`

Verify that the Pod is running.

## 2. ConfigMap-Based Application Configuration

Create a ConfigMap named **color-config** with:

```
COLOR=blue
LEVEL=high
```

Then create a Deployment named **cm-demo** (1 replica) using image `busybox` with a command that prints these env vars every 5 seconds:

```
command: ["sh", "-c", "while true; do echo $COLOR $LEVEL; sleep 5; done"]
```

Inject the values through environment variables using the ConfigMap.


## **3. Secret Injection Into a Pod

Create a Secret named **db-secret** with:

```
username=admin
password=S3cr3tPwd
```

Create a Pod **db-client** (image: `busybox`) that mounts this Secret at `/etc/creds`.

## 4. Multi-Container Pod

Create a Pod named **sidecar-demo** with:

* Main container: `nginx`
* Sidecar container: `busybox`
* Shared volume: `/var/log/app`
* Sidecar should output a line every 3 seconds into `/var/log/app/notes.txt`

## 5. Probes: Liveness & Readiness

Create a Deployment named **probe-app** using image `nginx`.
Configure:

* **Liveness probe**: HTTP GET `/healthz` on port 80
* **Readiness probe**: HTTP GET `/ready` on port 80
* Both should check every **5 seconds**.

## 6. Jobs & Backoff

Create a Job **math-job** that runs:

```
echo $((3*7))
```

Ensure:

* Job completes successfully
* Restart policy = Never

## 7. CronJob Scheduling

Create a CronJob **log-cleaner** that:

* Runs every minute
* Executes:
  `rm -rf /tmp/*`

Use image `busybox`.

## 8. Expose an Application (Service)

Create a Deployment **web-svc** using image `nginx` with **3 replicas**.
Expose it using a **ClusterIP** service named **web-svc** on port 80.

## 9. Namespaces & Context Switching

Create a namespace **team-a**.

Deploy a Pod **team-pod** (`nginx`) inside **team-a**.

Switch your kubectl context to permanently use namespace **team-a**.

## 10. Resource Requirements

Create a Pod **mem-limit** using image `nginx` with:

* Requests:

  * CPU: `100m`
  * Memory: `64Mi`
* Limits:

  * CPU: `200m`
  * Memory: `128Mi`

## 11. Labels, Selectors & Patching

Create a Pod **label-me** with label:

```
role=frontend
```

Later, patch it to add:

```
tier=prod
```

Finally, list all Pods with both labels.


## 12. Init Container

Create a Pod **init-demo** with:

* Init container: `busybox`
  Command: `echo initializing && sleep 3`
* Main container: `nginx`

Init should complete before the main container starts.
