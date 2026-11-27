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
7. Usa uma configuração MCP manual apenas quando a skill já estiver instalada, ou quando o cliente tiver confirmado que não suporta Skills persistentes e exigir essa ligação.
8. Uma cópia numa pasta temporária não conta como instalação.
9. Se não houver escrita persistente, não pares e não devolvas uma lista de escolhas. Avança automaticamente para o próximo método compatível e pede apenas a ação manual indispensável ao utilizador.

Nunca declares a skill instalada sem confirmar a cópia ou o registo no cliente.

## Fluxos específicos

- No Claude.ai, não clones para uma pasta temporária. Orienta uma única ação: enviar o ficheiro `https://mind.forgelabs.pt/forge-mind-skill.zip` em Definições, Capacidades, Skills, Upload Skill. Depois da confirmação, continua automaticamente para o conector da conta.
- No Gemini CLI, instala em `~/.gemini/skills/forge-mind` ou `~/.agents/skills/forge-mind`, executa `/skills reload` e confirma com `/skills list`. Depois adiciona a ligação MCP compatível e testa `list_maps`.
- No Gemini web, não afirmes que instalaste uma Skill local. Se Aplicações personalizadas estiver disponível, adiciona o servidor do Forge Mind. Caso contrário, informa o limite e encaminha diretamente para o Gemini CLI.
- Em Codex, OpenCode e clientes com escrita persistente, copia primeiro a Skill e confirma o `SKILL.md`.
- Em qualquer cliente, não pares apenas porque a primeira forma de instalação não está disponível.

## Ligar a conta

Conclui a ligação sem pedir ao utilizador que publique uma senha, chave ou token na conversa.

1. Depois da skill instalada, verifica se a ferramenta `list_maps` está disponível.
2. Se o cliente pedir autorização, abre `https://mind.forgelabs.pt/#app/ligar-agente`.
3. Orienta o utilizador a entrar na própria conta e usar o fluxo seguro do cliente.
4. Se for necessária uma chave pessoal, ela deve ser colada apenas no campo seguro de autenticação. Nunca a peças na conversa e nunca a repitas.
5. Depois da ligação, chama `list_maps`.
6. Se a lista for devolvida, confirma que a ligação está pronta.
7. Se a conta ainda estiver vazia, explica como criar gratuitamente o primeiro mapa e abre `https://mind.forgelabs.pt/#app`.
8. Ativa automaticamente o protocolo permanente da skill `forge-mind`. Em todo comando de trabalho, a entrada deve consultar o Forge Mind antes de agir e a saída deve atualizar e confirmar o Forge Mind antes da resposta final. O utilizador não precisa de voltar a mencionar o Forge Mind.

A instalação está confirmada quando a skill estiver disponível. A ligação da conta está confirmada apenas quando `list_maps` responder com os mapas da conta autorizada. A partir desse momento, a consulta na entrada e a atualização na saída tornam-se o comportamento padrão do agente, exceto quando o utilizador mandar não consultar ou não guardar.
