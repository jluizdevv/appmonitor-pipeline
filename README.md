# 📡 AppMonitor

![CI Status](https://img.shields.io/github/actions/workflow/status/jluizdevv/appmonitor-pipeline/ci.yml?branch=main&label=CI)


AppMonitor é uma aplicação voltada para o monitoramento simples e contínuo de sistemas. Seu objetivo é fornecer verificações automatizadas de status para auxiliar pipelines de CI/CD e garantir que aplicações estejam funcionando corretamente.

## Variáveis e Segredos no GitHub Actions

No GitHub Actions, existem três formas principais de usar variáveis:

### 1. Variables (Variáveis do repositório)
São valores públicos que você configura no GitHub, como ambiente ou email de suporte. Usamos elas com `${{ vars.NOME }}` no workflow.

### 2. Secrets (Segredos)
São dados confidenciais, como chaves de API ou senhas, que ficam protegidos e não aparecem nos logs. Acessamos com `${{ secrets.NOME }}`.

### 3. Env (Variáveis de ambiente)
São variáveis definidas direto no workflow para serem usadas nos scripts durante a execução. Elas recebem valores via `${{ vars.NOME }}` ou `${{ secrets.NOME }}` e ficam disponíveis como variáveis do sistema.

### Resumo rápido

| Tipo     | Onde define             | Como acessar             | Segurança          |
|----------|------------------------|--------------------------|--------------------|
| Variables| Configuração no GitHub  | `${{ vars.NOME }}`        | Público            |
| Secrets  | Configuração no GitHub  | `${{ secrets.NOME }}`     | Protegido          |
| Env      | No workflow (yaml)     | Variável do sistema shell | Depende do valor   |

---

Usar cada um no lugar certo ajuda a manter os workflows organizados, seguros e fáceis de manter.

---

## 🛠 Logs e Summaries no Pipeline CI

Durante a execução do pipeline, os **logs** detalhados ajudam a entender o que está acontecendo em cada etapa, facilitando a identificação rápida de erros e falhas.

Além disso, os **summaries** (resumos automáticos) fornecem uma visão geral do resultado dos jobs, incluindo o ambiente usado e links para artefatos gerados. Isso ajuda a monitorar e depurar o pipeline de forma mais eficiente, sem precisar navegar em todos os detalhes.

Ativar logs de debug e gerar summaries claros é essencial para manter pipelines confiáveis e fáceis de manter.


