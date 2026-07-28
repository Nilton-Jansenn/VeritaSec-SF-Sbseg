> ## Dados Experimentais
>
> O diretório **`Dados/`** reúne os **insumos utilizados** e os **resultados produzidos** durante os experimentos apresentados no artigo submetido ao **SBSeg 2026**, permitindo a reprodução, inspeção e validação das avaliações realizadas com o **VeritasSec**.
>
> A organização dos dados foi projetada para facilitar a reprodutibilidade dos experimentos, separando claramente as entradas utilizadas pelo framework das saídas geradas durante o processamento.
>
> ### Estrutura
>
> ```text
> Dados/
> │
> ├── JuiceShop/
> │   ├── Codigo-Fonte/
> │   └── JuiceShop.sarif
> │
> ├── Google-Gemini/
> │   └──  Google-Gemini.zip
        └──  README.md

> │
> └── OpenAI/
>      └──  OpenAI-ChatGpt
         └──  README.md
> ```
>
> ### Descrição dos Diretórios
>
> **JuiceShop/**
>
> Contém o projeto **OWASP Juice Shop** utilizado como objeto de estudo durante os experimentos, bem como o respectivo relatório **SARIF** gerado pela ferramenta SAST e utilizado como entrada para o VeritasSec.
>
> **Google-Gemini/**
>
> Contém os resultados produzidos pelo VeritasSec utilizando modelos da família **Google Gemini**, incluindo, conforme aplicável:
>
> - relatórios em CSV;
> - relatórios em JSON;
> - relatórios em Markdown;
> - arquivos SARIF enriquecidos;
> - métricas de execução;
> - gráficos estatísticos gerados automaticamente.
>
> **OpenAI/**
>
> Contém os resultados produzidos pelo VeritasSec utilizando modelos da **OpenAI**, seguindo a mesma organização e formato adotados para os experimentos realizados com o Google Gemini.
>
> ### Objetivo
>
> A disponibilização desses dados permite que os avaliadores:
>
> - reproduzam os experimentos descritos no artigo;
> - inspecionem os insumos utilizados durante a avaliação;
> - comparem os resultados produzidos pelos diferentes provedores de IA;
> - validem os relatórios, métricas, gráficos e arquivos SARIF enriquecidos gerados automaticamente pelo VeritasSec.




# Download do Artefato

O artefato oficial do SBSeg 2026 está disponível na seção **Releases** deste repositório.

👉 Acesse:
https://github.com/Nilton-Jansenn/VeritaSec-SF-Sbseg/releases/latest

Arquivo:

VeritasSec-SBSeg2026-Artifact-v1.0.zip


# VeritasSec

> **Context-Aware SAST Validation Framework**
>
> Artefato científico submetido ao **SBSeg 2026** para validação contextual de vulnerabilidades identificadas por ferramentas de Static Application Security Testing (SAST), utilizando enriquecimento semântico por Modelos de Linguagem (LLMs) e validação contextual multicamadas.

---

## Sumário

- [Visão Geral](#visão-geral)
- [Requisitos](#requisitos)
- [Estrutura do Artefato](#estrutura-do-artefato)
- [Inicialização](#inicialização)
- [Configuração da IA](#configuração-da-ia)
- [Execução da Análise](#execução-da-análise)
- [Resultados](#resultados)
- [Encerramento](#encerramento)
- [Solução de Problemas](#solução-de-problemas)
- [Limitações](#limitações)
- [Informações do Artefato](#informações-do-artefato)

---

# Visão Geral

O **VeritasSec** é um framework de apoio à análise de vulnerabilidades de aplicações, desenvolvido para reduzir falsos positivos provenientes de ferramentas SAST por meio de inferência contextual baseada em Grandes Modelos de Linguagem (LLMs).

O artefato disponibilizado nesta submissão permite reproduzir os experimentos apresentados no artigo científico de maneira simples, utilizando apenas os scripts disponibilizados no pacote.

> **Importante**
>
> Todo o ambiente de execução é inicializado automaticamente através do script `iniciar.sh`. Não é necessário executar comandos Docker manualmente.

---

# Requisitos

## Sistema operacional validado

- Ubuntu 22.04 LTS ou superior (recomendado)
- Linux x86_64
- Arquitetura AMD64

## Software

- Docker Engine **28.x** ou superior
- Docker Compose **2.x** ou superior

## Requisitos adicionais

- Conexão com a Internet (apenas para comunicação com o provedor de IA)
- Chave válida do provedor de IA suportado

---

# Verificando o Ambiente

Antes de executar o artefato, recomenda-se verificar se o Docker está funcionando corretamente.

```bash
docker info
docker compose version
docker ps
```

Caso algum desses comandos apresente erro, recomenda-se corrigir o ambiente Docker antes de prosseguir.

---

# Estrutura do Artefato

```
VeritasSec-SBSeg-2026/

├── iniciar.sh
├── parar.sh
├── imagem_docker.tar
├── docker-compose.protegido.yml
├── config/
├── input/
│   ├── projects/
│   └── sarif/
├── output/
└── logs/
```

### Diretórios

| Diretório | Descrição |
|------------|-----------|
| input/projects | Projetos a serem analisados |
| input/sarif | Relatórios SARIF produzidos pelo SAST |
| output | Resultados da análise |
| logs | Logs da execução |
| config | Arquivos de configuração |

---

# Fluxo de Execução

```
ZIP

↓

./iniciar.sh

↓

Docker

↓

PostgreSQL

↓

VeritasSec

↓

Interface Web

↓

Configurar IA

↓

Selecionar Projeto

↓

Selecionar SARIF

↓

Executar Análise

↓

Resultados
```

---

# Inicialização

Conceda permissão aos scripts, caso necessário:

```bash
chmod +x iniciar.sh parar.sh
```

Execute:

```bash
./iniciar.sh
```

O script realiza automaticamente:

- carregamento da imagem Docker;
- criação dos diretórios necessários;
- inicialização do PostgreSQL;
- inicialização do VeritasSec;
- disponibilização da interface Web.

---

# Verificando se a Inicialização foi Concluída

Após executar o script, confirme que os containers estão em execução:

```bash
docker compose ps
```

Resultado esperado:

```
postgres      Up (healthy)

veritassec    Up (healthy)
```

Em seguida, acesse a interface Web pelo navegador conforme indicado pelo artefato.

---

# Tempo Esperado

Primeira execução:

**2 a 5 minutos**

Execuções posteriores:

**20 a 40 segundos**

---

# Configuração da IA

Após acessar a interface:

1. selecione o provedor de IA;
2. informe a chave de API;
3. selecione o modelo desejado;
4. escolha o modo de análise;
5. clique em **Testar Conexão**.

A análise somente deve ser iniciada após a mensagem:

> **Conexão realizada com sucesso.**

---

# Execução da Análise

1. Copie o projeto para:

```
input/projects/
```

2. Copie o relatório SARIF para:

```
input/sarif/
```

3. Selecione ambos na interface.

4. Clique em **Executar**.

---

# Conclusão da Análise

A análise é considerada finalizada quando:

- o status da interface indicar **Concluído**;
- os arquivos forem gerados em `output/`.

---

# Resultados

Os resultados ficam disponíveis em:

```
output/
```

Exemplo:

```
output/

└── avaliacao/

    ├── relatorio.csv

    ├── relatorio.xlsx

    ├── relatorio.json

    └── ...
```

---

# Encerramento

Após finalizar as análises:

```bash
./parar.sh
```

O script encerrará automaticamente todos os serviços do artefato.

---

# O que NÃO fazer

Para garantir a correta reprodução dos experimentos apresentados no artigo:

**Não execute**

```
docker run ...
```

**Não altere**

```
docker-compose.protegido.yml
```

**Não modifique manualmente**

```
config/
```

**Não mova**

```
imagem_docker.tar
```

Utilize sempre:

```
./iniciar.sh

./parar.sh
```

---

# Solução de Problemas

## Erro

```
permission denied while trying to connect to the Docker API
```

Solução:

```bash
sudo usermod -aG docker $USER
```

Encerre a sessão do usuário e faça login novamente.

---

## Docker não inicia

Verifique:

```bash
docker info
```

---

## Containers não aparecem

Verifique:

```bash
docker compose ps
```

---

## Interface Web indisponível

Verifique se ambos os containers encontram-se com status:

```
Up (healthy)
```

---

## A IA não responde

Verifique:

- conexão com a Internet;
- chave de API válida;
- configuração correta do provedor.

---

# Limitações

- O acesso à Internet é necessário apenas para comunicação com o provedor de IA.
- Todo o restante do processamento ocorre localmente.
- O artefato foi validado em Ubuntu Linux x86_64 utilizando Docker.

---

# Informações do Artefato

| Item | Valor |
|------|-------|
| Projeto | VeritasSec |
| Evento | SBSeg 2026 |
| Plataforma validada | Ubuntu 22.04 LTS |
| Docker | 28.x |
| Arquitetura | AMD64 |

---

# Observações

Este artefato foi desenvolvido exclusivamente para fins de avaliação científica no contexto do SBSeg 2026.

Para garantir a reprodutibilidade dos experimentos apresentados no artigo, recomenda-se utilizar apenas os scripts fornecidos (`iniciar.sh` e `parar.sh`) e evitar alterações na estrutura original do pacote.
