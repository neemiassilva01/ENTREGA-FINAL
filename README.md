**INTEGRANTES:**

Késia Silva,
Marcos Angelo,
Mateus Vasconcelos,
Miguel Boscolo e
Neemias Silva


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
| **[EC2 Frontend](ca://s?q=AWS_EC2_costs)** | t3.small + 10GB EBS | ~US$ 17,79 |
| **[EC2 Backend](ca://s?q=AWS_EC2_costs)** | t3.small + 10GB EBS | ~US$ 17,79 |
| **[EC2 Monitoramento (Prometheus/Grafana)](ca://s?q=AWS_EC2_costs)** | t3.small + 10GB EBS | ~US$ 17,79 |
| **[Application Load Balancer](ca://s?q=AWS_ALB_costs)** | ALB | ~US$ 20–25 |
| **[NAT Gateway](ca://s?q=NAT_Gateway_em_AWS)** | 1 gateway + 10GB processados | ~US$ 33–36 |
| **[EBS Storage](ca://s?q=AWS_EBS_costs)** | 30GB (10GB × 3 instâncias) | ~US$ 3 |
| **[Data Transfer](ca://s?q=AWS_data_transfer_costs)** | estimado (tráfego leve) | ~US$ 5 |

---

## 📊 Total Estimado
**~US$ 110–120/mês**

**Arquivo em PDF dos custos iniciais: https://github.com/neemiassilva01/ENTREGA-FINAL/blob/main/My%20Estimate%20-%20Calculadora%20de%20Pre%C3%A7os%20da%20AWS.pdf**

**TOPOLOGIA INICIAL:**
