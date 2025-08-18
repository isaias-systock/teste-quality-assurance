## 🧪 Teste Técnico - Quality Assurance Full Stack

### 🧠 Resumo

O objetivo deste desafio é testar suas habilidades na garantia de qualidade. Ele é composto por vários blocos, alguns **obrigatórios** e outros *opcionais* que nos ajudarão a identificar o seu nível de expertise em cada área avaliada.

Os blocos são diferentes entre si e foram elaborados para testar habilidades distintas, contribuindo para elevar o nível das nossas entregas e soluções.

### 📑 Sumário

- [Bloco 1](#bloco-1)
- [Bloco 2](#bloco-2)
- [Bloco 3](#bloco-3)
- [Bloco 4](#bloco-4)
- [Bloco Bônus](#bloco-bonus)
- [Entrega](#entrega)
- [Critérios de Avaliação](#critérios-de-avaliação)
- [Dúvidas](#dúvidas)
---

### 📌 Objetivos

- Avaliar habilidades técnicas em testes manuais e/ou automatizados.
- Medir sua capacidade de análise de requisitos e criação de casos de teste.
- Validar habilidades de identificar melhorias em processos inexistentes ou pouco maduros.
- Testar a comunicação e documentação clara de bugs e resultados.

---

#### Bloco 1 – Análise de Requisitos (obrigatório)
Objetivo: medir a capacidade de interpretar especificações e identificar cenários de teste.

História de Usuário — Compra de Produto com Análise

Como comprador de uma empresa
Quero pesquisar um produto, avaliar seu score de análise (preço, popularidade e rentabildiade), selecionar quantidade e adicionar a um carrinho
Para gerar um pedido de compra que respeite políticas internas e disponibilidade do fornecedor

**Contexto**:
    - O sistema possui catálogo com produtos ativos e inativos, preços por fornecedor e score de análise (0–100) calculado a partir do preço, popularidade do produto e rentabildiade do produto.
    - Cada produto pode ter múltiplos fornecedores, cada um com preço, prazo de entrega (dias), MOQs (mínimo de compra) e lead time (tempo que ele leva para entregar o produto).

Critérios de Aceitação (CA)
CA1 — Pesquisa e seleção

    Dado que estou autenticado, quando pesquisar por nome, código ou SKU, então devo ver uma lista de produtos ativos contendo: nome, SKU, preço mínimo praticado, melhor score de fornecedor e disponibilidade estimada.

    Produtos inativos não devem aparecer nos resultados.

    Ao abrir a página do produto, devo conseguir visualizar fornecedores disponíveis ordenados por score (desc) com: preço unitário, prazo de entrega, MOQ e score.

CA2 — Análise e escolha do fornecedor

    Ao escolher um fornecedor, o sistema deve exibir o score detalhado (preço, entrega, qualidade) e um indicador:

        80–100: “Recomendado”

        60–79: “Aceitável”

        <60: “Risco”

    O comprador pode prosseguir mesmo em “Risco”, mas o pedido deverá exigir justificativa.

CA3 — Quantidade, MOQ e limites

    A quantidade deve ser inteira positiva.

    Se a quantidade informada < MOQ do fornecedor, o sistema deve sugerir ajustar para o MOQ.

    Máximo por pedido: 10.000 unidades. Acima disso, bloquear e orientar a dividir pedidos.

CA4 — Preço, impostos e frete

    O valor total = (preço unitário × quantidade) + frete + impostos – descontos.

    Arredondamento financeiro: 2 casas decimais, round half up.

    Se houver desconto por volume, aplicar conforme tabela do fornecedor (vide Dados de Exemplo).

    Frete é obrigatório quando valor total < R$ 5.000,00; caso contrário, frete = R$ 0,00.

CA5 — Regras de aprovação por alçada

    Até R$ 10.000,00: aprovação automática.

    R$ 10.000,01 a R$ 50.000,00: aprovação do Coordenador.

    Acima de R$ 50.000,00: aprovação do Gerente.

    Pedidos com fornecedor em “Risco” sempre exigem pelo menos aprovação do Coordenador, independente do valor.

CA6 — Geração do pedido

    Ao confirmar, o sistema gera um número de pedido único e estado inicial:

        “Aguardando Aprovação” (se necessário) ou “Aprovado”.

    Um e-mail é enviado para o aprovador (quando aplicável) com resumo do pedido.

    O comprador pode baixar o PDF do pedido após a criação.

CA7 — Auditoria e trilha

    Registrar quem criou, quando, fornecedor escolhido, preço, impostos, descontos e score no momento da compra.

    Alterações de status devem ficar registradas (aprovado/reprovado, data, aprovador).

CA8 — Desempenho (intencionalmente aberto para análise do candidato)

    Pesquisas por produto devem responder em ≤ 2s para catálogos de até 100 mil itens.

    Tempo de criação do pedido ≤ 3s em condições normais.
    (O candidato deve levantar dúvidas sobre ambiente, carga, picos, etc.)

CA9 — Acessibilidade & UX (aberto)

    Campos com erro devem ter mensagens claras e foco automático no campo inválido.
    (O candidato pode propor padrões e critérios adicionais.)

Regras de Negócio (RN)

    RN1: Apenas produtos ativos podem ser comprados.

    RN2: Score é recalculado diariamente; o pedido deve guardar o valor do score usado na decisão.

    RN3: Desconto por volume não se acumula com outros cupons (se houver).

    RN4: Se fornecedor estiver compendências (documentação vencida), bloquear compra e informar motivo. (intencionalmente possível de existir)

    RN5: Impostos calculados por NCM do produto (simplificado no exemplo).

Dados de Exemplo (para o teste)

Produto: “Cartucho Impressora X” — SKU: CX-123, NCM: 8443.99.99, status: ativo

Fornecedores:
Fornecedor	Score	Preço Unit.	Prazo (dias)	MOQ	Desconto por volume
AlfaSupplies	88	R$ 95,00	5	10	2% ≥ 200 un; 5% ≥ 500 un
BetaTrade	72	R$ 89,90	12	50	1,5% ≥ 100 un; 3% ≥ 300 un
GamaOffice	58	R$ 85,00	20	5	0%

Frete: R$ 150,00 se total < R$ 5.000,00; caso contrário, R$ 0,00
Imposto (simples): 12% sobre subtotal (preço × qtd) antes do frete/desconto
Limites: Máx. 10.000 un/pedido
Ambiguidades propositalmente deixadas para o candidato levantar

    Como lidar com produto inativo que estava no carrinho e foi desativado antes de fechar?

    Concorrência: dois compradores comprando o mesmo produto com estoque limitado (se aplicável ao contexto).

    Recalcular preço/score se o pedido ficar muito tempo “Aguardando Aprovação”?

    Política de frete por região/fornecedor (simplificada aqui).

    Cancelamento e reprovação: o que acontece com o número do pedido e trilha?

O que pedir no exercício (instruções ao candidato)

    Listar casos de teste cobrindo:

        Positivos (fluxo feliz)

        Negativos (validações, bloqueios, reprovações)

        Borda (MOQ-1, MOQ, MOQ+1; limites de desconto; valor exatamente em 10.000 e 50.000; quantidade 0; 10.001 etc.)

        Performance (consultas, criação)

        Usabilidade/Acessibilidade (mensagens, foco, atalhos)

    Mapear dados de teste (quantidades e cenários para acionar cada regra).

    Evidências: descreva passos, esperado/obtido e anexe prints ou registros.

    Riscos e sugestões: liste riscos percebidos (ex.: fraudes de desconto, arredondamento) e proponha melhorias.

    Dúvidas/Assunções: escreva perguntas que faria ao PO/Tech Lead e as suposições adotadas.

Exemplos de cenários que não podem faltar (checklist rápido)

Compra com fornecedor “Recomendado” (score ≥ 80) e valor ≤ 10.000 (aprovação automática).

Compra com valor = 10.000,00 (limite) e 10.000,01 (exige aprovação).

Fornecedor “Risco” (score < 60) exigindo justificativa + aprovação.

Aplicação correta de MOQ (ajuste sugerido) e desconto por volume.

Frete aplicado quando total < R$ 5.000 e isento quando ≥ R$ 5.000.

Arredondamento financeiro (2 casas, half up) em totais e impostos.

Bloqueio ao exceder 10.000 unidades.

Geração de nº de pedido, status correto e e-mail ao aprovador.

Registro de trilha de auditoria.








Bloco 2 – Execução de Testes (obrigatorio)

Objetivo: avaliar atenção a detalhes e raciocínio crítico.
Exemplo de exercício:

Disponibilizar um ambiente de teste simples ou protótipo (pode ser um link de staging ou uma aplicação fictícia).

Pedir que o candidato execute os testes e registre:
- Passos para reprodução
- Resultado esperado
- Resultado obtido
- Evidências (prints, vídeos, logs)

Bloco 3 – Report de Bugs (opcional)

Objetivo: avaliar clareza e objetividade na comunicação.
Exemplo de exercício:

Fornecer um bug intencional em um ambiente controlado e pedir que o candidato abra um ticket no padrão que a empresa deseja adotar (ex.: título claro, descrição, passos, evidências, severidade, prioridade).

Bloco 4 – Proatividade em Processos

Objetivo: entender como o candidato cria e melhora fluxos de QA.
Exemplo de exercício:

Apresentar um cenário fictício:

“A empresa não possui processo formal de QA. Hoje, as entregas vão direto do dev para produção.”

Pedir que o candidato descreva como estruturaria o fluxo de QA na empresa:

Tipos de teste que implementaria

Ferramentas que sugeriria

Métricas que acompanharia

Como lidaria com versionamento e automação no futuro

Bloco bônus

Incluir um mini-desafio técnico de automação de testes se a vaga exigir (ex.: Cypress, Selenium, Playwright).

Colocar limite de tempo para cada bloco para avaliar priorização.

Avaliar soft skills (organização, comunicação, clareza, visão de processo).

modelo completo de teste técnico com arquivos e instruções para enviar para os candidatos, incluindo história de usuário, protótipo e formatação para respostas

## 📦 Entrega

- **Prazo:** até 7 dias corridos após o recebimento.
- **Forma de entrega:** envie o link de um repositório público no GitHub ou em qualquer plataforma que possibilite a estrutura abaixo.
- Esta é a estrutura de arquivos esperada para a entrega:

```bash
/seu-repositorio
├── bloco-1/
│ ├── artefato-a.pdf
│ ├── artefato-b.docxs
│ ├── ...
│
├── bloco-2/
│ ├── artefato-a.txt
│ ├── artefato-b.pprt
│
├── bloco-3/
│ ├── artefato-a.pdf
│ ├── artefato-b.docxs
│ ├── ...
│
├── bloco-4/
│ ├── artefato-a.pdf
│ ├── artefato-b.docxs
│
├── bloco-bonus/
│ ├── ...
│
```

---

### ✅ Critérios de Avaliação

- Clareza, organização e estrutura dos artefatos
- Cumprimento dos requisitos obrigatórios
- Criatividade e uso de diferenciais opcionais

---


### ❓Dúvidas

Caso tenha dúvidas sobre o teste, sinta-se a vontade para questionar no contato na qual enviou-lhe este teste. 

Boa sorte! 🍀