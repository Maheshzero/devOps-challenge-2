
## Project Details

- **Containerization:**
  - The Flask backend was containerized using a custom Dockerfile.
  - The frontend (Vue) was also containerized for completeness.
  - Docker Compose was used for local multi-service orchestration.

- **Kubernetes Deployment:**
  - Minikube could not be used due to system errors, so a standard Kubernetes cluster was used for deployment.
  - The original repository could not be used directly due to a Celery version conflict during image composition. The backend was adapted to resolve these issues.
  - The application was split into two pods (frontend and backend) and exposed via the specified NodePort.

- **Proof of Deployment:**
  - Screenshots of the running pods and the app accessible via NodePort are included in the `screenshots/` folder in this directory.

## Steps Taken

1. **Forked and cloned the challenge repository.**
2. **Resolved dependency issues (Celery version conflict) and built Docker images for backend and frontend.**
3. **Created Kubernetes manifests (`deployment.yaml` and `service.yaml`) to deploy the backend and frontend as separate pods.**
4. **Exposed the backend via NodePort as required.**
5. **Verified deployment and accessibility; included screenshots for proof.**

## Screenshots

Screenshots showing the pods running and the app accessible via NodePort are available in the `screenshots/` folder:

## Notes

- Minikube was not used due to system errors; a standard Kubernetes cluster was used instead.
- The original repo was not used directly due to Celery version conflicts; the backend was adapted to resolve these issues.
- All steps, configuration files, and proof are included in this submission.
