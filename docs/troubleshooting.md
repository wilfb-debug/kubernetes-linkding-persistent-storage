# Troubleshooting Notes

## "zsh: command not found: apiVersion" / YAML pasted into terminal
Fix: YAML must be saved in a `.yaml` file and applied with:
- kubectl apply -f <file>.yaml

## "couldn't get current server API group list" / connection refused 127.0.0.1:6443
Fix checklist:
- Ensure Rancher Desktop Kubernetes is enabled and running
- Confirm context: `kubectl config current-context`
- Restart terminal after PATH changes

## kubectl port-forward looks "stuck"
Expected: it keeps running to maintain the tunnel.
Stop with Ctrl+C.
