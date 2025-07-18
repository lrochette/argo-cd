# `argocd admin app generate-spec` Command Reference

## argocd admin app generate-spec

Generate declarative config for an application

```
argocd admin app generate-spec APPNAME [flags]
```

### Examples

```

	# Generate declarative config for a directory app
	argocd admin app generate-spec guestbook --repo https://github.com/argoproj/argocd-example-apps.git --path guestbook --dest-namespace default --dest-server https://kubernetes.default.svc --directory-recurse

	# Generate declarative config for a Jsonnet app
	argocd admin app generate-spec jsonnet-guestbook --repo https://github.com/argoproj/argocd-example-apps.git --path jsonnet-guestbook --dest-namespace default --dest-server https://kubernetes.default.svc --jsonnet-ext-str replicas=2

	# Generate declarative config for a Helm app
	argocd admin app generate-spec helm-guestbook --repo https://github.com/argoproj/argocd-example-apps.git --path helm-guestbook --dest-namespace default --dest-server https://kubernetes.default.svc --helm-set replicaCount=2

	# Generate declarative config for a Helm app from a Helm repo
	argocd admin app generate-spec nginx-ingress --repo https://charts.helm.sh/stable --helm-chart nginx-ingress --revision 1.24.3 --dest-namespace default --dest-server https://kubernetes.default.svc

	# Generate declarative config for a Kustomize app
	argocd admin app generate-spec kustomize-guestbook --repo https://github.com/argoproj/argocd-example-apps.git --path kustomize-guestbook --dest-namespace default --dest-server https://kubernetes.default.svc --kustomize-image quay.io/argoprojlabs/argocd-e2e-container:0.1

	# Generate declarative config for a app using a custom tool:
	argocd admin app generate-spec kasane --repo https://github.com/argoproj/argocd-example-apps.git --path plugins/kasane --dest-namespace default --dest-server https://kubernetes.default.svc --config-management-plugin kasane

```

### Options

```
      --allow-empty                                Set allow zero live resources when sync is automated
      --annotations stringArray                    Set metadata annotations (e.g. example=value)
      --auto-prune                                 Set automatic pruning when sync is automated
      --config-management-plugin string            Config management plugin name
      --dest-name string                           K8s cluster Name (e.g. minikube)
      --dest-namespace string                      K8s target namespace
      --dest-server string                         K8s cluster URL (e.g. https://kubernetes.default.svc)
      --directory-exclude string                   Set glob expression used to exclude files from application source path
      --directory-include string                   Set glob expression used to include files from application source path
      --directory-recurse                          Recurse directory
      --dry-source-path string                     Path in repository to the app directory for the dry source
      --dry-source-repo string                     Repository URL of the app dry source
      --dry-source-revision string                 Revision of the app dry source
      --env string                                 Application environment to monitor
  -f, --file string                                Filename or URL to Kubernetes manifests for the app
      --helm-api-versions stringArray              Helm api-versions (in format [group/]version/kind) to use when running helm template (Can be repeated to set several values: --helm-api-versions traefik.io/v1alpha1/TLSOption --helm-api-versions v1/Service). If not set, use the api-versions from the destination cluster
      --helm-chart string                          Helm Chart name
      --helm-kube-version string                   Helm kube-version to use when running helm template. If not set, use the kube version from the destination cluster
      --helm-namespace string                      Helm namespace to use when running helm template. If not set, use app.spec.destination.namespace
      --helm-pass-credentials                      Pass credentials to all domain
      --helm-set stringArray                       Helm set values on the command line (can be repeated to set several values: --helm-set key1=val1 --helm-set key2=val2)
      --helm-set-file stringArray                  Helm set values from respective files specified via the command line (can be repeated to set several values: --helm-set-file key1=path1 --helm-set-file key2=path2)
      --helm-set-string stringArray                Helm set STRING values on the command line (can be repeated to set several values: --helm-set-string key1=val1 --helm-set-string key2=val2)
      --helm-skip-crds                             Skip helm crd installation step
      --helm-skip-schema-validation                Skip helm schema validation step
      --helm-skip-tests                            Skip helm test manifests installation step
      --helm-version string                        Helm version
  -h, --help                                       help for generate-spec
      --hydrate-to-branch string                   The branch to hydrate the app to
      --ignore-missing-components                  Ignore locally missing component directories when setting Kustomize components
      --ignore-missing-value-files                 Ignore locally missing valueFiles when setting helm template --values
  -i, --inline                                     If set then generated resource is written back to the file specified in --file flag
      --jsonnet-ext-var-code stringArray           Jsonnet ext var
      --jsonnet-ext-var-str stringArray            Jsonnet string ext var
      --jsonnet-libs stringArray                   Additional jsonnet libs (prefixed by repoRoot)
      --jsonnet-tla-code stringArray               Jsonnet top level code arguments
      --jsonnet-tla-str stringArray                Jsonnet top level string arguments
      --kustomize-api-versions stringArray         api-versions (in format [group/]version/kind) to use when running helm template (Can be repeated to set several values: --helm-api-versions traefik.io/v1alpha1/TLSOption --helm-api-versions v1/Service). If not set, use the api-versions from the destination cluster. Only applicable when Helm is enabled for Kustomize builds
      --kustomize-common-annotation stringArray    Set common labels in Kustomize
      --kustomize-common-label stringArray         Set common labels in Kustomize
      --kustomize-force-common-annotation          Force common annotations in Kustomize
      --kustomize-force-common-label               Force common labels in Kustomize
      --kustomize-image stringArray                Kustomize images (e.g. --kustomize-image node:8.15.0 --kustomize-image mysql=mariadb,alpine@sha256:24a0c4b4a4c0eb97a1aabb8e29f18e917d05abfe1b7a7c07857230879ce7d3d)
      --kustomize-kube-version string              kube-version to use when running helm template. If not set, use the kube version from the destination cluster. Only applicable when Helm is enabled for Kustomize builds
      --kustomize-label-include-templates          Apply common label to resource templates
      --kustomize-label-without-selector           Do not apply common label to selectors. Also do not apply label to templates unless --kustomize-label-include-templates is set
      --kustomize-namespace string                 Kustomize namespace
      --kustomize-replica stringArray              Kustomize replicas (e.g. --kustomize-replica my-development=2 --kustomize-replica my-statefulset=4)
      --kustomize-version string                   Kustomize version
  -l, --label stringArray                          Labels to apply to the app
      --name string                                A name for the app, ignored if a file is set (DEPRECATED)
      --nameprefix string                          Kustomize nameprefix
      --namesuffix string                          Kustomize namesuffix
  -o, --output string                              Output format. One of: json|yaml (default "yaml")
  -p, --parameter stringArray                      set a parameter override (e.g. -p guestbook=image=example/guestbook:latest)
      --path string                                Path in repository to the app directory, ignored if a file is set
      --plugin-env stringArray                     Additional plugin envs
      --project string                             Application project name
      --ref string                                 Ref is reference to another source within sources field
      --release-name string                        Helm release-name
      --repo string                                Repository URL, ignored if a file is set
      --revision string                            The tracking source branch, tag, commit or Helm chart version the application will sync to
      --revision-history-limit int                 How many items to keep in revision history (default 10)
      --self-heal                                  Set self healing when sync is automated
      --set-finalizer                              Sets deletion finalizer on the application, application resources will be cascaded on deletion
      --source-name string                         Name of the source from the list of sources of the app.
      --sync-option Prune=false                    Add or remove a sync option, e.g add Prune=false. Remove using `!` prefix, e.g. `!Prune=false`
      --sync-policy string                         Set the sync policy (one of: manual (aliases of manual: none), automated (aliases of automated: auto, automatic))
      --sync-retry-backoff-duration duration       Sync retry backoff base duration. Input needs to be a duration (e.g. 2m, 1h) (default 5s)
      --sync-retry-backoff-factor int              Factor multiplies the base duration after each failed sync retry (default 2)
      --sync-retry-backoff-max-duration duration   Max sync retry backoff duration. Input needs to be a duration (e.g. 2m, 1h) (default 3m0s)
      --sync-retry-limit int                       Max number of allowed sync retries
      --sync-source-branch string                  The branch from which the app will sync
      --sync-source-path string                    The path in the repository from which the app will sync
      --validate                                   Validation of repo and cluster (default true)
      --values stringArray                         Helm values file(s) to use
      --values-literal-file string                 Filename or URL to import as a literal Helm values block
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
      --server string                   Argo CD server address
      --server-crt string               Server certificate file
      --server-name string              Name of the Argo CD API server; set this or the ARGOCD_SERVER_NAME environment variable when the server's name label differs from the default, for example when installing via the Helm chart (default "argocd-server")
```

### SEE ALSO

* [argocd admin app](argocd_admin_app.md)	 - Manage applications configuration

