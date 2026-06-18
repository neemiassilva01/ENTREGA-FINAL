# 📦 TechStock — Multi-Cloud Deployment Guide

## 🌐 Contexto de Negócio
A **Honey Badger (Alpha Tech Group)** utiliza o sistema **TechStock** para gestão de estoque.  
- Atualmente: **AWS (IaaS + PaaS)**  
- BI: contratou **Azure Power BI** sem alinhamento com TI  
- Infraestrutura: moveu **Grafana + Prometheus** para **Azure**, centralizando observabilidade, relatórios e backup  
- TechStock encerrou operações, deixando apenas o repositório disponível  

---

## 🎯 Desafios
- [Migrar frontend para S3](ca://s?q=Migrar_frontend_para_S3) e integrar com backend  
- [Criar VPN Site-to-Site](ca://s?q=Criar_VPN_Site_To_Site_AWS_Azure) entre AWS e Azure sem exposição pública  
- [Migrar monitoramento para Azure](ca://s?q=Migrar_monitoramento_para_Azure)  
- [Conectar Power BI ao RDS](ca://s?q=Conectar_Power_BI_ao_RDS)  
- [Criar infraestrutura IaC](ca://s?q=Criar_infraestrutura_IaC_multi_cloud)  

---

## 🏗️ Arquitetura Multi-Cloud

### AWS (us-east-1)
- **S3 + CloudFront** → Frontend  
- **ALB**  
  - `/api/*` → Backend  
  - `/grafana/*` → Azure  
  - `/prometheus/*` → Azure  
  - `/*` → Frontend  
- **EC2 Backend** (Node.js :3000)  
- **RDS PostgreSQL** (privado, porta 5432)  
- **VPC** com subnets públicas e privadas  

### Azure
- **Grafana + Prometheus** (AKS ou App Service)  
- **Azure Monitor + Log Analytics**  
- **Power BI** conectado ao RDS via VPN  
- **Backup** em Blob Storage  

### VPN Site-to-Site
- **AWS Virtual Private Gateway**  
- **Azure VPN Gateway**  

---

## 🔑 Componentes Principais
- **[Frontend no S3](ca://s?q=Frontend_no_S3)** — Deploy estático em S3 + CloudFront  
- **[Backend no EC2 + RDS](ca://s?q=Backend_no_RDS_e_EC2)** — Node.js em EC2 privado + PostgreSQL isolado  
- **[Monitoramento na Azure](ca://s?q=Monitoramento_na_Azure)** — Grafana + Prometheus migrados  
- **[VPN Site-to-Site](ca://s?q=VPN_Site_to_Site_AWS_Azure)** — IPSec entre AWS e Azure  
- **[Power BI conectado ao RDS](ca://s?q=Power_BI_conectado_ao_RDS)** — Azure Data Gateway + dashboards  
- **[Infraestrutura IaC](ca://s?q=Infraestrutura_IaC_multi_cloud)** — Terraform multi-cloud + CI/CD  

---

## ⚠️ Ajustes Críticos
- Ordem das regras no ALB: `/api* → /grafana* → /prometheus* → /*`  
- Security Groups: liberar portas 3000 e 9100 do backend para o SG do monitoring  
- Datasource Grafana: UID fixo `PBFA97CFB590B2093`  
- `config.js`: regenerar sempre que o ALB mudar  
- Power BI: acesso ao RDS apenas via VPN  

---

## 📋 Checklist de Implantação
- [ ] VPC com subnets pública e privada  
- [ ] RDS PostgreSQL provisionado  
- [ ] Backend em EC2 com API funcional  
- [ ] Frontend migrado para S3 + CloudFront  
- [ ] Monitoramento migrado para Azure  
- [ ] VPN Site-to-Site configurada  
- [ ] Power BI conectado ao RDS  
- [ ] Terraform IaC versionado e aplicado  
