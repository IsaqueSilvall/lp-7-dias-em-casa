# Checkout — Cakto

Verificação do checkout público em 03/11/2026. Esta página é hospedada e
controlada pela Cakto; o repositório da LP não controla o formulário nem os
métodos de pagamento.

**Link:** https://pay.cakto.com.br/kw79pwa_1252481

## Observado no checkout ao vivo

Teste de carregamento em viewport mobile (390 × 844) e desktop (1440 × 1000).
A página respondeu HTTP 200 nas duas resoluções, sem erros JavaScript visíveis
no navegador de teste. Nenhum formulário foi preenchido e nenhuma cobrança ou
pedido PIX foi criado.

- Produto: 7 Dias em Casa.
- Valor do produto: R$ 27,00.
- Taxa de serviço: R$ 0,99.
- Total exibido: **R$ 27,99**.
- Método padrão: PIX.
- Métodos configurados no checkout: PIX, cartão de crédito, PicPay, Google Pay
  e Apple Pay (a exibição das carteiras pode depender do dispositivo/navegador).
- Parcelamento configurado: até 6 vezes.
- Validade de PIX configurada: 3.600 segundos (1 hora).
- Campo de cupom: habilitado (`showCouponField: true`), embora não haja cupom de
  campanha atribuído ao link observado (`campaignCoupon: null`).
- Desconto PIX: nenhum configurado.
- Order bumps: nenhum configurado.
- Upsell: desativado.
- Campos visíveis: nome, e-mail, confirmação de e-mail, celular e CPF/CNPJ.

### Campos e atrito

O formulário apresenta confirmação de e-mail duplicada. Os campos aparecem sem
o atributo HTML `required` no DOM observado; isso **não comprova** que a
validação da Cakto permita concluir o pedido sem algum deles.

O campo CPF/CNPJ usa o placeholder “Preencha para emitir sua nota fiscal”.
Portanto, a afirmação anterior de que o CPF é obrigatório para gerar PIX não
está comprovada. É necessário confirmar a validação no fluxo oficial da Cakto
ou com o suporte, sem criar pedidos de teste na conta de produção.

## Pixel e conversões

O checkout carrega o mesmo Pixel ID presente na LP:

`1553546152077434`

A documentação da Cakto informa que o checkout deve enviar
`InitiateCheckout` ao abrir e `Purchase` após a aprovação do pagamento. Para
PIX pago depois da geração, a documentação informa que o evento de compra
confirmada precisa da API de Conversões/token configurado.

No teste automatizado, confirmei que o Pixel ID é carregado, mas não consegui
verificar um evento `InitiateCheckout` chegando ao Meta. Isso precisa ser
validado em **Testar eventos** no Events Manager e no Pixel Helper antes de
remover o evento manual provisório da LP. Também é necessário conferir que
`Purchase` represente pagamento aprovado, não PIX apenas gerado.

Documentação Cakto:
- Pixel e API de Conversões:
  https://ajuda.cakto.com.br/pt-br/articles/56-como-configurar-o-pixel-do-facebook-na-cakto
- Ocultar campo de cupom:
  https://ajuda.cakto.com.br/pt-br/articles/31-como-criar-e-configurar-cupons-de-desconto-na-cakto
- Personalizar checkout:
  https://ajuda.cakto.com.br/pt-br/articles/75-como-realizar-a-personalizacao-do-checkout

## Ajustes recomendados no painel Cakto

1. Ocultar o campo de cupom enquanto não houver uma campanha de cupom pública.
2. Personalizar cores e logotipo para manter a identidade visual da LP, priorizando
   a versão mobile e preservando a leitura do total de R$ 27,99.
3. Confirmar com a Cakto se a confirmação de e-mail pode ser desativada e se
   CPF/CNPJ é realmente obrigatório para cada método de pagamento.
4. Configurar o token da API de Conversões e validar o `Purchase` de PIX pago.
5. Conferir no Events Manager se há duplicidade de `InitiateCheckout` entre LP
   e checkout antes de alterar o código de rastreamento.

**Limite da auditoria:** nenhum pagamento foi realizado, nenhum pedido PIX foi
gerado e não foram enviados dados pessoais durante a verificação. A leitura
da interface e da configuração pública não substitui um teste de compra
controlado nem a confirmação de regras internas da Cakto.
