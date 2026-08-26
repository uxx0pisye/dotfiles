# Kubernetes Cheatsheet

Useful commands and aliases for daily SRE work.

## Context & Namespace

```bash
# List contexts
alias kctx='kubectl config get-contexts'

# Switch context (with fzf)
alias kc='kubectl config use-context'
function kcx() {
  local ctx=$(kubectl config get-contexts --output=name | fzf)
  kubectl config use-context "$ctx"
}

# Set default namespace for current context
alias kns='kubectl config set-context --current --namespace'
```

## Pods & Containers

```bash
# Tail logs from all pods in a deployment
alias kl='kubectl logs -f'

# Exec into a pod by name
alias ke='kubectl exec -it'

# Run a temporary debug pod
alias kdbg='kubectl run debug --rm -it --image=nicolaka/netshoot -- /bin/bash'
```

## Port Forwarding

```bash
# Forward local port to a pod
alias kpf='kubectl port-forward'
```

## Resource Inspection

```bash
# Get everything in current namespace
alias kga='kubectl get all'

# Describe a resource (e.g., pod, node)
alias kd='kubectl describe'

# Show resource usage
alias ktop='kubectl top'

# Watch node status
alias kwn='kubectl get nodes -w'
```

## YAML / Debugging

```bash
# Dry-run and output YAML
alias ky='kubectl create --dry-run=client -o yaml'

# Get events sorted by time
alias kev='kubectl get events --sort-by=.lastTimestamp'

# Inspect resource as JSON (for jq)
alias kj='kubectl get -o json'
```

## Notes

- Always verify context before destructive operations: `kubectl config current-context`
- Use `kubectl api-resources` to discover resource shortnames.
- For cluster-wide issues, check `kubectl get nodes -o wide` and `kubectl describe node <name>`.
