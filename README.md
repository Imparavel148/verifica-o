# verificação — página de resultado (GitHub Pages)

Arquivos estáticos para exibir a mensagem de "Verificação concluída" após o fluxo OAuth do Discord.

Arquivos:
- docs/index.html — página principal com estilo
- docs/verification.html — fallback simples

Publicação no GitHub Pages:
1. No repositório, vá em Settings → Pages.
2. Em "Source" selecione: Branch `main` e folder `/docs`.
3. Salve. Em alguns minutos a página estará disponível em:
   `https://<seu-usuario>.github.io/verifica-o/`

Integração com o backend:
- Seu backend (Express) deve processar o OAuth e, depois de atribuir o cargo, redirecionar o usuário para:
  `https://<seu-usuario>.github.io/verifica-o/`
- Exemplo:
```js
if (roleAssigned) {
  res.redirect('https://<seu-usuario>.github.io/verifica-o/');
} else {
  res.redirect('https://<seu-usuario>.github.io/verifica-o/?error=role');
}
```

Segurança:
- Não comite tokens (client_secret, bot token). Use environment variables no host do backend.
