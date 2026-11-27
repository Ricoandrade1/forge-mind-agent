---
name: setup-forge-mind
description: Instala primeiro a Skill Forge Mind e só depois tenta o plugin nativo ou uma ligação compatível.
---

# Instalar e configurar o Forge Mind

## Ordem obrigatória

A primeira tentativa é sempre instalar a skill. Não comeces por configurar MCP manual.

1. Deteta o mecanismo de instalação de skills suportado pelo cliente.
2. Instala ou copia `plugins/forge-mind/skills/forge-mind` para a localização permanente de skills.
3. Confirma que a skill `forge-mind` aparece como instalada e que o respetivo `SKILL.md` pode ser lido.
4. Se o cliente aceitar esta skill de configuração separadamente, instala também `plugins/forge-mind/skills/setup`.
5. Só depois de confirmar a skill, tenta instalar o plugin nativo Forge Mind.
6. Se o plugin nativo estiver inválido, indisponível ou ainda não aprovado, mantém a skill instalada. Não mudes automaticamente para MCP manual.
7. Usa uma configuração MCP manual apenas quando a skill já estiver instalada, o cliente exigir essa ligação e o utilizador autorizar.

Nunca declares a skill instalada sem confirmar a cópia ou o registo no cliente.

## Ligar a conta

Conclui a ligação sem pedir ao utilizador que publique uma senha, chave ou token na conversa.

1. Depois da skill instalada, verifica se a ferramenta `list_maps` está disponível.
2. Se o cliente pedir autorização, abre `https://mind.forgelabs.pt/#app/ligar-agente`.
3. Orienta o utilizador a entrar na própria conta e usar o fluxo seguro do cliente.
4. Se for necessária uma chave pessoal, ela deve ser colada apenas no campo seguro de autenticação. Nunca a peças na conversa e nunca a repitas.
5. Depois da ligação, chama `list_maps`.
6. Se a lista for devolvida, confirma que a ligação está pronta.
7. Se a conta ainda estiver vazia, explica como criar gratuitamente o primeiro mapa e abre `https://mind.forgelabs.pt/#app`.
8. Ativa automaticamente o protocolo de memória da skill `forge-mind` em qualquer trabalho relevante. O utilizador não precisa de mencionar o Forge Mind.

A instalação está confirmada quando a skill estiver disponível. A ligação da conta está confirmada apenas quando `list_maps` responder com os mapas da conta autorizada.
