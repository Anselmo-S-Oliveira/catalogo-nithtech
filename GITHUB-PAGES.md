# Publicação no GitHub Pages

## 1. Crie o repositório
Sugestão de nome: `nightech-catalogo`

Para usar GitHub Pages gratuitamente, mantenha o repositório público.

## 2. Envie todos os arquivos desta pasta para a raiz do repositório
O `index.html` deve ficar na raiz.

## 3. Ative o GitHub Pages
No repositório:

Settings > Pages > Build and deployment > Source > GitHub Actions

## 4. Aguarde o workflow
Abra a aba `Actions`. O workflow `Deploy to GitHub Pages` será executado automaticamente após um push na branch `main`.

## URL esperada
Se o usuário GitHub for `seuusuario` e o repositório `nightech-catalogo`:

`https://seuusuario.github.io/nightech-catalogo/`

## Atualizações futuras
Depois de editar qualquer arquivo:

```bash
git add .
git commit -m "Atualiza catálogo"
git push
```

O GitHub Pages republicará automaticamente.

## Importante
GitHub Pages hospeda somente a camada estática do catálogo. Cadastro real compartilhado entre dispositivos, banco de dados, autenticação segura, permissões de administrador, histórico central e envio automático de pedidos por e-mail exigem um backend externo.
