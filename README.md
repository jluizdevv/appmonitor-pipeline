# 📡 AppMonitor

## CI Status

![CI Status](https://github.com/jluizdevv/appmonitor-pipeline/actions/workflows/ci.yml/badge.svg)

---

AppMonitor é uma aplicação voltada para o monitoramento simples e contínuo de sistemas. Seu objetivo é fornecer verificações automatizadas de status para auxiliar pipelines de CI/CD e garantir que aplicações estejam funcionando corretamente.

---

## Pipeline de Integração Contínua (CI)

O workflow `ci.yml` é acionado automaticamente a cada push e pull request na branch `main`. Ele executa:

- **validate**: verifica a sintaxe do script `status-check.sh` com `bash -n`.
- **test**: simula a execução de testes com mensagem simples.
- **package**: gera um artefato `report.zip` e faz upload para o GitHub.

Esse pipeline ajuda a garantir a qualidade do código antes do deploy.

---

## Pipeline de Deploy Contínuo (CD)

O workflow `deploy.yml` é disparado em pushes para a branch `main` e simula o deploy da aplicação. 

- Usa um ambiente `production` configurado com aprovação manual obrigatória.
- Utiliza a variável de ambiente `PROD_DOMAIN=appmonitor.com`.
- O job de deploy só é executado após aprovação via interface do GitHub.

---

## Diagnóstico Automático de Falhas

O workflow `diagnostic.yml` verifica se variáveis obrigatórias estão definidas, como:

- `APP_ENV`
- `API_KEY`

Se alguma variável estiver faltando, o workflow gera erros e mensagens de diagnóstico, além de um resumo automático para ajudar a corrigir problemas rapidamente.

---

## Variáveis e Segredos no GitHub Actions

No GitHub Actions, existem três formas principais de usar variáveis:

1. **Variables (Variáveis do repositório)**  
   São valores públicos que você configura no GitHub, como ambiente ou email de suporte. Usamos elas com `${{ vars.NOME }}` no workflow.

2. **Secrets (Segredos)**  
   Dados confidenciais, como chaves de API ou senhas, que ficam protegidos e não aparecem nos logs. Acessamos com `${{ secrets.NOME }}`.

3. **Env (Variáveis de ambiente)**  
   Variáveis definidas diretamente no workflow para uso nos scripts durante a execução. Podem receber valores via `${{ vars.NOME }}` ou `${{ secrets.NOME }}` e ficam disponíveis como variáveis do sistema.

| Tipo      | Onde define                 | Como acessar          | Segurança  |
|-----------|-----------------------------|----------------------|------------|
| Variables | Configuração no GitHub       | `${{ vars.NOME }}`    | Público    |
| Secrets   | Configuração no GitHub       | `${{ secrets.NOME }}` | Protegido  |
| Env       | No workflow (arquivo YAML)   | Variável do sistema   | Depende do valor |

Usar cada um no lugar certo ajuda a manter os workflows organizados, seguros e fáceis de manter.

---

## Logs e Summaries no Pipeline CI

Durante a execução do pipeline:

- Os **logs detalhados** ajudam a entender o que está acontecendo em cada etapa, facilitando a identificação rápida de erros.
- Os **summaries (resumos automáticos)** mostram o status dos jobs, o ambiente usado e links para os artefatos gerados.

Ativar logs de debug e criar summaries claros é essencial para manter pipelines confiáveis e facilitar a depuração.

---

## Como usar este projeto

1. Faça push nas branches configuradas para disparar o pipeline.
2. Para deploy, aprove manualmente o job no ambiente `production`.
3. Revise logs e artefatos gerados para garantir qualidade.

---

## Contato

Em caso de dúvidas ou sugestões, entre em contato: suporte@appmonitor.io

---
