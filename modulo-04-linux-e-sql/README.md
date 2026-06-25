# Módulo 4: Ferramentas do Ofício - Linux e SQL 🛠️

*Status: Em andamento ⏳*

Neste módulo prático, estou aprendendo a utilizar o sistema operacional Linux via linha de comando (CLI) e a realizar consultas em bancos de dados relacionais com SQL, ferramentas indispensáveis para a rotina de um Analista de Segurança.

## 🧠 Principais Conceitos em Aprendizado

*   **Ambiente Linux:** Navegação em sistemas de arquivos usando o terminal (Bash), gerenciamento de arquivos e manipulação de texto.
*   **Permissões de Arquivos:** Compreensão e alteração de permissões de acesso a arquivos e diretórios (`chmod`) para proteger dados sensíveis.
*   **Fundamentos de SQL:** Introdução a bancos de dados relacionais, tabelas e estruturas básicas de consulta de dados.

## 💻 Guia de Comandos Linux Praticados (Cheat Sheet)

### Navegação e Arquivos
*   `pwd` — Exibe o caminho absoluto do diretório atual.
*   `ls -la` — Lista todos os arquivos (incluindo ocultos) com detalhes de permissões, dono e tamanho.
*   `cd [diretorio]` — Altera o diretório de trabalho atual.
*   `cat [arquivo]` — Exibe o conteúdo de um arquivo de texto diretamente no terminal.
*   `nano [arquivo]` — Abre o editor de texto direto no terminal para modificar arquivos de configuração.

### Filtros e Análise de Logs
*   `grep "termo"` — Filtra linhas que contêm uma palavra específica (essencial para buscar erros ou invasões em logs).
*   `head -n 10` / `tail -n 10` — Exibe as primeiras ou as últimas 10 linhas de um arquivo grande de log.

---

## 🎯 Laboratório Prático: Auditoria e Alteração de Permissões no Linux

**Cenário:** Como analista de segurança, recebi a tarefa de auditar o diretório `/home/projetos_confidenciais` para garantir que apenas usuários autorizados tenham acesso aos relatórios de vulnerabilidades da empresa.

### Passo 1: Identificação do Problema
Ao rodar o comando para listar as permissões:
```bash
ls -la relatorio_vulnerabilidades.txt
```
O terminal retornou: `-rw-rw-rw- 1 analista_junior consultores 2048 Jan 15 10:00 relatorio_vulnerabilidades.txt`

*   **Análise:** O arquivo estava com a permissão `666` (leitura e escrita para o Dono, Grupo e Outros). Isso significa que qualquer usuário temporário ou atacante que invadisse o sistema poderia ler e modificar o relatório.

### Passo 2: Correção e Mitigação do Risco
Para aplicar o princípio do privilégio mínimo, removi o acesso de escrita e leitura de todos os outros usuários, mantendo o acesso completo apenas para o dono (analista_junior).

Utilizei o comando em notação octal:
```bash
chmod 600 relatorio_vulnerabilidades.txt
```

### Passo 3: Verificação do Sucesso
Rodei novamente o comando de listagem e o resultado foi atualizado com sucesso:
`-rw------- 1 analista_junior consultores 2048 Jan 15 10:05 relatorio_vulnerabilidades.txt`

*   **Resultado:** O arquivo agora está devidamente protegido contra acessos não autorizados de terceiros.

---

## 💾 Próximos Laboratórios (Espaço Reservado)
*   [ ] Filtros avançados de arquivos de log com `grep` e `pipe (|)`
*   [ ] Consultas SQL básicas: Extraindo dados de acessos suspeitos com `SELECT`, `FROM` e `WHERE`
*   [ ] Junção de tabelas com `JOIN` para correlacionar eventos de segurança

---
[Voltar para a página inicial do repositório](../README.md)
