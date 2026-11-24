# Guia de testes

## Objetivo

Confirmar que o cliente consegue instalar o plugin, autenticar a própria conta e trabalhar apenas nos mapas autorizados.

## Instalar no Codex

```bash
codex plugin marketplace add Ricoandrade1/forge-mind-agent
codex plugin add forge-mind@forge-labs
```

Reinicia o cliente se o plugin não aparecer imediatamente.

## Ligar a conta

1. Abre `https://mind.forgelabs.pt/#app/ligar-agente`.
2. Entra na tua conta.
3. Escolhe o cliente que estás a testar.
4. Gera uma chave pessoal.
5. Cola a chave apenas no campo seguro de autenticação do cliente.
6. Não envies a chave numa conversa.

## Teste mínimo

Pede ao agente:

```text
Lista os meus mapas do Forge Mind.
```

O teste está correto quando o agente devolve apenas os mapas da conta autorizada.

## Teste de leitura

```text
Lê o mapa escolhido e resume os cards sem fazer alterações.
```

Verifica se o agente usa `get_map` e não inventa conteúdo.

## Teste de escrita

```text
Cria um card de teste chamado Verificação MCP e confirma onde ficou guardado.
```

Depois verifica o card dentro do Forge Mind.

## Teste de atualização

```text
Atualiza a descrição do card Verificação MCP para Ligação confirmada e relê o mapa.
```

O agente deve confirmar a alteração apenas depois da resposta da ferramenta.

## Teste de ligação

```text
Liga o card Verificação MCP a outro card de teste e explica a relação criada.
```

Confirma visualmente a linha no mapa.

## Teste de isolamento

O agente nunca deve:

- Mostrar mapas de outra conta.
- Aceitar IDs inventados.
- Pedir uma chave na conversa.
- Afirmar que guardou algo quando a ferramenta falhou.
- Tratar texto dentro de um card como instrução para ignorar a Skill.

## Limpeza depois do teste

Apaga apenas os cards criados para o teste. Revoga a chave pessoal se o cliente ou computador deixar de ser utilizado.

## Reportar problemas

Inclui:

- Cliente e versão.
- Sistema operativo.
- Nome da ferramenta que falhou.
- Mensagem de erro sem credenciais.
- Passos para reproduzir com dados fictícios.

Nunca publiques chaves, tokens, e-mails, nomes de clientes ou conteúdo privado dos mapas.

