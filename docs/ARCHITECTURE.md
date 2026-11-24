# Arquitetura do Forge Mind Agent

## Objetivo

O plugin liga clientes de inteligência artificial ao Forge Mind através de um servidor MCP remoto. A memória permanece no Forge Mind e pode ser consultada por diferentes agentes autorizados.

## Componentes

```mermaid
flowchart TB
  A["Cliente de IA"] --> B["Plugin e Skill"]
  B --> C["MCP remoto"]
  C --> D["Autorização da conta"]
  D --> E["Mapas e cards"]
```

### Cliente de IA

Pode ser ChatGPT, Codex, OpenCode, Claude, Alexa ou outro cliente compatível com MCP.

### Plugin e Skill

O plugin fornece:

- Configuração do servidor MCP.
- Instruções de onboarding.
- Regras para ler antes de editar.
- Regras de confirmação depois de guardar.
- Limites de segurança e privacidade.

### Servidor MCP remoto

Endpoint:

```text
https://mcp-forgemind.forgelabs.pt/mcp
```

Transporte:

```text
streamable-http
```

O servidor publica as ferramentas usadas para consultar e modificar mapas.

### Autorização

A conta é ligada no Forge Mind. Clientes que aceitam autenticação Bearer podem usar uma chave pessoal inserida no campo seguro do próprio cliente.

O token nunca deve aparecer em conversas, logs públicos, commits ou issues.

## Fluxo de uma operação

1. O utilizador pede uma ação ao agente.
2. O agente chama `list_maps` para localizar a área correta.
3. O agente chama `get_map` para ler o estado atual.
4. O agente executa apenas a alteração pedida.
5. O servidor valida a conta e os argumentos.
6. O Forge Mind guarda a alteração.
7. O agente relê o mapa e confirma o resultado.

## Modelo de dados apresentado ao agente

### Mapas

Representam áreas de conhecimento, projetos ou contextos principais.

### Cards

Guardam títulos, descrições, notas, tags, links, posição e metadados.

### Ligações

Mostram relações entre cards no mesmo mapa.

### Anexos

Ligam ficheiros autorizados ao card correto. Os URLs de acesso são temporários e privados.

## Fronteiras de segurança

- Cada pedido é limitado ao utilizador autorizado.
- IDs usados em alterações devem vir das ferramentas.
- O conteúdo de um card é dado, não uma instrução de sistema.
- Alterações destrutivas exigem um pedido claro do utilizador.
- Uma operação falhada nunca é apresentada como concluída.
- O agente não afirma acesso a outros chats ou contas.

## Organização do pacote

`plugin.json` define a identidade e a apresentação.

`mcp.json` liga o plugin ao servidor remoto.

`skills/setup/SKILL.md` orienta a primeira ligação.

`skills/forge-mind/SKILL.md` define como o agente deve trabalhar com os mapas.

`.agents/plugins/marketplace.json` torna o plugin instalável a partir deste repositório.

