# Nightech Catálogo Digital — PWA (protótipo funcional)

## O que já funciona
- Layout responsivo para PC, Android e iOS.
- Instalação como PWA quando servido por HTTPS/localhost.
- Catálogo com busca, filtros e ordenação.
- Seleção por clique e alteração de quantidade.
- Cadastro e login de cliente no protótipo.
- Perfil ADM demonstrativo, com inclusão/exclusão de produtos, cadastro/exclusão de vendedores, desconto geral e frete grátis.
- Carrinho e cálculo de valores parciais/totais.
- Geração de documento de pedido otimizado para PDF; o navegador abre a janela de impressão para salvar como PDF com comprador, vendedor, itens, quantidades, valores, data e horário.
- Histórico local de pedidos.
- Cache básico para funcionamento offline após o primeiro acesso.

## Como testar
1. Abra esta pasta no VS Code.
2. Use uma extensão de servidor local (ex.: Live Server) ou rode `python -m http.server 8080` dentro da pasta.
3. Acesse `http://localhost:8080`.
4. ADM de demonstração: `admin@nightech.local` / `admin123`.

## Limites intencionais do protótipo
Este primeiro pacote usa `localStorage`, portanto os dados ficam somente no navegador/dispositivo atual. Ele NÃO deve ser usado em produção para autenticação ou dados comerciais.

Para atender integralmente ao projeto (mesmo histórico em qualquer aparelho, mais de 1.000 itens, acesso por perfis, segurança e envio automático do PDF ao cliente + vendedor + gerente), a etapa de produção deve usar backend e banco central. O arquivo `docs/schema.sql` traz uma estrutura PostgreSQL já pensada para isso.

## Arquitetura recomendada para produção
- Frontend: esta PWA em HTML/CSS/JS (ou evolução para React/Vue sem necessidade imediata).
- API: Node.js/Express ou Supabase.
- Banco: PostgreSQL.
- Autenticação: sessão segura/JWT + senhas com hash; RBAC para `admin`, `seller` e `client`.
- PDFs: geração no servidor e armazenamento do arquivo por pedido.
- E-mail: SMTP/Resend/SendGrid, anexando o mesmo PDF para cliente, vendedor e gerente/ADM.
- Imagens: object storage/CDN.
- Importação do catálogo: rotina para XLSX/CSV para facilitar manutenção de centenas/milhares de produtos.

## Regras de acesso recomendadas
- Cliente: cria o próprio cadastro, compra e vê apenas seus pedidos.
- Vendedor/consultor: somente ADM cria; vê pedidos vinculados a ele.
- ADM: produtos, preços, estoque, promoções, vendedores, clientes e todos os pedidos.

## Dados iniciais
O catálogo foi iniciado com os itens disponíveis na planilha `CATÁLOGO NIGHTECH - karina.xlsx` fornecida para o projeto.

## Atualização — imagens e busca para catálogo grande

- Cada produto agora possui área de foto/imagem no card.
- O administrador pode informar uma URL de imagem ou enviar uma foto ao cadastrar o produto.
- Produtos sem foto exibem um placeholder visual automático.
- A busca ganhou botão **Buscar**, pesquisa por part number/código e descrição e pode ser limpa rapidamente.
- Os resultados são exibidos em blocos de 48 itens com **Carregar mais**, evitando renderizar 1.000+ cards de uma vez.
- No protótipo local, imagens enviadas ficam em `localStorage`; na versão de produção, devem ser armazenadas em object storage/CDN e referenciadas no banco de dados.
