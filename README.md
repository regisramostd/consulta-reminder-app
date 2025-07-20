# consulta-reminder-app
# App que lembra os pacientes das consultas evitando faltas 

# 🤖📱 Consulta Reminder App: AI + n8n + WhatsApp

> Plataforma inteligente para envio de lembretes automatizados de consultas via WhatsApp, integrando **inteligência artificial (LLM)**, **n8n** e dados de agendamento provenientes do **e-SUS PEC** (https://sisaps.saude.gov.br/sistemas/esusaps/), com foco em reduzir faltas, promover o cuidado contínuo e aumentar a eficiência assistencial.

---

## 🧩 Visão Geral

Faltas em consultas são um problema recorrente na atenção primária e especializada. Este sistema resolve o desafio por meio de um **pipeline robusto de agendamento, predição e notificação**, com **entrada padronizada a partir do e-SUS PEC** — podendo ser adaptado, se necessário, para outras fontes como Outlook ou Google Calendar.

O fluxo completo envolve:
1. **Coleta automatizada do agendamento** (via exportação CSV do e-SUS PEC ou API customizada);
2. **Avaliação de risco de ausência** com modelo supervisionado baseado em histórico e perfis;
3. **Geração personalizada de mensagem via LLM** (ex: ChatGPT, Gemini ou Claude);
4. **Envio automatizado via WhatsApp**;
5. **Monitoramento de entregas, respostas e comparecimentos**.

---

## 🧠 Funcionalidades

### 🔗 Integração com Agendas Clínicas
- Input padronizado a partir de arquivos CSV gerados pelo e-SUS PEC (ou outra fonte validada);
- Parsing automatizado do nome do paciente, data, hora, local e profissional;
- Trigger agendado via n8n para processar diariamente as próximas 48h de agenda.

### 🧠 Motor de IA Híbrida
- Modelo preditivo (logística ou XGBoost) baseado em presença prévia e dados contextuais;
- Utilização de LLM (ChatGPT, Gemini, Claude) para gerar lembretes empáticos e apropriados;
- Adaptação automática do texto por horário, histórico ou canal preferido.

### 📱 Mensagens via WhatsApp
- Integração com **360dialog**, **Z-API** ou **Twilio**;
- Registro de envio, recebimento e interação com o paciente;
- Possibilidade de reagendamento automático via comando ou resposta natural.

### 📊 Métricas e Outputs
- Input: CSV do e-SUS PEC (`nome`, `data_consulta`, `profissional`, `unidade`, `status`)
- Output: Dashboard de presenças, taxa de resposta, mensagens enviadas, remarcações;
- Métricas definidas:
  - **Redução esperada de faltas**: 30–45%
  - **Taxa de leitura/resposta das mensagens**: > 80%
  - **Aumento na ocupação de vagas remanescentes**: até 25%

---

## 📁 Estrutura do Projeto
```
whatsapp-consulta-reminder/
├── app/
│   ├── main.py              # API de entrada para receber CSV ou trigger
│   ├── ia_llm.py            # Integração com OpenAI, Gemini ou HuggingFace
│   ├── modelo_faltas.py     # Previsão de ausência
│   ├── scheduler.py         # Agendamento das mensagens via cron/n8n
│   └── whatsapp_sender.py   # Envio via 360dialog/Z-API
├── flows/
│   └── n8n_fluxo.json       # Exportação do fluxo de automação n8n
├── templates/
│   └── lembrete_modelo.txt
├── data/
│   └── consultas_2024.csv
├── dashboard/
│   └── streamlit_app.py     # Visualização de métricas
```

---

## ⚙️ Tecnologias Utilizadas
- **Python 3.11**, **FastAPI**, **Streamlit**, **n8n**
- **OpenAI API**, **Gemini (Google AI Studio)**, **Langchain**
- **Scikit-learn**, **XGBoost**, **spaCy**
- **WhatsApp API (360dialog / Z-API / Twilio)**
- **Docker**, **PostgreSQL**, **Redis**, **GitHub Actions**

---

## 🛡️ Privacidade e Ética
- Dados anonimizados para treino e teste
- Registro criptografado de eventos e respostas
- Conformidade com LGPD (base legal: prestação de serviço em saúde – art. 7º, IX)

---

## 👩‍⚕️ Aplicações
- Unidades Básicas de Saúde
- Ambulatórios universitários
- Clínicas e hospitais públicos ou privados
- Consultórios individuais

---

> “Engenharia de sistemas aplicada à saúde precisa ser ética, automatizada e humana.”

👨‍⚕️ Desenvolvido por [Dr. Reginaldo E. Ramos Teodoro](https://www.linkedin.com/in/reginaldo-eugenio-ramos-teodoro-4210b9376) 

🔗 [GitHub](https://github.com/regisramostd)
