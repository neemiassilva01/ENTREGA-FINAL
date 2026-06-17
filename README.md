#ENTREGA-FINAL

Arquitetura inicial (+ diagrama):

Internet (HTTP:80)
    │
    ▼
ALB (SEU_ALB_DNS)
    ├── /api/*        prioridade 1 → tg-backend   (EC2 Backend :3000)
    ├── /grafana/*    prioridade 2 → tg-monitoring (EC2 Monitoring :80 → Nginx)
    ├── /prometheus/* prioridade 3 → tg-monitoring (EC2 Monitoring :80 → Nginx)
    └── /*            prioridade 4 → tg-frontend   (EC2 Frontend :80)

VPC (10.0.0.0/16)
    Subnet Pública   → NAT Gateway, ALB
    Subnet Privada   → EC2 Backend, EC2 Frontend, EC2 Monitoring, RDS PostgreSQL

EC2 Backend (subnet privada)
    ├── Node.js :3000 (TechStock API)
    ├── Node Exporter :9100
    └── CloudWatch Agent → /techstock/app

EC2 Frontend (subnet privada)
    ├── Nginx :80 (arquivos estáticos)
    ├── Node Exporter :9100
    └── CloudWatch Agent → /techstock/nginx-*

EC2 Monitoring (subnet privada)
    ├── Nginx :80
    │       ├── /grafana/    → Grafana :3000
    │       └── /prometheus/ → Prometheus :9090
    ├── Grafana :3000
    ├── Prometheus :9090
    ├── Node Exporter :9100
    └── CloudWatch Agent → TechStock/Monitoring

RDS PostgreSQL (subnet privada, SSL, porta 5432)

//////////////////////////////////////////////////////////////////////////////////////

┌─────────────────────────────────┐ 
│           AWS                   │ 
│  us-east-1                      │ 
│                                 │ 
│  EC2 ─── Frontend (HTML/JS/CSS) │ 
│                                 │ 
│  EC2 ─── Prometheus | Grafana   │
│                                 │
│  ALB ─── EC2 Backend (Node.js)  │
│               │                 │
│  VPC: 10.0.0.0/16               │ 
└─────────────────────────────────┘
