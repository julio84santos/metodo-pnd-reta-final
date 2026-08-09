# Landing Page — Método PND Reta Final

Página única (`index.html`) com duas colunas de preço:

- **Pacote Essencial — R$ 19,90**: peças 1 a 10 do método (mapas, discursiva, simulado geral, planner, revisão ativa, painel de desempenho, reta final, checklist, radar legislativo, guia de uso).
- **Pacote Completo + Atualizações — R$ 24,90**: tudo do Essencial + os 5 volumes de Simulados Específicos por área + Banco Turbo (120 questões) + Discursiva Intensiva + qualquer material novo lançado depois (sem custo extra).

## Identidade visual e gatilhos de conversão

- **Cores (v2)**: troquei o fundo escuro/saturado por um layout claro, já que pesquisas de UX (CXL, OptinMonster, Usertesting) mostram que o que mais converte não é uma cor específica, e sim o contraste do botão contra o fundo, e que fundos escuros com muitas cores fortes cansam a leitura e reduzem a permanência na página.
- **Cores (v3 — logo real)**: você enviou a logo oficial "Prova Nacional Docente" (capelo com losango amarelo e aba verde, texto azul). Extraí as cores exatas da imagem — azul `#3657A5`, verde `#00A758`, amarelo `#E0A800`/`#FFCC29` — e apliquei: azul para texto/ícones, verde no botão de compra (também é cor de "ação positiva" e tem ótimo contraste em fundo claro), amarelo em detalhes do plano "Completo" (borda, ribbon). A logo está no arquivo `logo-pnd.png`, referenciada no topo da página.
- ⚠️ **Atenção**: essa é a logo real do concurso (PND/INEP/MEC). Como o produto é material de apoio extraoficial (não é do INEP), mantive o aviso "material extraoficial, sem vínculo com INEP/MEC" logo abaixo da logo no cabeçalho — isso ajuda a evitar que a página pareça uma comunicação oficial do governo, o que poderia gerar problema de uso indevido de marca. Se quiser remover essa logo depois por segurança jurídica, é só apagar o bloco `<div class="seal">...</div>` no `index.html` (aparece 2x: no topo fixo e no cabeçalho principal).
- **Contador regressivo real** até 20/09/2026 (data oficial da prova) — gera urgência genuína, não fictícia.
- **Ancoragem de preço**: preço riscado (R$ 49,90 → R$ 19,90 no Essencial; R$ 59,90 → R$ 24,90 no Completo) com selo "% OFF". Ajuste esses valores em `index.html` (seção `#planos`) se decidir usar outro preço "de".
- **Barra de confiança**: ícones de pagamento seguro, atualização com o edital e liberação imediata — reduzem a percepção de risco da compra.
- Não incluí depoimentos ou números de alunos fictícios, por decisão sua — se quiser adicionar prova social real depois, há espaço reservado na seção de planos.

## Atualização final — pesquisa de conversão em infoprodutos

Pesquisei cases e boas práticas de páginas de venda de infoproduto (Hotmart, CXL, casos de A/B test de 2025/2026) e apliquei:

- **Múltiplos CTAs ao longo da página**: antes só existiam os 2 botões de compra dentro dos cards de preço. Agora tem: barra fixa no topo (desktop), botão logo no hero ("Quero garantir meu acesso agora"), banners de chamada após as seções "Por que funciona", "Como funciona" e "O que tem dentro", mais um no fim do FAQ, e a barra fixa no rodapé (mobile). Um case de 2025 (Fuel Your Digital) mediu +32% em conversões só por adicionar um CTA no meio do conteúdo, depois de dar contexto antes de pedir a ação.
- **Copy dos botões em primeira pessoa**: troquei "Quero o Pacote X" por "Quero garantir meu Pacote X" — testes de CTA mostram que a primeira pessoa ("meu", "minha") converte mais do que a segunda pessoa genérica.
- **Garantia de 7 dias**: adicionei um bloco de garantia incondicional entre os planos e o FAQ, mais uma linha em cada card de preço e no rodapé. Garantia é um dos "blocos obrigatórios" de página de vendas segundo o guia da Hotmart — reduz a sensação de risco na hora de decidir.
- **Navegação fixa no topo (desktop)**: com atalhos para as seções e um botão de compra sempre visível, sem depender de rolar até o fim.

Todos os novos botões de CTA "genéricos" (banners no meio da página, barra do topo, sticky mobile) apontam para `#planos` — a seção de preços — porque eles servem para trazer o visitante até a decisão de compra. Os botões dentro dos cards de preço (`#link-plano-1` e `#link-plano-2`) continuam sendo os únicos que precisam do link de checkout real.

## Links de checkout

Já configurados no `index.html`:

- **Pacote Essencial** → botão "Quero garantir meu Pacote Essencial" aponta para `https://pay.hotmart.com/C107081055O` (link "Reta Final")
- **Pacote Completo** → botão "Quero garantir meu Pacote Completo" aponta para `https://pay.hotmart.com/Y107081480X?checkoutMode=10` (link "Supercombo Reta Final")

Se algum dia precisar trocar, procure por `cta-plano-1` e `cta-plano-2` no `index.html` — são os únicos dois links de compra reais da página; todos os outros botões ("Quero garantir meu acesso", banners no meio da página, barra do topo) só rolam a tela até a seção `#planos`, onde estão esses dois botões.

## Como publicar no GitHub Pages

1. Crie um repositório novo no GitHub (ex: `metodo-pnd-2026`), público.
2. Suba os arquivos `index.html`, `logo-pnd.png` e `comparativo-metodo.png` juntos, para a raiz do repositório (pelo site do GitHub: "Add file" → "Upload files"). Todos precisam estar na mesma pasta, senão as imagens não aparecem.
3. No repositório, vá em **Settings → Pages**.
4. Em "Build and deployment", escolha **Source: Deploy from a branch**.
5. Em "Branch", selecione `main` e pasta `/ (root)`, depois clique em **Save**.
6. Aguarde 1–2 minutos. Sua página ficará disponível em:
   `https://SEU-USUARIO.github.io/metodo-pnd-2026/`

## Domínio próprio (opcional)

Se quiser usar um domínio próprio (ex: `metodopnd.com.br`):
1. Crie um arquivo `CNAME` na raiz do repositório contendo apenas o domínio.
2. Configure o DNS do domínio apontando para o GitHub Pages (registro CNAME para `SEU-USUARIO.github.io`, ou registros A para os IPs do GitHub Pages).
3. Em Settings → Pages, adicione o domínio customizado e ative "Enforce HTTPS".

## Editando conteúdo depois

Todo o texto e preço estão diretamente no HTML, nas seções `#planos` (preços/planos) e `#conteudo` (lista de materiais). É só editar o texto entre as tags.
