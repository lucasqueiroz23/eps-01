# Relatório de Prontidão Técnica: Onboarding SecOps

**Disciplina:** Engenharia de Produto de Software (FGA0316) - 2026.1
**Aluno:** Lucas Henrique Lima de Queiroz | **Matrícula:** 190091703

## 1. Configuração do Ambiente (Zero Trust & Isolamento)

Conforme as diretrizes de Soberania Técnica, as seguintes configurações foram aplicadas:

- [x] **Python 3.12:** Instalado e verificado.
- [x] **Poetry:** Configurado para criar `.venv` dentro do projeto (`virtualenvs.in-project true`).
- [x] **Determinismo:** Arquivos `pyproject.toml` e `poetry.lock` gerados com sucesso.

## 2. Logs de Auditoria e Qualidade (Security Gate)

Abaixo constam os resumos das execuções dos comandos de segurança:

### 2.1. Auditoria Estática (Bandit)

> [Cole aqui o log resumido ou o número de vulnerabilidades encontradas - Deve ser ZERO]

*Comando: `poetry run bandit -r .`*

![Bandit output](images/bandit.png)

### 2.2. Verificação de Dependências (Safety)

> [Cole aqui o log da verificação de CVEs em bibliotecas de terceiros]

*Comando: `poetry run safety check`*

![Safety output](images/safety.png)

### 2.3. Qualidade e Conformidade (Ruff)

> [Cole o log do linter e formatter]

*Comando: `poetry run ruff check .`*

![Ruff output](images/ruff.png)

## 3. Evidência de Integração Contínua (CI)

O pipeline automatizado foi executado com sucesso no GitHub Actions:

- **Link da Action de Sucesso:** [https://github.com/lucasqueiroz23/eps-01/actions/runs/23691447221](https://github.com/lucasqueiroz23/eps-01/actions/runs/23691447221)

![GitHub Actions CI](images/ci.png)

## 4. Declaração de Soberania Técnica (CISSP Domain 8)

Eu, Lucas Henrique Lima de Queiroz, declaro que auditei manualmente as ferramentas e dependências deste projeto. Confirmo que o código gerado via IA (GitHub Copilot) passou pela minha revisão humana (*Human-in-the-loop*), garantindo que não há vazamento de segredos ou falhas lógicas críticas antes da migração para o ecossistema da PCDF.

---

**Data de Entrega:** 30/03/2026

## Observações

Eu escolhi executar os checks de CI no mesmo job, ao invés de jobs paralelos, para evitar a latência de instanciar runners novos e instalar as dependências mais de uma vez. Além disso, na etapa de execução do `bandit`, tive que adicionar a opção `-x ./.venv` ao CI para evitar que ele verificasse os arquivos da `venv`, ou seja, validasse apenas os arquivos do projeto, e não as dependências.
