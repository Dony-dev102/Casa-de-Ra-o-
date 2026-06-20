# 🐾 Casa de Ração Rocha — Sistema de Auto-Atendimento via WhatsApp

> Sistema de pedidos online para pet shops e lojas de ração. O cliente navega pelo catálogo, monta o carrinho e finaliza o pedido direto pelo WhatsApp — sem nenhum app ou integração de pagamento necessária.

---

## 📋 Funcionalidades

- **Catálogo filtrável** por categoria (Cachorros, Gatos, Pássaros, Medicamentos, Acessórios)
- **Carrinho de compras** com controle de quantidade e resumo de valores
- **Taxa de entrega** configurável pelo lojista
- **Checkout completo** com nome, WhatsApp, endereço e ponto de referência
- **Formas de pagamento** PIX, Débito, Crédito e Dinheiro (com campo de troco)
- **Envio automático** via WhatsApp com mensagem já formatada para o lojista
- **Memória do cliente** — dados salvos no navegador para facilitar o próximo pedido
- **Design responsivo** otimizado para celular
- **Catálogo em JSON** — lojista atualiza preços sem precisar mexer no código

---

## 📁 Estrutura de Arquivos

```
/
├── index.html       # Página principal da loja (todo o sistema)
├── produtos.json    # Catálogo de produtos (editável pelo lojista)
└── README.md        # Este arquivo
```

---

## ⚙️ Como Configurar

### 1. Alterar dados da loja

Abra o arquivo `produtos.json` e edite o bloco `"loja"`:

```json
"loja": {
  "nome": "Casa de Ração Rocha",
  "whatsapp": "5512997503412",   ← número com DDI + DDD, sem espaços ou traços
  "taxaEntrega": 5.00,           ← taxa de entrega em reais
  "pedidoMinimo": 20.00          ← valor mínimo para aceitar pedido
}
```

> O número do WhatsApp deve estar no formato internacional: `55` (Brasil) + DDD + número. Exemplo: `5512999990000`

---

### 2. Adicionar ou editar produtos

Cada produto segue este formato no array `"produtos"`:

```json
{
  "id": "p001",              ← ID único (não repita)
  "categoria": "cachorros",  ← deve existir em "categorias"
  "nome": "Ração Premium 15kg",
  "descricao": "Ração completa para cães adultos",
  "preco": 89.90,
  "unidade": "saco",
  "disponivel": true         ← false = oculta o produto sem apagar
}
```

**Categorias disponíveis por padrão:**

| id | Nome |
|---|---|
| `cachorros` | Ração para Cachorros |
| `gatos` | Ração para Gatos |
| `passaros` | Ração para Pássaros |
| `medicamentos` | Medicamentos |
| `acessorios` | Acessórios |

Para adicionar uma nova categoria, inclua no array `"categorias"` e use o mesmo `id` nos produtos.

---

### 3. Ocultar um produto temporariamente

Basta mudar `"disponivel": true` para `"disponivel": false`. O produto some da loja sem precisar apagar.

---

## 🚀 Como Publicar (grátis)

### Opção A — GitHub Pages (recomendado)

1. Crie uma conta gratuita em [github.com](https://github.com)
2. Clique em **New repository** e dê um nome (ex: `loja-racao-rocha`)
3. Faça upload dos arquivos `index.html` e `produtos.json`
4. Vá em **Settings → Pages → Source → main → / (root)** e salve
5. Aguarde 1–2 minutos e acesse a URL gerada:
   ```
   https://seu-usuario.github.io/loja-racao-rocha
   ```

### Opção B — Netlify (arrastar e soltar)

1. Acesse [netlify.com](https://netlify.com) e crie uma conta gratuita
2. Arraste a pasta com os dois arquivos para a área de deploy
3. Pronto — URL gerada na hora

### Opção C — Hospedagem própria

Suba os dois arquivos (`index.html` e `produtos.json`) na raiz de qualquer hospedagem web tradicional (cPanel, FTP etc.).

> ⚠️ Os dois arquivos **devem estar na mesma pasta**. O `index.html` carrega o `produtos.json` via URL relativa.

---

## 📲 Configurar no WhatsApp Business

Após publicar, configure a **mensagem de saudação automática** no WhatsApp Business:

```
Olá! 😊 Seja bem-vindo à Casa de Ração Rocha! 🐾

Para fazer seu pedido de forma rápida, acesse nosso cardápio online:
👉 https://seu-usuario.github.io/loja-racao-rocha

Escolha os produtos, informe seu endereço e finalize — a mensagem chega direto aqui pra gente! 🛵
```

---

## 🔄 Como o pedido chega para o lojista

Ao finalizar o pedido, o cliente é redirecionado para o WhatsApp já com uma mensagem formatada como esta:

```
🐾 PEDIDO - Casa de Ração Rocha
━━━━━━━━━━━━━━━━━━━━

👤 Cliente: João Silva
📱 WhatsApp: (12) 99999-0000

📍 Endereço de Entrega:
Rua das Flores, nº 45 - Jardim Primavera
Referência: Próximo à padaria

📦 Itens do Pedido:
• Ração Premium Adulto 15kg ×1 → R$ 89,90
• Brinquedo Mordedor ×2 → R$ 30,00

💰 Subtotal: R$ 119,90
🛵 Taxa entrega: R$ 5,00
✅ TOTAL: R$ 124,90

💳 Pagamento: 💚 PIX

Pedido feito pelo site 🌐
```

---

## 💾 Dados Salvos no Cliente

O sistema salva automaticamente no navegador do cliente (localStorage):

- Nome
- WhatsApp
- Endereço completo (rua, número, bairro, referência)

No próximo pedido, os campos já aparecem preenchidos. Nenhum dado é enviado para servidores externos — tudo fica no próprio dispositivo do cliente.

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Uso |
|---|---|
| HTML5 + CSS3 | Interface visual |
| JavaScript (vanilla) | Lógica do carrinho e checkout |
| JSON | Catálogo de produtos |
| localStorage | Persistência dos dados do cliente |
| WhatsApp API (wa.me) | Envio do pedido formatado |

Sem frameworks, sem banco de dados, sem backend. Funciona em qualquer hospedagem estática.

---

## 📈 Roadmap — Próximas Versões

- [ ] Painel administrativo para editar produtos sem mexer no JSON
- [ ] Histórico de pedidos para o cliente
- [ ] Integração com sistema de pagamento (PIX automático)
- [ ] Versão PWA (instalável como app no celular)
- [ ] Multi-loja (uma instalação serve vários estabelecimentos)
- [ ] Área do lojista com controle de status dos pedidos

---

## 📄 Licença

Este projeto foi desenvolvido para uso comercial da **Casa de Ração Rocha**.  
Para adaptar e revender para outros estabelecimentos, mantenha a estrutura do `produtos.json` — ela foi pensada para ser o coração do produto SaaS.

---

*Cuidando bem de quem você ama! 🐾*
