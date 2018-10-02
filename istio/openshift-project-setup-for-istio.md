# Setup project to Istio

```bash
# Select your project
export PROJECT_NAME=yourproject

oc project $PROJECT_NAME

# Add privileged rules to default sa that runs all containers by default
oc adm policy add-scc-to-user privileged -z default

# Allow your devops sa to view istio-system namespace
oc policy add-role-to-user view system:serviceaccount:$PROJECT_NAME:devops -n istio-system

PROJECT_NAME=yourproject \
oc project $PROJECT_NAME && \
oc adm policy add-scc-to-user privileged -z default && \
oc policy add-role-to-user view system:serviceaccount:$PROJECT_NAME:devops -n istio-system
```