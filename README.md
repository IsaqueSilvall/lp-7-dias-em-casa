# LP — 7 Dias em Casa

Página de vendas do produto digital **7 Dias em Casa**, no ar em
https://sete-dias-em-casa.vercel.app

Página única, sem build e sem framework: todo o HTML, CSS e JavaScript estão
dentro de `index.html`. As imagens de `img/` são as capturas de prova usadas
nas seções de demonstração do app.

## Arquivos

| Arquivo | O que é |
|---|---|
| `index.html` | A página inteira — estrutura, estilo, animações e os scripts de captura de lead e Pixel. |
| `img/prova-plano.png` | Captura da tela de plano do app. |
| `img/prova-calendario.png` | Captura do calendário de execução. |
| `img/prova-mapa.png` | Captura do mapa de categorias. |
| `img/prova-modelos-1.png`, `-2.png` | Capturas do arsenal de modelos. |

## Fluxo

O visitante preenche nome, e-mail e WhatsApp; a página envia o lead para a API
de entrega e encaminha para o checkout da Cakto. O Pixel do Meta registra os
eventos de página, lead e início de checkout.

## Publicar

```bash
vercel deploy --prod --yes
```

> Este repositório é só a página de vendas. O app de entrega, o conteúdo do
> produto e as apostilas ficam em repositório privado separado.
