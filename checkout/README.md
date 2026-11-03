# Checkout — Cakto

O que o comprador vê depois de clicar no CTA da LP. Hospedado pela Cakto em
`https://pay.cakto.com.br/kw79pwa_1252481` — a página não é nossa, é o
checkout padrão da plataforma, então o que dá para controlar é o produto, o
preço e o que a LP promete antes de chegar aqui.

## Estrutura da página, de cima para baixo

1. **Cabeçalho** — miniatura da capa do produto + nome "7 Dias em Casa".
2. **Apple Pay** — botão preto de largura total, acima de tudo, com um
   divisor "OU" separando do formulário.
3. **Formulário**, nesta ordem:
   - Nome completo
   - Email
   - Confirme seu email (campo duplicado, atrito extra)
   - Celular (seletor de país, padrão +55) e CPF/CNPJ, lado a lado
4. **Forma de Pagamento** — quatro cartões em linha: **PIX** (selecionado por
   padrão, verde-escuro), Cartão de Crédito, PicPay, Google Pay.
5. **Resumo do pedido** — campo de cupom ("Código de desconto" + "Aplicar
   Cupom") e a composição do preço.
6. **CTA** — botão verde-escuro de largura total, "Gerar PIX" (o texto muda
   conforme a forma de pagamento escolhida).
7. **Rodapé** — selo "Compra segura", link para Termos de uso de 7 Dias em
   Casa e Termos e Políticas da Cakto, e "Processado por Cakto".

## Composição do preço

| Linha | Valor |
|---|---|
| 7 Dias em Casa | R$ 27,00 |
| Taxa de serviço | R$ 0,99 |
| **Total** | **R$ 27,99** |

## Pontos de atrito conhecidos

- **A taxa de serviço quebra a promessa da LP.** A página de vendas anuncia
  R$ 27 como preço final; o checkout cobra R$ 27,99. São 99 centavos, mas a
  surpresa aparece no momento exato da decisão, que é o pior lugar para ela
  estar.
- **CPF é obrigatório** para gerar o PIX. É exigência da plataforma, não
  nossa, mas é um campo a mais entre o clique e o pagamento.
- **Confirmação de e-mail duplicada** — mais um campo em um formulário que
  já tem cinco.
- **PIX vem pré-selecionado.** Combina com o público, mas significa que o
  comprador precisa sair da página, abrir o banco e voltar; a conversão
  depende do que acontece fora do nosso controle.

## Captura

A captura real da tela está pendente: a que eu tinha em mãos continha dados
pessoais reais (nome, e-mail, celular e CPF) e não pode ir para um
repositório público sem tarja.
