Projeto Técnico: Lembretes de Consultas com IA, WhatsApp e n8n
Objetivo:
Reduzir faltas em consultas médicas por meio de automação e inteligência artificial, integrando o sistema e-SUS PEC à plataforma n8n e enviando mensagens inteligentes via WhatsApp.

Entrada de Dados:
Arquivo CSV exportado do e-SUS PEC

Colunas mínimas exigidas:

nome

data_consulta

profissional

unidade

status

Fluxo Técnico:
Trigger via n8n coleta agendamentos das próximas 48 horas.

Modelo preditivo supervisionado (ex: regressão logística, XGBoost) estima probabilidade de falta com base em:

histórico de comparecimentos;

perfil demográfico;

contexto do agendamento.

LLM (ChatGPT, Gemini, Claude) gera lembretes empáticos e personalizados com variações de linguagem segundo o perfil do paciente.

Mensagem automatizada é enviada via API do WhatsApp (360dialog, Twilio, Z-API).

Monitoramento das respostas e registros de comparecimento:

leitura da mensagem;

confirmação ou pedido de remarcação;

comportamento na próxima consulta.

Saídas e Visualização:
Dashboard interativo (Streamlit):

Taxa de comparecimento por profissional ou unidade;

Número de mensagens enviadas, lidas e respondidas;

Casos reagendados com sucesso;

Comparação antes/depois da intervenção.

Métricas Esperadas:
Redução nas faltas: 30% a 45%

Taxa de leitura das mensagens: > 80%

Aumento na ocupação de vagas remanescentes: até 25%

Feedback positivo dos usuários/pacientes: a ser coletado por NPS

Tecnologias Empregadas:
Backend e processamento:

Python 3.11, FastAPI

Scikit-learn, XGBoost

Langchain, Pandas

Automação:

n8n (automação de fluxos low-code)

IA Generativa:

OpenAI (ChatGPT), Gemini (Google), Claude (Anthropic)

Mensageria:

WhatsApp API via 360dialog, Z-API ou Twilio

Frontend e visualização:

Streamlit, Plotly

Infraestrutura:

Docker, GitHub Actions, PostgreSQL, Redis

Privacidade e Conformidade:
Dados anonimizados para treinamento dos modelos;

Mensagens não armazenam conteúdo sensível;

Conformidade com a LGPD (Art. 7º, IX — prestação de serviço em saúde);

Logs criptografados e protegidos.

Aplicações Reais:
UBSs (Unidades Básicas de Saúde)

Ambulatórios universitários e hospitais-escola

Clínicas e consultórios privados

Serviços integrados de telemedicina e regulação

Autor:
👨‍⚕️ Dr. Reginaldo E. Ramos Teodoro
