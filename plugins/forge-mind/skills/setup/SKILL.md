---
name: setup-forge-mind
description: Liga com segurança a conta Forge Mind ao agente depois da instalação do plugin.
---

# Configurar o Forge Mind

Conclui a ligação sem pedir ao utilizador que publique uma senha, chave ou token na conversa.

1. Verifica se a ferramenta `list_maps` está disponível.
2. Se o cliente pedir uma credencial, abre `https://mind.forgelabs.pt/#app/ligar-agente`.
3. Orienta o utilizador a entrar na própria conta, escolher o cliente que usa e gerar uma chave pessoal.
4. A chave deve ser colada apenas no campo seguro de autenticação do cliente. Nunca a peças na conversa e nunca a repitas.
5. Depois da ligação, chama `list_maps`.
6. Se a lista for devolvida, confirma que a ligação está pronta.
7. Se a conta ainda estiver vazia, explica como criar gratuitamente o primeiro mapa e abre `https://mind.forgelabs.pt/#app`.
8. Depois de confirmar a ligação, ativa automaticamente o protocolo de memória da skill `forge-mind` em qualquer trabalho relevante. O utilizador não precisa de mencionar o Forge Mind.

Uma configuração só está confirmada quando `list_maps` responder com os mapas da conta autorizada.
