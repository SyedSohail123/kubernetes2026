Deployment order

Because several controllers depend on others, I'd deploy them in this order:

1. ArgoCD
        │
        ▼
2. Gateway API CRDs
        │
        ▼
3. ingress-nginx
        │
        ▼
4. Envoy Gateway
        │
        ▼
5. Istio Base
        │
        ▼
6. Istiod
        │
        ▼
7. Istio Gateway
        │
        ▼
8. Cert Manager
        │
        ▼
9. Prometheus
        │
        ▼
10. Grafana
        │
        ▼
11. kube-prometheus-stack



Wave -2
    ArgoCD (optional)

Wave -1
    Gateway API CRDs

Wave 0
    ingress-nginx
    cert-manager
    istio-base

Wave 1
    Envoy Gateway
    istiod

Wave 2
    Istio Gateway

Wave 3
    Prometheus

Wave 4
    Grafana




kubernetes/
│
├── controllers/
│   │
│   ├── charts/
│   │   │
│   │   ├── argocd/
│   │   │   ├── application.yaml
│   │   │   └── values.yaml
│   │   │
│   │   ├── ingress-nginx/
│   │   │   ├── application.yaml
│   │   │   └── values.yaml
│   │   │
│   │   ├── gateway-api-crds/
│   │   │   ├── application.yaml
│   │   │   └── values.yaml
│   │   │
│   │   ├── envoy-gateway/
│   │   │   ├── application.yaml
│   │   │   └── values.yaml
│   │   │
│   │   ├── istio/
│   │   │   ├── base/
│   │   │   │   ├── application.yaml
│   │   │   │   └── values.yaml
│   │   │   │
│   │   │   ├── istiod/
│   │   │   │   ├── application.yaml
│   │   │   │   └── values.yaml
│   │   │   │
│   │   │   └── gateway/
│   │   │       ├── application.yaml
│   │   │       └── values.yaml
│   │   │
│   │   ├── cert-manager/
│   │   │   ├── application.yaml
│   │   │   └── values.yaml
│   │   │
│   │   ├── prometheus/
│   │   │   ├── application.yaml
│   │   │   └── values.yaml
│   │   │
│   │   ├── grafana/
│   │   │   ├── application.yaml
│   │   │   └── values.yaml
│   │   │
│   │   └── kube-prometheus-stack/
│   │       ├── application.yaml
│   │       └── values.yaml
│   │
│   └── application-manifests/
│       │
│       ├── argocd/
│       │   ├── application.yaml
│       │   └── manifests/
│       │       └── install.yaml
│       │
│       ├── ingress-nginx/
│       │   ├── application.yaml
│       │   └── manifests/
│       │       └── deploy.yaml
│       │
│       ├── gateway-api-crds/
│       │   ├── application.yaml
│       │   └── manifests/
│       │       └── standard-install.yaml
│       │
│       ├── envoy-gateway/
│       │   ├── application.yaml
│       │   └── manifests/
│       │       └── install.yaml
│       │
│       ├── istio/
│       │   ├── base/
│       │   │   ├── application.yaml
│       │   │   └── manifests/
│       │   │
│       │   ├── istiod/
│       │   │   ├── application.yaml
│       │   │   └── manifests/
│       │   │
│       │   └── gateway/
│       │       ├── application.yaml
│       │       └── manifests/
│       │
│       ├── cert-manager/
│       │   ├── application.yaml
│       │   └── manifests/
│       │
│       ├── prometheus/
│       │   ├── application.yaml
│       │   └── manifests/
│       │
│       ├── grafana/
│       │   ├── application.yaml
│       │   └── manifests/
│       │
│       └── kube-prometheus-stack/
│           ├── application.yaml
│           └── manifests/
│
├── applications/
│
├── ingress/
│
├── gateway-api/
│
└── tls/