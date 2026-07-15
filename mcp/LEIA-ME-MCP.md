# Prospector CRM — MCP (modo avançado)

Um servidor MCP local que dá à IA **ferramentas de verdade** para administrar o CRM do Prospector de Sites — o MESMO `prospector.db` do dashboard. Funciona no **ChatGPT (Work/Codex)** e no **Claude (Desktop/Cowork)** ao mesmo tempo: um banco, duas IAs.

**É opcional**: o plugin e as skills funcionam sem ele. Com ele, a IA nunca "esquece" de atualizar o CRM — atualizar lead vira ferramenta, não passo de arquivo.

## 9 ferramentas

listar_leads · obter_lead · salvar_lead · atualizar_status · registrar_fechamento (só com valor confirmado pelo usuário) · followups_pendentes · registrar_followup · resumo_financeiro · regenerar_dashboard

## Instalação (3 passos, ~2 min)

**1. Dependência** (uma vez): duplo clique em `instalar-mcp.bat` (Windows) ou `instalar-mcp.command` (Mac). — Requisito: Python, o mesmo do dashboard.

**2. Copie `prospector-mcp.py`** para a SUA pasta de trabalho do Prospector (a que tem o `prospector.db`).

**3. Registre na IA:**

### ChatGPT (Work/Codex)
Plugins → MCPs → **Conectar a um MCP personalizado**:
- **Nome**: `prospector-crm`
- **Tipo**: STDIO
- **Comando para iniciar**: no Windows, use o CAMINHO COMPLETO do python.exe — à prova de erro (ex.: `C:\Users\voce\AppData\Local\Programs\Python\Python312\python.exe`; descubra o seu com `where python` no cmd). No Mac: `python3`.
- **Argumentos**: `prospector-mcp.py`
- **Diretório de trabalho**: o caminho da sua pasta (ex.: `C:\Users\voce\Desktop\Clientes`)
- Salvar. Pronto — pergunte "resumo financeiro do meu CRM" pra testar.

### Claude (Desktop/Cowork)
Abra o arquivo de configuração (Configurações → Desenvolvedor → Editar configuração) e adicione em `mcpServers`:
```json
{
  "mcpServers": {
    "prospector-crm": {
      "command": "python",
      "args": ["prospector-mcp.py", "--pasta", "C:\\Users\\voce\\Desktop\\Clientes"],
    }
  }
}
```
(Mac: `"command": "python3"` e o caminho no formato `/Users/voce/Clientes`.) Reinicie o Claude. As 9 ferramentas aparecem nos conectores.

## Deu "não encontrei o CRM"?

1. Confirme que o `prospector-mcp.py` está DENTRO da pasta apontada no Diretório de trabalho.
2. Troque o comando `python` pelo caminho completo do python.exe (acima).
3. Desligue e ligue o toggle do servidor e teste numa conversa NOVA.
4. O app do ChatGPT é novo e tem bugs conhecidos de MCP — se tudo acima estiver certo, atualize o app e tente de novo.

## Teste rápido sem IA

`python prospector-mcp.py --teste` → deve terminar com `AUTOTESTE OK`.

## Segurança

Roda 100% local (STDIO — sem porta aberta, sem internet). Lê e grava apenas o `prospector.db` da pasta indicada. A IA não consegue marcar `fechado` sem valor confirmado — regra embutida na ferramenta.
