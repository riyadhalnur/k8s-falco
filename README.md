# k8s-falco  
Set up [falco](https://falco.org) to for real-time threat monitoring. Events are configured to be sent to a webhook URL.  

## Installation  
Install the helm charts,
```shell
helm repo add falcosecurity https://falcosecurity.github.io/charts
helm repo update
```  

Modify `config/falco-values.yaml` to update the webhook URL you want to send audit events to  
```yaml
falcosidekick:
  enabled: true
  fullfqdn: false
  config:
    webhook:
      address: "<replace-with-your-url>"
      customHeaders: "<set-any-headers>"
```

Install `falco` using custom values  
```shell
helm install falco falcosecurity/falco -f config/falco-values.yaml --namespace <namespace-name>
```