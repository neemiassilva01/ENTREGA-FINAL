# TechStock - Arquitetura Inicial (AWS)

## 📌 Contexto
A empresa Honey Badger utiliza o sistema de gestão de estoque **TechStock** hospedado na **AWS (us-east-1)**.  
Esta entrega parcial (17/06/2026) contempla a **arquitetura inicial com monitoramento/observabilidade** e os **custos estimados apenas na AWS**.

---

## 🏗️ Arquitetura Inicial

- **Frontend (EC2)**: Servindo HTML/JS/CSS.
- **Backend (EC2 + ALB)**: Aplicação Node.js atrás de um Application Load Balancer.
- **Monitoramento (EC2)**: Prometheus + Grafana para observabilidade.
- **VPC**: 10.0.0.0/16 com subnets públicas e privadas.
- **Storage**: EBS para persistência.

---

## ✅ Checklist de Validação

- [VPC configurada](ca://s?q=AWS_VPC_best_practices) com subnets públicas/privadas.  
- [Frontend](ca://s?q=Frontend_on_EC2_best_practices) acessível via ALB + HTTPS.  
- [Backend Node.js](ca://s?q=Nodejs_on_AWS_best_practices) com health checks ativos.  
- [Prometheus + Grafana](ca://s?q=Prometheus_Grafana_on_AWS) rodando e coletando métricas.  
- [Custos iniciais](ca://s?q=AWS_cost_estimation) calculados e documentados.  

---

## 💰 Custos Estimados (Somente AWS)

| Serviço | Tipo | Estimativa Mensal |
| --- | --- | --- |
| **[EC2 Frontend](ca://s?q=AWS_EC2_costs)** | t3.small | ~US$ 16 |
| **[EC2 Backend](ca://s?q=AWS_EC2_costs)** | t3.small | ~US$ 16 |
| **[EC2 Prometheus/Grafana](ca://s?q=AWS_EC2_costs)** | t3.small | ~US$ 16 |
| **[Application Load Balancer](ca://s?q=AWS_ALB_costs)** | ALB | ~US$ 18 |
| **[EBS Storage](ca://s?q=AWS_EBS_costs)** | 50GB | ~US$ 10 |
| **[Data Transfer](ca://s?q=AWS_data_transfer_costs)** | 2 GB/mês | ~US$ 15 |
| **[VPC Gateway Load Balancer](ca://s?q=AWS_Gateway_Load_Balancer_costs)** | 1 endpoint | ~US$ 20 |

**Total aproximado: ~US$ 143/mês**
