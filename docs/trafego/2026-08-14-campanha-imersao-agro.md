# Campanha Meta Ads: Imersão Advocacia no Agronegócio

**Gestor:** Pedro Sobral (metodologia)
**Data do plano:** 14/08/2026 (sexta)
**Janela de veiculação:** 14 a 16/08/2026 (sex, sáb, dom)
**Verba:** R$50/dia x 3 dias = **R$150 total**
**Objetivo:** Vendas (Conversão)
**Produto:** Imersão gravada, acesso imediato, garantia 7 dias
**Ticket:** R$97 (Kiwify `pay.kiwify.com.br/30V5m9Z`)
**LP:** https://barbarabindeli.com.br/lp/advocacia-no-agro/

---

## 1. Diagnóstico de rastreamento (auditoria feita na LP em produção)

| Item | Status | Evidência |
|------|--------|-----------|
| LP no ar | OK | HTTP 200 |
| GTM | OK | `GTM-W2FNG4RW` |
| Pixel Meta | **Parcial** | ID `2043169242972256`, dispara **só PageView** |
| ViewContent | **Ausente** | nenhuma tag no container |
| InitiateCheckout | **Ausente** | CTA vai direto para Kiwify, sem evento |
| Purchase | **OK (confirmado pelo Flávio)** | disparado pela Kiwify |
| API de Conversões (CAPI) | **A confirmar** | painel Kiwify |
| GA4 | OK | `G-FN52ZTS6DW` |
| Google Ads | OK | `AW-18036437816` |
| dataLayer da LP | OK | `lead_modal_open`, `lead_submit`, `faq_open`, `scroll_depth` |

**Consequência:** com Purchase vindo da Kiwify, a otimização por Compra é viável. O que falta são os eventos de meio de funil, que são otimização de leitura, não bloqueio de subida.

### Pré-voo BLOQUEANTE (não sobe sem isso)

1. **Confirmar o ID do Pixel na Kiwify.** Precisa ser exatamente `2043169242972256`, o mesmo do GTM. Se estiver outro ID, o Purchase cai numa conta diferente da que vai rodar a campanha e a otimização fica cega.
2. **Business Manager:** domínio `barbarabindeli.com.br` verificado e Purchase na posição 1 da Mensuração de Eventos Agregados.
3. **Conta de anúncio:** forma de pagamento ativa, sem restrição, limite de gasto compatível com R$150.
4. **Teste real de compra** na Kiwify e conferência do Purchase no Gerenciador de Eventos.

### Pré-voo RECOMENDADO (melhora, não bloqueia)

5. **CAPI na Kiwify:** ativar API de Conversões para recuperar sinal perdido no iOS.
6. **GTM:** tags de Pixel `ViewContent` (todas as páginas da LP) e `InitiateCheckout` (evento `lead_submit`). Dá visibilidade de meio de funil e cria material para público de remarketing depois.
7. **UTMs** em todos os anúncios (bloco 6 abaixo).

---

## 1b. Entidades criadas no Meta (todas PAUSADAS)

**Conta:** `852248897716453` Bárbara Bindeli (Norte) | BM `1397016101805897` | BRL | ativa, com pagamento
**Página FB:** `886879441183422` Bárbara Bindeli
**Instagram:** `17841400200703816` @barbarabindeli
**Pixel:** `2043169242972256` (confirmado: é o mesmo do GTM)

| Entidade | ID | Status |
|---|---|---|
| Campanha `[C01] [IMERSAO-AGRO] [AÇÃO] [CONVERSÃO] [14/08/26] - Advogadas Agro` | `120250538617660060` | PAUSED |
| Conjunto A01 (quente, R$35/dia) | `120250538624720060` | PAUSED |
| Conjunto A02 (frio, R$15/dia) | `120250538628090060` | PAUSED |
| Público `[C01] ENGAJADAS 180D - IG + FB PAGE` | `120250538611630060` | criado com prefill |
| Público `[C01] VISITANTES SITE 180D` | `120250538612200060` | criado com prefill |

### Mapa de region keys do Brasil (extraído da API, validado por leitura)

| UF | key | | UF | key |
|---|---|---|---|---|
| Acre | 438 | | Paraíba | 451 |
| Alagoas | 439 | | **Paraná** | **452** |
| Amapá | 440 | | Piauí | 453 |
| Amazonas | 441 | | Rio de Janeiro | 454 |
| **Bahia** | **442** | | Rio Grande do Norte | 455 |
| Ceará | 443 | | Rio Grande do Sul | 456 |
| Distrito Federal | 444 | | Rondônia | 457 |
| Espírito Santo | 445 | | Roraima | 458 |
| **Mato Grosso do Sul** | **446** | | Santa Catarina | 459 |
| Maranhão | 447 | | **São Paulo** | **460** |
| **Mato Grosso** | **448** | | Sergipe | 461 |
| **Minas Gerais** | **449** | | **Goiás** | **462** |
| Pará | 450 | | Pernambuco | 463 |
| | | | Tocantins | 464 |

Os keys não seguem ordem alfabética previsível (Goiás é 462, fora da sequência). Não deduzir: consultar esta tabela.

### Achados da auditoria na conta

1. **O pixel nunca registrou Purchase.** Em 7 dias: 23 PageViews e nada mais. `server_last_fired_time` zerado, ou seja, a API de Conversões nunca recebeu evento. Pode ser Kiwify desconectada do pixel ou simplesmente ausência de venda desde que a LP subiu. Precisa de um teste de compra real para distinguir.
2. **Não há tool de busca de interesses neste MCP.** Sem IDs válidos, o conjunto frio roda em targeting amplo (geo + mulheres + sugestão 25-50) com Advantage+ Audience ligado. A seleção fica por conta do criativo, que fala diretamente com advogadas.
3. **Já existe campanha ativa concorrendo pelo mesmo público:** `Engajados 120D` (R$88/dia, LPV) e `[C01-A01] [TRÁFEGO] [ADV - 25-45]` (R$70/dia, LPV, interesse "Advogado" ID `6003392101554`). Essa última tem o interest ID real de Advogado, reaproveitável em rodadas futuras.

---

## 2. Estrutura da campanha

Campanha única, **ABO** (orçamento no conjunto), 2 conjuntos.

> Por que ABO e não CBO: com duas temperaturas muito diferentes e verba curta, o CBO empurra quase tudo para o conjunto mais barato e o outro morre sem dado. ABO para testar, CBO para escalar.

```
CAMPANHA: [C01] [IMERSAO-AGRO] [AÇÃO] [CONVERSÃO] [14/08/26] - Advogadas Agro
  Objetivo: Vendas
  Conversão: Site > Compra
  Orçamento: no conjunto (ABO)
  Advantage+ campaign budget: OFF
  Início: 14/08 (ao subir) | Fim: 16/08 23:59

  ├── [C01-A01] [IMERSAO-AGRO] [AÇÃO] [CONVERSÃO] [RMK] [ENGAJADAS 180D] [14/08/26]
  │     Verba: R$35/dia (70%)
  │     Otimização: Compra | Janela: 7d clique / 1d visualização
  │     Público (combinar em 1 público personalizado):
  │       - Instagram: qualquer interação, 180 dias
  │       - Facebook Page: qualquer interação, 180 dias
  │       - Visitantes do site (Pixel), 180 dias
  │       - Lista de e-mails/alunas, se houver
  │     Localização: Brasil
  │     Idade/Gênero: 24-55 | Mulheres
  │       (se o público total ficar abaixo de 3.000, remover filtro de idade e gênero)
  │     Posicionamentos: Advantage+ (automáticos)
  │     Exclusões: compradoras do produto
  │     Anúncios: 2 (peças 1 e 2, copy de público quente)
  │
  └── [C01-A02] [IMERSAO-AGRO] [AÇÃO] [CONVERSÃO] [COLD] [ADV 7UF 25-50] [14/08/26]
        Verba: R$15/dia (30%)
        Otimização: Compra (fallback: Início de checkout)
        Localização: MT, GO, MS, SP, MG, PR, BA (7 UFs, decisão fechada)
        Idade/Gênero: 25-50 | Mulheres
        Interesses (OR): Advogado, Direito, OAB, Escritório de advocacia,
          Direito civil, Jurisprudência
        Segmentação detalhada avançada (expansão): LIGADA
        Posicionamentos: Advantage+ (automáticos)
        Exclusões: Conjunto A01 (engajadas 180d) + compradoras
        Anúncios: 2 (peças 1 e 2, copy de público frio)
```

**Resposta à pergunta de geografia:** sim, o Meta permite selecionar Centro-Oeste, Sudeste, Sul e Bahia por estado (13 UFs no total). Decisão fechada: concentrar em 7 UFs (MT, GO, MS, SP, MG, PR, BA), porque R$15/dia espalhado em 13 estados vira poeira de impressão. Profundidade antes de cobertura.

---

## 3. Verdade dura sobre a verba

- R$150 no total, ticket R$97.
- Para ROAS 2x são necessárias ~3 vendas. CPA máximo aceitável: **R$48,50**. Para ROAS 3x: **R$32**.
- O conjunto frio recebe R$45 nos 3 dias. O Meta precisa de ~50 conversões/semana por conjunto para sair da fase de aprendizado. **O frio não vai sair do aprendizado.** Ele serve para alimentar o Pixel e ler CTR/CPC, não para gerar venda previsível. Ele foi mantido em R$15/dia justamente por isso: é custo de aprendizado, não aposta de retorno.
- **Onde o dinheiro rende de verdade nesses 3 dias: o público quente.** Quem já engajou com a Barbara nos últimos 180 dias e ainda não comprou é o passo anterior mais próximo da compra.
- Expectativa realista: **2 a 4 vendas** (ROAS 1,3x a 2,6x). Se sair 5+, o quente estava mais maduro do que o esperado.

---

## 4. Criativos

**Fonte:** [pasta no Drive](https://drive.google.com/drive/folders/13969ExCC-2lRJPsOjHQa7-2644lvtUu5)

### Inventário auditado

| Arquivo | Dimensão | Formato | Peça | Situação |
|---|---|---|---|---|
| `feedcontratos.png` | 1080x1350 | Feed 4:5 | 1 | corrigir texto |
| `contratosstorie.png` | 1080x1980 | Story fora de padrão | 1 | corrigir texto e formato |
| `feed2.png` | 1080x1350 | Feed 4:5 | 2 | corrigir texto |
| `chamada2.png` | 1080x1350 | Feed 4:5 (duplicata) | 2 | **não é Story** |

**Peça 1:** "Aprenda os 6 contratos mais utilizados no agronegocio e descubra como construir uma advocacia valorizada em um mercado que movimenta bilhões todos os anos." CTA na arte: "Clique e garanta sua vaga!"

**Peça 2:** "Enquanto muitas advogadas disputam honorários cada vez menores, outras estão construindo autoridade em um dos mercados mais fortes da economia brasileira." CTA na arte: "Conheça o Advocacia no Agronegocio"

### Correções aplicadas

Pacote final em [`criativos/meta-c01/`](../../criativos/meta-c01/). Originais do Drive preservados.

| # | Problema | Status | Como foi resolvido |
|---|---|---|---|
| 1 | `agronegocio` sem acento (peça 1, Feed e Story) | **Corrigido** | corpo da fonte calibrado pelo x-height medido na própria arte (Playfair 58px = 33px de x-height), glifo do acento isolado e composto. Gap de 4px, idêntico ao do ponto do "i" já existente |
| 2 | `Agronegocio` sem acento (peça 2, ambos) | **Corrigido** | idem, Poppins 28px = 16px de x-height |
| 3 | `Conheça o Advocacia`, artigo errado | **Corrigido** | glifo "a" clonado da própria arte. Mesmo desenho, cor e anti-aliasing |
| 4 | Peça 2 sem versão Story | **Resolvido** | Story 1080x1920 gerado: layout ancorado em y=450, topo estendido pela textura de fundo, base em fade para preto. Pill a 302px do rodapé |
| 5 | Story da peça 1 em 1080x1980 | **Corrigido** | reflow para 1080x1920 removendo 40px do vão handle/título e 100px do vão texto/botão (região de preto puro), 80px devolvidos no rodapé. Nada foi redesenhado |
| 6 | CTA no rodapé absoluto do Story | **Corrigido** | botão verde subiu 140px pelo mesmo reflow. Termina a 251px do rodapé, fora da faixa do CTA nativo |
| 7 | "garanta sua vaga" contradiz a oferta | **Aceito como está** | decisão do Flávio. Trocar o texto do botão exigiria redesenhar em serifada e a fonte da arte não é Playfair exata. Copy do anúncio e LP dizem "acesso imediato", só a arte fala em vaga. Incoerência leve, tolerável para 3 dias |

### Arquivos finais

| Arquivo | Dimensão | Uso |
|---|---|---|
| `CR01-6contratos-feed-4x5.png` | 1080x1350 | Feed, ambos os conjuntos |
| `CR01-6contratos-story-9x16.png` | 1080x1920 | Stories e Reels |
| `CR02-honorarios-feed-4x5.png` | 1080x1350 | Feed, ambos os conjuntos |
| `CR02-honorarios-story-9x16.png` | 1080x1920 | Stories e Reels |

### Pareamento de ângulo

| Peça | Ângulo | Leitura |
|---|---|---|
| 1. 6 contratos | Mecanismo, benefício numerável | Funciona nas duas temperaturas |
| 2. Disputam honorários | Dor por comparação social | Mais forte no frio, é o melhor hook do par |

**Estrutura:** as 2 peças rodam nos 2 conjuntos, com copy adaptada por temperatura. Total de 4 anúncios.

> Por que as 2 peças nos 2 conjuntos: em ABO a verba trava no nível do conjunto, mas **dentro** do conjunto o Meta distribui dinamicamente entre os anúncios e concentra entrega no que performa melhor. Não é split fixo. Logo, subir 2 peças por conjunto não divide a verba ao meio, dá ao algoritmo uma escolha. E ao final você sabe qual peça ganha no quente e qual ganha no frio, que é o aprendizado que sobrevive para a próxima rodada.

**Convenção:** `CR01` é sempre a **peça 1** e `CR02` é sempre a **peça 2**, nos dois conjuntos. O que muda entre conjuntos é a copy, não a peça. Isso mantém o relatório legível.

**Montagem no Meta:** em cada anúncio, ligar **Editar por posicionamento**. Versão Feed para Feed, versão Stories para Stories/Reels. Nunca deixar o Meta cortar a peça de Feed sozinho para o Stories, ele corta errado e come o texto.

**Princípio das copies abaixo:** a arte já carrega o gancho. A copy não repete o que está escrito na imagem, ela continua a frase e leva para a oferta.

---

### CONJUNTO A01 (quente): ela já conhece a Barbara, corta a apresentação

#### [C01-A01-CR01] [ESTÁTICO] [6 CONTRATOS] [V1] [14/08/26]
*Peça 1. A arte entrega o mecanismo, a copy entrega a oferta.*

> **Texto principal:**
> São 6 contratos. Aprendeu esses, você já consegue atender.
>
> Arrendamento, parceria, compra e venda, e o resto do pacote que sustenta praticamente toda negociação rural do país.
>
> Você acompanha meu conteúdo. A imersão completa está no ar:
>
> Acesso imediato, assiste no seu ritmo
> Minutas de contrato, notificação e distrato prontas para adaptar
> Checklist de due diligence de imóveis rurais
> Garantia de 7 dias
>
> R$97.
>
> **Título:** Os 6 contratos do agro | Acesso imediato
> **Descrição:** Garantia de 7 dias. Compra segura.
> **CTA:** Saiba mais

#### [C01-A01-CR02] [ESTÁTICO] [HONORÁRIOS] [V1] [14/08/26]
*Peça 2. A arte abre a comparação, a copy fecha com o caminho.*

> **Texto principal:**
> A diferença raramente é competência. É onde a advogada escolheu estar.
>
> O agro segue com demanda alta e pouca gente qualificada para redigir contrato rural entendendo a operação por trás dele. Enquanto isso, a advocacia generalista briga por honorário cada vez menor.
>
> Montei a imersão para quem quer fazer essa virada: quais contratos geram oportunidade, como o mercado funciona e por onde entrar.
>
> Acesso imediato, R$97, garantia de 7 dias. Com as minutas que eu uso.
>
> **Título:** Saia da disputa por honorário
> **Descrição:** Acesso imediato. Garantia de 7 dias.
> **CTA:** Saiba mais

---

### CONJUNTO A02 (frio): ela não faz ideia de quem é a Barbara

#### [C01-A02-CR01] [ESTÁTICO] [6 CONTRATOS] [V1] [14/08/26]
*Peça 1. Mesma arte, copy com contexto de mercado e apresentação.*

> **Texto principal:**
> Advogada: o agronegócio movimenta uma das maiores economias do país e boa parte dos contratos rurais ainda é redigida sem análise estratégica e sem entendimento da operação.
>
> Não é falta de demanda. É falta de gente preparada.
>
> São 6 contratos que sustentam quase toda negociação rural. Nesta imersão você aprende cada um deles, entende como o mercado funciona e sai com um caminho de entrada definido.
>
> Sou Bárbara Bindeli, filha de produtor rural e advogada. Cresci vendo essas negociações acontecerem antes de estudar Direito.
>
> Acesso imediato, R$97, garantia de 7 dias.
>
> **Título:** Os 6 contratos do agro | Comece do zero
> **Descrição:** Acesso imediato. Garantia de 7 dias.
> **CTA:** Saiba mais

#### [C01-A02-CR02] [ESTÁTICO] [HONORÁRIOS] [V1] [14/08/26]
*Peça 2. Melhor hook do par para público frio.*

> **Texto principal:**
> Você disputa os mesmos clientes, na mesma área, com as mesmas centenas de advogadas da sua cidade. E o honorário só cai.
>
> Do outro lado, o agro movimenta bilhões todos os anos e continua com escassez de advogada que entenda contrato rural na prática. Alta demanda, pouca concorrência qualificada. É uma das poucas áreas do Direito brasileiro onde isso ainda acontece.
>
> Nesta imersão você aprende os 6 contratos que sustentam esse mercado, entende a operação por trás deles e sai com as minutas prontas para adaptar.
>
> Sou Bárbara Bindeli, filha de produtor rural e advogada.
>
> Acesso imediato, R$97, garantia de 7 dias.
>
> **Título:** Onde a advogada do agro ganha mais
> **Descrição:** Acesso imediato. Garantia de 7 dias.
> **CTA:** Saiba mais

---

### Por que 2 anúncios em cada conjunto

Em ABO a verba trava no nível do conjunto, mas dentro do conjunto o Meta distribui entrega dinamicamente e concentra no anúncio que performa. Não é split fixo de 50/50. Subir as 2 peças em cada conjunto não parte a verba ao meio, dá ao algoritmo uma escolha, e no fim você sabe qual peça ganha no quente e qual ganha no frio. Esse é o aprendizado que sobrevive para a próxima rodada.

Ressalva: com verba baixa o Meta tende a eleger o vencedor cedo, com pouco dado. A leitura de segunda-feira serve como indício, não como veredito.

---

## 5. Métricas de controle

| Métrica | Meta conjunto quente | Meta conjunto frio |
|---------|---------------------|-------------------|
| CTR (link) | > 1,5% | > 1,0% |
| CPC (link) | < R$1,50 | < R$2,50 |
| Custo por LPV | < R$2,00 | < R$3,00 |
| CPM | R$20 a R$45 | R$25 a R$55 |
| CPA | < R$48,50 | leitura, não meta |

Sem hook rate nesta rodada: métrica de vídeo, e a campanha sobe só com estático.

---

## 6. UTMs (colar no campo Parâmetros de URL de cada anúncio)

```
utm_source=facebook&utm_medium=cpc&utm_campaign=imersao-agro-conv&utm_content={{ad.name}}&utm_term={{adset.name}}&utm_id={{campaign.id}}
```

---

## 7. Cronograma de operação

| Momento | Ação | O que NÃO fazer |
|---------|------|-----------------|
| Subida (D0) | Conferir aprovação e entrega nas primeiras 4h. Se CPM absurdo ou entrega zero, checar reprovação de anúncio e público. | Nada além disso |
| D1 manhã | Ler CTR, CPC e custo por LPV. Anotar. | **Não mexer em verba.** Não editar conjunto. |
| D2 | No quente, se uma das duas copies estiver com CTR abaixo da metade da outra, **pausar aquele anúncio**, nunca o conjunto. No frio não tem o que pausar, é anúncio único. | Não trocar otimização, não mexer em público |
| D3 (domingo) | Deixar rodar. | Não tocar em nada |
| Segunda | Análise completa, decisão de escala ou reestruturação | |

**Regra de ouro:** em campanha de 3 dias, cada edição estrutural zera o aprendizado. Sobe certo e deixa quieto.

---

## 8. Nomenclatura

Padrão adotado: o **praticado** na conta da Bárbara (campanha `[C02] [ADV-NA-PRATICA] [AÇÃO] [LEADS] [17/06/26] - Advogadas Agro`, Google Ads `6473647703`). Divergente do `nomenclatura-campanhas.md`, que está desatualizado.

```
Campanha: [C##] [PRODUTO] [ETAPA AIDA] [OBJETIVO] [DD/MM/AA] - Público
Conjunto: [C##-A##] [PRODUTO] [ETAPA AIDA] [OBJETIVO] [TEMPERATURA] [DETALHE] [DD/MM/AA]
Anúncio:  [C##-A##-CR##] [FORMATO] [ÂNGULO] [V#] [DD/MM/AA]
```

Série numérica: **por plataforma**. Esta abre a série do Meta como `C01` (a `C02` do Google segue a série própria do Google).

### Nomes finais desta campanha

```
[C01] [IMERSAO-AGRO] [AÇÃO] [CONVERSÃO] [14/08/26] - Advogadas Agro
├── [C01-A01] [IMERSAO-AGRO] [AÇÃO] [CONVERSÃO] [RMK] [ENGAJADAS 180D] [14/08/26]
│   ├── [C01-A01-CR01] [ESTÁTICO] [6 CONTRATOS] [V1] [14/08/26]
│   └── [C01-A01-CR02] [ESTÁTICO] [HONORÁRIOS] [V1] [14/08/26]
└── [C01-A02] [IMERSAO-AGRO] [AÇÃO] [CONVERSÃO] [COLD] [ADV 7UF 25-50] [14/08/26]
    ├── [C01-A02-CR01] [ESTÁTICO] [6 CONTRATOS] [V1] [14/08/26]
    └── [C01-A02-CR02] [ESTÁTICO] [HONORÁRIOS] [V1] [14/08/26]
```

`CR01` é sempre a peça "6 contratos" e `CR02` é sempre a peça "honorários", nos dois conjuntos. O que muda entre conjuntos é a copy, nunca a peça. Assim o relatório fica legível.

### Dívida de padronização (fora do escopo desta campanha)

- `nomenclatura-campanhas.md` está desatualizado nos dois repositórios (`agencia-rocket` e `rocketalive`). Não reflete o padrão praticado.
- Google Ads da Bárbara: asset group `[ CJ01] Direito Agrário` tem espaço solto dentro do colchete e não amarra na campanha (deveria ser `[C02-A01]`).
- Google Ads da Bárbara: asset group `Grupo de recursos 1` nunca foi renomeado.
- Google Ads da Bárbara: campanha `Leads-Display-Imersão Advocacia no Agro` (pausada) está fora de qualquer padrão.

---

## 9. Checklist de subida

- [ ] **Pixel da Kiwify confirmado como `2043169242972256`** (bloqueante)
- [ ] Domínio verificado e Purchase priorizado no AEM (bloqueante)
- [ ] Conta de anúncio com pagamento ativo e sem restrição (bloqueante)
- [ ] CAPI ativa na Kiwify (recomendado)
- [ ] Tags ViewContent e InitiateCheckout no GTM publicadas (recomendado)
- [ ] Público personalizado "Engajadas 180d IG + FB + Site" criado
- [ ] Público de exclusão (compradoras) criado
- [ ] Campanha criada em ABO com data de fim em 16/08
- [ ] Artes corrigidas: acentos, "Conheça a Advocacia", Story real da peça 2, CTA fora da zona inferior
- [ ] "Editar por posicionamento" ligado nos 4 anúncios
- [ ] UTMs preenchidas nos 4 anúncios
- [ ] Teste real de compra na Kiwify para validar o Purchase
