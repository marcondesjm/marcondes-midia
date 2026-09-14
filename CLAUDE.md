# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

---

## **1. Projeto e Estrutura**
Este repositório contém o site institucional e de alta conversão para a **Marcondes Mídia**, uma agência focada em entregar landing pages profissionais de alta performance e tráfego pago para negócios locais.

### **1.1. Arquitetura Geral**
- **Modelo Estático**: O site é estático, leve e otimizado, sem necessidade de etapas de build ou servidores dinâmicos de backend.
- **Estrutura de Arquivos Principal**:
  - `index.html`: Centraliza todo o conteúdo, a marcação (HTML5), estilização responsiva (Tailwind CSS) e os scripts de interatividade (JavaScript).
  - `assets/`: Armazena todos os recursos visuais (imagens de portfólio em `.webp` e panfletos digitais em `.png`).
  - `.vercel/project.json`: Configurações de vinculação do projeto com a plataforma de hospedagem Vercel.

### **1.2. Estrutura de Pastas**
```
marcondes-midia/
├── index.html                  # Página principal do site (único arquivo HTML)
├── CLAUDE.md                   # Diretrizes e arquitetura do projeto para IAs (este arquivo)
├── .gitignore                  # Regras de exclusão do controle de versão (ex: ignora .vercel/)
├── assets/                     # Pasta de recursos estáticos e imagens
│   ├── flyer-novo.png          # Flyer promocional principal exibido na seção demonstrativa
│   ├── flyer-novo_.png         # Backup/alternativa do flyer promocional
│   ├── viacivil_cover.webp     # Capa do portfólio: Via Civil
│   ├── elgmanutencao_cover.webp# Capa do portfólio: ELG Manutenção
│   ├── grupogplan_cover.webp   # Capa do portfólio: Grupo Gplan
│   ├── spmserralheria24hs_cover.webp # Capa do portfólio: SPM 24hs
│   ├── cintiterraplanagem_cover.webp # Capa do portfólio: Cinti Terraplanagem
│   └── remistech_cover.webp    # Capa do portfólio: Remistech
└── .vercel/                    # Configurações do Vercel (Ignorado pelo Git)
    └── project.json            # Metadados do projeto na Vercel (ID, Org e Nome)
```

---

## **2. Mapeamento do Portfólio (Os 6 Cards)**
A seção de portfólio destaca seis cases reais criados pela Marcondes Mídia. Abaixo está o mapeamento exato dos cards no HTML e seus respectivos assets de imagem:

| # | Projeto | Imagem Associada | Badge de Destaque / Especialidade |
|---|---------|------------------|----------------------------------|
| 1 | **Via Civil** | `assets/viacivil_cover.webp` | Sinalização viária de alta qualidade |
| 2 | **ELG Manutenção** | `assets/elgmanutencao_cover.webp` | Agendamentos via WhatsApp |
| 3 | **Grupo Gplan** | `assets/grupogplan_cover.webp` | Credibilidade para fechar obras |
| 4 | **SPM 24hs** | `assets/spmserralheria24hs_cover.webp` | Destaque em Serviços locais |
| 5 | **Cinti Terraplanagem** | `assets/cintiterraplanagem_cover.webp` | Posicionamento forte na região |
| 6 | **Remistech** | `assets/remistech_cover.webp` | Mais conversões e leads |

---

## **3. Tecnologias e Configurações**

### **3.1. Estilização com Tailwind CSS**
- O Tailwind CSS é carregado em tempo de execução via CDN oficial no `index.html`:
  ```html
  <script src="https://cdn.tailwindcss.com"></script>
  ```
- Configuração estendida aplicada na tag `<script>` de cabeçalho:
  ```javascript
  tailwind.config = {
      theme: {
          extend: {
              fontFamily: {
                  sans: ['Inter', 'sans-serif'],
              },
              colors: {
                  brand: {
                      dark: '#0F172A',      // Slate 900 para fundo escuro e textos
                      light: '#F8FAFC',     // Slate 50 para fundo claro principal
                      green: '#22C55E',     // Green 500 para CTAs principais (WhatsApp / Vendas)
                      greenHover: '#16A34A',// Green 600 para efeito hover dos botões
                  }
              }
          }
      }
  }
  ```

### **3.2. Script e Lógica do Formulário de Avaliação Gratuita**
O formulário de diagnóstico (`#evaluation-form`) utiliza JavaScript puro para implementar um fluxo de dupla confirmação antes de redirecionar para o WhatsApp.
- **Funcionamento (Modo de Pré-visualização / Preview Mode)**:
  - **Passo 1**: O usuário preenche o nome da empresa e o número do WhatsApp e clica no botão.
  - **Passo 2**: O script intercepta o envio (`e.preventDefault()`), monta a mensagem estruturada e exibe uma caixa de confirmação visual (`#preview-box`) preenchida com o texto (`#preview-text`). O botão de envio muda de cor (de `bg-brand-green` para o tom de alerta `bg-amber-500`) e exibe o texto: *"Confirmar e Enviar no WhatsApp 🚀"*.
  - **Passo 3**: Ao clicar no botão em estado de pré-visualização, o script codifica a mensagem com `encodeURIComponent`, abre o link do WhatsApp (`https://wa.me/554896029392?text=...`) em uma nova aba e reseta o formulário para seu estado inicial.

---

## **4. Regras de Edição e Contribuição**

### **4.1. Edição do HTML e Estilos**
- **Centralização**: Como não há build ou modularização, todas as alterações de marcação, textos e scripts devem ser feitas diretamente no `index.html`.
- **Efeitos de Hover e Transição**: Sempre inclua classes de transição do Tailwind (`transition duration-200`) em botões, links e cards para manter a experiência de navegação polida e profissional.

### **4.2. Links de Integração Externa**
Todas as ações de conversão redirecionam para canais específicos:
- **WhatsApp Oficial**: `https://wa.me/554896029392` (utilizado no cabeçalho, botão flutuante, planos e formulário).
- **Checkout de Pagamento (Kiwify)**: `https://pay.kiwify.com.br/g4df72A` (utilizado em todos os botões de compra da Landing Page por R$ 119,90).
- **Instagram**: `https://www.instagram.com/marcondes.machado.oficial/`.

### **4.3. Regras de Otimização de Assets**
- **Formato WebP**: Novas capas de portfólio devem ser adicionadas na pasta `assets/` preferencialmente em formato `.webp` para garantir compressão eficiente e tempos mínimos de carregamento.
- **Proporção**: As imagens do portfólio seguem uma proporção aproximada de tela de computador (ex: `1407x767`). Mantenha a proporção de paisagem (landscape) com a propriedade de classe CSS `w-full h-48 object-cover` nos cards do portfólio para evitar distorções.

---

## **5. Manutenção e Cuidados de Operação**

### **5.1. Cuidados com Duplicações**
- Atente-se à marcação de elementos repetitivos como os benefícios abaixo dos botões de CTA (*"Garantia de 7 dias"*, *"Entrega em 48h"*, etc.) para manter consistência em toda a página e evitar repetições desnecessárias.

### **5.2. Deploy Continuo**
- A hospedagem do site é realizada de forma serverless e estática na Vercel.
- O arquivo `.vercel/project.json` possui as chaves de vínculo do deploy. **Nunca apague ou altere este arquivo**, a menos que precise mover o projeto para outra conta/organização Vercel. Ele é explicitamente ignorado no controle de versão pelo `.gitignore`.

### **5.3. Testes Rápidos**
- Devido à natureza estática, para testar as alterações locais basta abrir o arquivo `index.html` diretamente em qualquer navegador moderno ou rodar um servidor HTTP local simples de forma rápida:
  ```bash
  python -m http.server 8000
  ```
