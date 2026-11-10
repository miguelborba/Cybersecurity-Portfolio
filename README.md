# 🛡️ Portfólio de Cibersegurança - Miguel Borba

Bem-vindo ao meu portfólio prático de Cibersegurança! Este repositório documenta os meus laboratórios, análises de tráfego de rede e projetos desenvolvidos ao longo dos meus estudos.

---

## 📜 Certificações & Cursos

| Certificado / Módulo | Emissor | Data de Conclusão | Verificação |
| :--- | :--- | :--- | :--- |
| **Google Cybersecurity Certificate** | Google / Coursera | 🔄 Em andamento | *(2 de 7 concluídos)* |
| ├─ **Foundations of Cybersecurity** | Google | 02/10/2026 | [Credencial](https://coursera.org/verify/113ID1507INP) |
| ├─ **Play It Safe: Manage Security Risks** | Google | 17/10/2026 | [Credencial](https://coursera.org/verify/LHBP7PAIK8KX) |
| └─ **Networks and Network Security** | Google | ⏳ Em andamento | — |

---

## 🛰️ Projeto 1: Análise de Tráfego de Rede e Criptografia Web (Wireshark)

### 📌 Objetivo
Analisar a captura de pacotes em tempo real numa rede local para compreender o funcionamento dos protocolos **DNS** (resolução de nomes) e **TLS/HTTPS** (criptografia web).

### 🛠️ Ferramentas Utilizadas
* **Wireshark** (Captura e Análise de Pacotes)
* **Npcap** (Driver de Captura no Windows)
* **Protocolos:** DNS, TLSv1.2, TLSv1.3, IPv4, IPv6, TCP, UDP

---

### 🔍 1. Resolução de Nomes com o Protocolo DNS
* **Filtro utilizado:** `dns`
* **Análise:** Foi capturada a consulta (`Standard query`) enviada pelo computador para descobrir o endereço IP do domínio `youtube.com` na porta 53 (UDP).
* **Resultado:** O servidor DNS respondeu (`Standard query response`) com a lista de endereços IP numéricos pertencentes à infraestrutura da plataforma, permitindo ao computador iniciar a conexão.

---

### 🔒 2. Identificação de Servidores em Tráfego Criptografado (SNI)
* **Filtro utilizado:** `tls.handshake.type == 1`
* **Análise:** Com a aplicação do filtro no *Handshake* (mensagem *Client Hello*), foi possível inspecionar o parâmetro **SNI (Server Name Indication)** no cabeçalho TLS.
* **Resultado:** Identificação dos nomes de domínio reais de destino antes da conversa ser encriptada (ex.: `canva.com`, `riotgames.com`, `operacdn.com`).

---

### 🛡️ 3. Análise de Confidencialidade e Criptografia
* **Observação de Pacotes `Application Data`:** Após o estabelecimento do *handshake* TLS, todo o conteúdo das aplicações (mensagens de texto, credenciais, ficheiros) passa a ser transmitido de forma cifrada.
* **Conclusão:** A inspeção visual dos bytes no Wireshark demonstrou que conexões HTTPS impedem a leitura de dados sensíveis por terceiros na rede local, garantindo o princípio da **Confidencialidade** da Segurança da Informação.
