# Prospector de Sites — PORT para ChatGPT (Work/Codex)

Port do fluxo do Prospector de Sites para o novo app do ChatGPT (Chat + Work + Codex), no padrão aberto **Agent Skills** — o mesmo que o ChatGPT usa nas skills (beta).

## O que mudou em relação à versão Claude

| Etapa | Claude Cowork | ChatGPT Work |
|---|---|---|
| Navegação (Maps/sites) | Claude in Chrome | Extensão do ChatGPT para Chrome |
| Publicação | HostGator + publicador local | **ChatGPT Sites** (nativo: URL pública, domínio próprio, analytics) |
| E-mail | Conector Gmail | App de e-mail conectado (@Gmail) |
| Agendamento (/respostas) | Tarefas agendadas do Cowork | Tarefas agendadas do ChatGPT |
| CRM local (SQLite) | Igual | Igual (mesmos arquivos) |
| Contrato Word travado | Igual | Igual |
| Comandos (/prospectar...) | Comandos + skills | **Só skills** — dispara pedindo em linguagem natural |

## As 6 skills

1. `prospector-prospeccao` — leads no Google Maps (3 filtros eliminatórios)
2. `prospector-redesign` — redesign premium + editor visual + comparador
3. `prospector-publicacao` — publica via ChatGPT Sites (página + capa)
4. `prospector-proposta` — e-mail anti-spam + capa + follow-up
5. `prospector-crm` — dashboard local (kanban/financeiro/contratos)
6. `prospector-contrato` — folha A4 + Word travado

## O pacote tem DUAS partes

1. **As 6 skills** (zips) — o manual do fluxo: é o que ensina o ChatGPT a prospectar, redesenhar, publicar, propor e gerar contrato.
2. **O MCP** (pasta `mcp/`) — o CRM de verdade: dá ao ChatGPT ferramentas pra ler e gravar no seu banco local (prospector.db). Instale os DOIS — as skills usam o MCP pra nunca esquecerem de atualizar o CRM.

## Como instalar o MCP (primeiro — 5 min)

1. Duplo clique em `mcp/instalar-mcp.bat` (Mac: `instalar-mcp.command`).
2. Copie `mcp/prospector-mcp.py` para a SUA pasta de trabalho (onde fica o prospector.db).
3. No cmd, digite `where python` e copie o caminho completo do python.exe.
4. ChatGPT → Plugins → MCPs → Conectar a um MCP personalizado: Nome `prospector-crm` · Tipo STDIO · Comando = o caminho completo do python.exe (Mac: `python3`) · Argumento `prospector-mcp.py` · Variáveis e Encaminhamento VAZIOS · Diretório de trabalho = sua pasta → Salvar.
5. Teste em tarefa nova: "usando o prospector-crm, resumo financeiro do meu CRM". Detalhes e erros comuns: `mcp/LEIA-ME-MCP.md`.

## Como instalar (cada skill)

ChatGPT → foto de perfil → **Skills** → **New skill** → **Upload from your computer** → envie o `.zip` da skill (os zips estão nesta pasta). O ChatGPT escaneia e libera. Skills pessoais no Work: planos pagos (exceto Free/Go); também funcionam no Codex.

## Como usar

Sem comandos: peça em linguagem natural — "prospecta 10 nutricionistas em São Paulo", "redesenha os 5 melhores", "publica os sites", "manda as propostas", "quem respondeu?", "o Gianluca fechou, gera o contrato". A skill certa dispara pela descrição.

## Para testar (roteiro de validação)

1. Sobe as 6 skills e confirma que aparecem em Installed.
2. Prospecção com 3 leads → planilha no Drive + leads.md + CRM criado.
3. Redesign de 1 → página + editor + comparador.
4. Publicação via Sites → URL pública SEM login (testar em aba anônima!).
5. Proposta → rascunho no Gmail com link limpo.
6. Tarefa agendada de respostas às 9h.

*Port gerado a partir do prospector-de-sites v0.13.5 (Claude). Projetos independentes — nenhum arquivo é compartilhado.*
