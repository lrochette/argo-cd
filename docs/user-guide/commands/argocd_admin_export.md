# `argocd admin export` Command Reference

## argocd admin export

Export all Argo CD data to stdout (default) or a file

```
argocd admin export [flags]
```

### Options

```
      --application-namespaces strings      Comma-separated list of namespace globs to export applications from, in addition to the control plane namespace (Argo CD namespace). By default, all applications from the control plane namespace are always exported. If this flag is provided, applications from the specified namespaces are exported along with the control plane namespace. If not specified, the value from 'application.namespaces' in argocd-cmd-params-cm is used (if defined in the ConfigMap). If the ConfigMap value is not set, only applications from the control plane namespace are exported.
      --applicationset-namespaces strings   Comma-separated list of namespace globs to export ApplicationSets from, in addition to the control plane namespace (Argo CD namespace). By default, all ApplicationSets from the control plane namespace are always exported. If this flag is provided, ApplicationSets from the specified namespaces are exported along with the control plane namespace. If not specified, the value from 'applicationsetcontroller.namespaces' in argocd-cmd-params-cm is used (if defined in the ConfigMap). If the ConfigMap value is not set, only ApplicationSets from the control plane namespace are exported.
      --as string                           Username to impersonate for the operation
      --as-group stringArray                Group to impersonate for the operation, this flag can be repeated to specify multiple groups.
      --as-uid string                       UID to impersonate for the operation
      --certificate-authority string        Path to a cert file for the certificate authority
      --client-certificate string           Path to a client certificate file for TLS
      --client-key string                   Path to a client key file for TLS
      --cluster string                      The name of the kubeconfig cluster to use
      --context string                      The name of the kubeconfig context to use
      --disable-compression                 If true, opt-out of response compression for all requests to the server
  -h, --help                                help for export
      --insecure-skip-tls-verify            If true, the server's certificate will not be checked for validity. This will make your HTTPS connections insecure
      --kubeconfig string                   Path to a kube config. Only required if out-of-cluster
  -n, --namespace string                    If present, the namespace scope for this CLI request
  -o, --out string                          Output to the specified file instead of stdout (default "-")
      --password string                     Password for basic authentication to the API server
      --proxy-url string                    If provided, this URL will be used to connect via proxy
      --request-timeout string              The length of time to wait before giving up on a single server request. Non-zero values should contain a corresponding time unit (e.g. 1s, 2m, 3h). A value of zero means don't timeout requests. (default "0")
      --server string                       The address and port of the Kubernetes API server
      --tls-server-name string              If provided, this name will be used to validate server certificate. If this is not provided, hostname used to contact the server is used.
      --token string                        Bearer token for authentication to the API server
      --user string                         The name of the kubeconfig user to use
      --username string                     Username for basic authentication to the API server
```

### Options inherited from parent commands

```
      --argocd-context string           The name of the Argo-CD server context to use
      --auth-token string               Authentication token; set this or the ARGOCD_AUTH_TOKEN environment variable
      --client-crt string               Client certificate file
      --client-crt-key string           Client certificate key file
      --config string                   Path to Argo CD config (default "/home/user/.config/argocd/config")
      --controller-name string          Name of the Argo CD Application controller; set this or the ARGOCD_APPLICATION_CONTROLLER_NAME environment variable when the controller's name label differs from the default, for example when installing via the Helm chart (default "argocd-application-controller")
      --core                            If set to true then CLI talks directly to Kubernetes instead of talking to Argo CD API server
      --grpc-web                        Enables gRPC-web protocol. Useful if Argo CD server is behind proxy which does not support HTTP2.
      --grpc-web-root-path string       Enables gRPC-web protocol. Useful if Argo CD server is behind proxy which does not support HTTP2. Set web root.
  -H, --header strings                  Sets additional header to all requests made by Argo CD CLI. (Can be repeated multiple times to add multiple headers, also supports comma separated headers)
      --http-retry-max int              Maximum number of retries to establish http connection to Argo CD server
      --insecure                        Skip server certificate and domain verification
      --kube-context string             Directs the command to the given kube-context
      --logformat string                Set the logging format. One of: json|text (default "json")
      --loglevel string                 Set the logging level. One of: debug|info|warn|error (default "info")
      --plaintext                       Disable TLS
      --port-forward                    Connect to a random argocd-server port using port forwarding
      --port-forward-namespace string   Namespace name which should be used for port forwarding (default "argocd")
      --prompts-enabled                 Force optional interactive prompts to be enabled or disabled, overriding local configuration. If not specified, the local configuration value will be used, which is false by default.
      --redis-compress string           Enable this if the application controller is configured with redis compression enabled. (possible values: gzip, none) (default "gzip")
      --redis-haproxy-name string       Name of the Redis HA Proxy; set this or the ARGOCD_REDIS_HAPROXY_NAME environment variable when the HA Proxy's name label differs from the default, for example when installing via the Helm chart (default "argocd-redis-ha-haproxy")
      --redis-name string               Name of the Redis deployment; set this or the ARGOCD_REDIS_NAME environment variable when the Redis's name label differs from the default, for example when installing via the Helm chart (default "argocd-redis")
      --repo-server-name string         Name of the Argo CD Repo server; set this or the ARGOCD_REPO_SERVER_NAME environment variable when the server's name label differs from the default, for example when installing via the Helm chart (default "argocd-repo-server")
      --server-crt string               Server certificate file
      --server-name string              Name of the Argo CD API server; set this or the ARGOCD_SERVER_NAME environment variable when the server's name label differs from the default, for example when installing via the Helm chart (default "argocd-server")
```

### SEE ALSO

* [argocd admin](argocd_admin.md)	 - Contains a set of commands useful for Argo CD administrators and requires direct Kubernetes access

