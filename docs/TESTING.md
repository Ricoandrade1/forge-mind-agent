# Guia de testes

## Objetivo

Confirmar primeiro que o cliente instalou a skill Forge Mind. Depois, quando suportado, testar o plugin nativo, autenticar a própria conta e trabalhar apenas nos mapas autorizados.

## Instalação obrigatória da Skill

A ordem de teste é obrigatória:

1. Tenta primeiro o instalador de skills do cliente.
2. Instala ou copia `plugins/forge-mind/skills/forge-mind` para a pasta permanente de skills.
3. Instala `plugins/forge-mind/skills/setup` quando o cliente aceitar uma segunda skill de configuração.
4. Confirma que `SKILL.md` está disponível para o agente.
5. Reinicia ou recarrega o cliente quando necessário.
6. Só depois tenta o plugin nativo.

Prompt de validação:

```text
Instala primeiro a Skill Forge Mind deste repositório. Confirma que a skill foi copiada e pode ser lida. Só depois tenta o plugin nativo. Se o plugin for inválido ou indisponível, mantém a skill e não mudes automaticamente para MCP manual.
```

A instalação da skill está correta quando o cliente consegue encontrar e ler a regra permanente de memória em `plugins/forge-mind/skills/forge-mind/SKILL.md`.

## Plugin nativo, teste posterior

```bash
codex plugin marketplace add Ricoandrade1/forge-mind-agent
codex plugin add forge-mind@forge-labs
```

Se o plugin não aparecer, estiver inválido ou ainda não for aceite pelo cliente, regista esse resultado sem remover a skill. A skill continua a ser a instalação principal.

## MCP manual, apenas quando necessário

Não uses MCP manual como primeira tentativa. Só configura o endpoint depois da skill, quando o cliente exigir essa ligação e o utilizador autorizar.

## Ligar a conta

1. Abre `https://mind.forgelabs.pt/#app/ligar-agente`.
2. Entra na tua conta.
3. Escolhe o cliente que estás a testar.
4. Usa a autorização segura oferecida pelo cliente.
5. Se o cliente exigir uma chave pessoal, cola-a apenas no campo seguro.
6. Não envies a chave numa conversa.

## Teste mínimo

Pede ao agente:

```text
Lista os meus mapas do Forge Mind.
```

O teste está correto quando o agente devolve apenas os mapas da conta autorizada.

## Teste de memória automática

Depois de confirmar a ligação, inicia uma conversa nova e pede uma tarefa relacionada com um projeto já guardado, sem escrever as palavras Forge Mind.

```text
Continua a campanha do cliente e prepara o próximo passo.
```

O teste está correto quando o agente:

1. Usa `list_maps` e `get_map` antes de começar.
2. Trabalha com as decisões já guardadas.
3. Atualiza o card correto com o resultado e o próximo passo antes de terminar.
4. Relê o mapa e confirma a atualização.

Repete o teste com uma pergunta geral sem relação com projetos ou memória pessoal. Nesse caso, o agente não deve consultar o Forge Mind.

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

