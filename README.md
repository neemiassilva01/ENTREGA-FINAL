# 📦 TechStock — Guia de Implantação Multi-Cloud (AWS + Azure)

## 🖼️ Arquitetura Inicial
*(arquitetura inicial abaixo)*

---

## 🖼️ Arquitetura Final
*(arquitetura final abaixo)*

---

## 🏗️ Arquitetura Multi-Cloud

### AWS (Core da Aplicação)
- **Frontend**: migrado para **S3 + CloudFront** (HTML, CSS, JS).
- **Backend**: **EC2 Amazon Linux** rodando TechStock API (Node.js + Nginx).
- **Banco de Dados**: **Amazon RDS PostgreSQL**.
- **Gestão de Segredos**: **AWS Secrets Manager** para credenciais e certificados.
- **Balanceamento**: **Application Load Balancer (ALB)** distribuindo tráfego.
- **Rede Segura**: VPC privada com NAT Gateway e VPN Site-to-Site.

### Azure (Observabilidade + BI)
- **Monitoramento**: **Grafana + Prometheus** em VM Linux.
- **Business Intelligence**: **Power BI** conectado ao RDS via VPN.
- **Backup e relatórios**: centralizados na Azure.
- **VPN Gateway**: integração segura com AWS.

---

## 📊 Custos Estimados

| Serviço | AWS | Azure |
|---------|-----|-------|
| **Frontend** | S3 + CloudFront: USD 5–10/mês | — |
| **Backend** | EC2 t3.medium: USD 35–40/mês | — |
| **Banco de Dados** | RDS PostgreSQL db.t3.medium: USD 60–70/mês | — |
| **Gestão de Segredos** | Secrets Manager: USD 5–10/mês | Key Vault: USD 5–10/mês |
| **Balanceamento** | ALB: USD 18–20/mês | — |
| **Rede Segura** | NAT + VPN: USD 25–30/mês | VPN Gateway: USD 25–30/mês |
| **Monitoramento** | — | VM Linux (Grafana + Prometheus): USD 40–50/mês |
| **BI** | — | Power BI Pro: USD 10/usuário/mês |

**Total AWS**: ~USD 150–170/mês  
**Total Azure**: ~USD 100–120/mês  
**Custo combinado**: ~USD 250–300/mês

---

## 🎯 Benefícios da Arquitetura Final
- **Segurança reforçada**: comunicação via VPN Site-to-Site sem exposição pública.  
- **Custo otimizado**: frontend barato no S3, monitoramento consolidado na Azure.  
- **Governança**: credenciais centralizadas no Secrets Manager.  
- **Escalabilidade**: ALB e RDS permitem crescimento controlado.  
- **Flexibilidade**: BI acessa dados do RDS sem duplicação.  

---

## 📋 Ordem de Execução
1. Criar **VPC** com subnets públicas e privadas.  
2. Provisionar **RDS PostgreSQL**.  
3. Configurar **EC2 Backend** com API TechStock.  
4. Migrar **Frontend** para S3 + CloudFront.  
5. Configurar **VPN Site-to-Site** entre AWS e Azure.  
6. Migrar **Monitoramento** para Azure (Grafana + Prometheus).  
7. Conectar **Power BI** ao RDS via VPN.  
8. Validar **ALB + regras de roteamento**.  

---

## 🔧 Troubleshooting Rápido
- **Frontend sem dados** → verificar `config.js` com URL correta do ALB.  
- **Prometheus DOWN** → liberar portas 3000 e 9100 no SG do Backend.  
- **Grafana sem datasource** → recriar com UID fixo `PBFA97CFB590B2093`.  
- **API retornando HTML** → checar prioridade das regras no ALB.  

---
