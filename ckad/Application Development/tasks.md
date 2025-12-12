
## Mock Exam – Application Deployment (CKAD)

### Task 1: Create and Scale a Deployment

Create a Deployment named **`web-app`** with the following requirements:

* Namespace: `app-deploy`
* Image: `nginx:1.25`
* Replicas: `3`
* Container port: `80`

After creation:

* Scale the Deployment to **5 replicas**
* Verify all Pods are running

🔍 *Skills tested:* Deployment creation, scaling, namespaces

### Task 2: Rolling Update with Zero Downtime

Update the `web-app` Deployment created earlier:

* Change the image to `nginx:1.26`
* Ensure:

  * Max unavailable Pods during update: `1`
  * Max surge Pods during update: `1`

Confirm that the rollout completes successfully.

🔍 *Skills tested:* Rolling update strategy, Deployment configuration

### Task 3: Rollback a Failed Deployment

A bad image update was applied to `web-app` and Pods are failing.

Your tasks:

1. Inspect the rollout history
2. Roll back to the **previous stable revision**
3. Verify the Deployment is healthy again

🔍 *Skills tested:* Rollout history, rollback, troubleshooting

### Task 4: Expose a Deployment

Expose the `web-app` Deployment:

* Service name: `web-app-svc`
* Type: `ClusterIP`
* Port: `80`
* TargetPort: `80`

Confirm the Service endpoints are correctly populated.

🔍 *Skills tested:* Service creation, Deployment-to-Service wiring

### Task 5: Blue-Green Style Deployment

Create a second Deployment named **`web-app-v2`**:

* Image: `nginx:alpine`
* Labels:

  * `app: web`
  * `version: v2`
* Replicas: `2`

Update the existing Service so that it routes traffic **only to `v2` Pods**.

🔍 *Skills tested:* Labels, selectors, Service updates

### Task 6: Deployment Using Environment Variables

Create a Deployment named **`api-app`**:

* Image: `busybox`
* Command: `sleep 3600`
* Namespace: `app-deploy`
* Environment variables:

  * `APP_ENV=production`
  * `APP_VERSION=1.0`

Verify the environment variables inside the running Pod.

🔍 *Skills tested:* Env vars, Pod inspection

### Task 7: Pause and Resume a Deployment

For the `web-app` Deployment:

1. Pause the rollout
2. Change the image to `nginx:1.27`
3. Confirm no rollout happens
4. Resume the rollout
5. Verify the update completes

🔍 *Skills tested:* Deployment pause/resume lifecycle

### Task 8: Declarative Deployment Management

You are given a file `frontend.yaml` defining a Deployment.

* Apply the Deployment
* Modify it to:

  * Increase replicas to `4`
  * Add label `tier=frontend`
* Apply changes **declaratively**
* Verify the changes are reflected

🔍 *Skills tested:* Declarative workflows, YAML editing

## Scoring Guide (Self-Assessment)

| Skill Area                         | Tasks   |
| ---------------------------------- | ------- |
| Create & manage Deployments        | 1, 6, 8 |
| Scaling & rollout strategies       | 1, 2, 7 |
| Rollback & updates                 | 3       |
| Service exposure & traffic routing | 4, 5    |
| Real exam readiness                | All     |

