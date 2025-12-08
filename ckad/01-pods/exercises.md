# Define, Build and Modify Container Images

##Exercise 1: Build a Custom Image for a Kubernetes App

### Task:

1. Create a simple Python web server (python:3.12-slim) that prints Hello CKAD.
2. Write a Dockerfile that:
   1. copies code into /app
   2. runs server on port 8080
   3. sets the entrypoint correctly
3. Build the image locally as ckad/app:v1.
4. Use it in a Pod named app-pod and verify it runs.

**Success Criteria**
`kubectl logs app-pod` includes Hello CKAD.

