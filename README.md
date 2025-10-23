# cheat-sheet_cmd_devops-
# common Kubernetes (kubectl) commands used by DevOps engineer

Cluster Information & Context
Purpose                            Command
View current context               kubectl config current-context
List all contexts                  kubectl config get-contexts
Switch context                     kubectl config use-context <context-name>
View cluster info                  kubectl cluster-info
Check node status                  kubectl get nodes

Workload Management (Pods, Deployments, etc.)
Task                                  Command
Get all resources in a namespace      kubectl get all -n <namespace>
Get all pods                          kubectl get pods
Describe pod                          kubectl describe pod <pod-name>
Check pod logs                        kubectl logs <pod-name>
Follow logs                           kubectl logs -f <pod-name>
Logs from specific container          kubectl logs <pod-name> -c <container-name>
Exec into a pod                       kubectl exec -it <pod-name> -- /bin/bash
Apply YAML config                     kubectl apply -f <file.yaml>
Delete resource                       kubectl delete -f <file.yaml>
Rollout status                        kubectl rollout status deployment/<deployment-name>
Restart deployment                    kubectl rollout restart deployment/<deployment-name>
Scale deployment                      kubectl scale deployment <name> --replicas=3

Namespace Management
Task                          Command
List namespaces               kubectl get namespaces
Create namespace              kubectl create namespace <name>
Delete namespace              kubectl delete namespace <name>
Use a namespace                kubectl config set-context --current --namespace=<name>

 Services & Networking
Task                           Command
List services                  kubectl get svc
Describe service               kubectl describe svc <service-name>
Port-forward service           kubectl port-forward svc/<svc-name> <local-port>:<svc-port>
Port-forward pod               kubectl port-forward pod/<pod-name> <local-port>:<pod-port>


Task                            Command
List ConfigMaps                 kubectl get configmaps
Describe ConfigMap              kubectl describe configmap <name>
List Secrets                    kubectl get secrets
Describe Secret                 kubectl describe secret <name>

Monitoring & Debugging
Task                                   Command
Top nodes (requires metrics-server)    kubectl top nodes
Top pods                               kubectl top pods
Events in namespace                    kubectl get events -n <namespace>
Dry run a deployment                   kubectl apply -f <file.yaml> --dry-run=client
Debug a pod (ephemeral container)      kubectl debug -it <pod-name> --image=busybox

Jobs & CronJobs
Task                          Command
Get jobs                      kubectl get jobs
Get cronjobs                  kubectl get cronjobs
Describe job/cronjob          kubectl describe job <name> / kubectl describe cronjob <name>

Get resource YAML             kubectl get <resource> <name> -o yaml

Authenticate & Configure kubectl for EKS
aws eks update-kubeconfig --region <region> --name <cluster_name>

Cluster & Node Management
Task                                            Command
List all EKS clusters                           aws eks list-clusters
Describe a cluster                              aws eks describe-cluster --name <cluster_name>
Get worker nodes                                kubectl get nodes
Drain a node for maintenance                    kubectl drain <node-name> --ignore-daemonsets --delete-emptydir-data
Mark node as schedulable                        kubectl uncordon <node-name>
Cordon a node (unschedulable)                   kubectl cordon <node-name>

Workloads (Pods, Deployments, etc.)
Task                            Command
List all deployments            kubectl get deployments
Restart a deployment            kubectl rollout restart deployment <deployment-name>
Exec into a pod                 kubectl exec -it <pod-name> -- bash
View logs                       kubectl logs <pod-name>
Apply configuration             kubectl apply -f <file.yaml>


# Terraform Advanced Commands Cheat Sheet
# State Management
Command                                    Description
terraform state list                       List all resources in the current state
terraform state show <resource>            Show attributes of a specific resource
terraform state mv <source> <destination>  Rename or move a resource in state (refactor without destroying)
terraform state rm <resource>              Remove a resource from state (useful before importing or decommissioning)
terraform import <resource> <id>           Import existing resource into Terraform state

Targeted Execution
Command                                        Description
terraform plan -target=resource_type.name      Generate plan for a specific resource
terraform apply -target=resource_type.name     Apply changes only for a specific resource
terraform destroy -target=resource_type.name   Destroy only the targeted resource

Validation & Formatting
Command                        Description
terraform validate             Check if configuration is syntactically valid
terraform fmt -recursive       Auto-format .tf files in current and nested directories
terraform providers            List all used providers and their versions
terraform version              Display Terraform version and provider versions used

Automation-Friendly Usage
Command                            Description
terraform apply -auto-approve      Skip manual approval during apply
terraform destroy -auto-approve    Skip approval for destroy (⚠️ dangerous in production)
terraform plan -out=tfplan         Save the plan to a file (binary) for later apply
terraform apply tfplan             Apply a saved plan file (no re-evaluation)

Terraform Cloud / Enterprise (TFE)
Command                          Description
terraform login                  Authenticate with Terraform Cloud/Enterprise
terraform logout                 Remove Terraform Cloud credentials
terraform force-unlock <lock-id> Manually unlock state file (last resort)
terraform init -backend-config="..." Set remote backend config for TFE/S3 etc.




















