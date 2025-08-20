# 🧪 Teste Técnico - Quality Assurance Full Stack
**🧠 Resumo**

O objetivo deste desafio é testar suas habilidades na garantia de qualidade. Ele é composto por vários blocos, alguns **obrigatórios** e outros *opcionais* que nos ajudarão a identificar o seu nível de expertise em cada área avaliada.

Os blocos são diferentes entre si e foram elaborados para testar habilidades distintas, contribuindo para elevar o nível das nossas entregas e soluções.

## 📑 Sumário

- [Bloco 1 | Análise de Requisitos](#bloco-1–analise-de-requisitos-(obrigatorio))
- [Bloco 2 | Execução de Testes](#bloco-2-execucao-de-testes-(opcional))
- [Bloco 3 | Report de Bugs](#bloco-3-report-de-bugs-(opcional))
- [Bloco 4 | Proatividade em Processos](#bloco-4-proatividade-em-processos-(obrigatorio))
- [Bloco Bônus | Mini desafio](#bloco-bonus-mini-desafio-(opcional))
- [Entrega](#entrega)
- [Critérios de Avaliação](#critérios-de-avaliação)
- [Dúvidas](#dúvidas)

## 📌 Objetivos

- Avaliar habilidades técnicas em testes manuais e/ou automatizados.
- Medir sua capacidade de análise de requisitos e criação de casos de teste.
- Validar habilidades de identificar melhorias em processos inexistentes ou pouco maduros.
- Testar a comunicação e documentação clara de bugs e resultados.

---

### 1️⃣ Bloco 1 – Análise de Requisitos (obrigatório)
Objetivo: medir sua capacidade de interpretar especificações e identificar cenários de teste.

História de Usuário — Compra de Produto com Análise

Como comprador de uma empresa. Quero pesquisar um produto, avaliar seu score de análise (preço, popularidade e rentabildiade), selecionar quantidade e adicionar a um carrinho.

Para gerar um pedido de compra que respeite políticas internas e disponibilidade do fornecedor.

**Contexto**:
O sistema possui catálogo com produtos ativos e inativos, preços por fornecedor e score de análise (0–100) calculado a partir do preço, popularidade do produto e rentabildiade do produto.

Cada produto pode ter múltiplos fornecedores, cada um com preço, prazo de entrega (dias), MOQs (mínimo de compra) e lead time (tempo que ele leva para entregar o produto).

**Critérios de Aceitação (CA)**
CA1 — Pesquisa e seleção

- Dado que estou autenticado, quando pesquisar por nome, código ou SKU, então devo ver uma lista de produtos ativos contendo: nome, SKU, preço mínimo praticado, melhor score de fornecedor e disponibilidade estimada.
- Produtos inativos não devem aparecer nos resultados.
- Ao abrir a página do produto, devo conseguir visualizar fornecedores disponíveis ordenados por score (desc) com: preço unitário, prazo de entrega, MOQ e score.

CA2 — Análise e escolha do fornecedor
Ao escolher um fornecedor, o sistema deve exibir o score detalhado (preço, entrega, qualidade) e um indicador:

- 80–100: “Recomendado”
- 60–79: “Aceitável”
- <60: “Risco”

O comprador pode prosseguir mesmo em “Risco”, mas o pedido deverá exigir justificativa.

Regras de Negócio (RN)

- RN1: Apenas produtos ativos podem ser comprados.
- RN2: Score é recalculado diariamente; o pedido deve guardar o valor do score usado na decisão.
- RN3: Desconto por volume não se acumula com outros cupons (se houver).
- RN4: Se fornecedor estiver compendências (documentação vencida), bloquear compra e informar motivo. (intencionalmente possível de existir)
- RN5: Impostos calculados por NCM do produto (simplificado no exemplo).

Liste casos de teste cobrindo:

- Positivos (fluxo feliz)
- Negativos (validações, bloqueios, reprovações)
- Usabilidade/Acessibilidade (mensagens, foco, atalhos)
- Mapear dados de teste (quantidades e cenários para acionar cada regra).
- Evidências: descreva passos, esperado/obtido e anexe prints ou registros.
- Riscos e sugestões: liste riscos percebidos (ex.: fraudes de desconto, arredondamento) e proponha melhorias.
- Dúvidas/Assunções: escreva perguntas que faria ao PO/Tech Lead e as suposições adotadas.

### 2️⃣ Bloco 2 – Execução de Testes (opcional)
Objetivo: avaliar atenção a detalhes e raciocínio crítico.
Exemplo de exercício:

Esta é uma plataforma simples para o cadastro de um usuário: https://userinyerface.com/. Realize um cadastro e documente sua trajetória, seja ela de sucesso e a de fracasso:

Tente executar testes e registrar:
- Passos para reprodução
- Resultado esperado
- Resultado obtido
- Evidências (prints, vídeos, logs)

### 3️⃣ Bloco 3 – Report de Bugs (opcional)
Objetivo: avaliar clareza e objetividade na comunicação.
Exemplo de exercício:

Em um determinado processo de testes manuais, você encontra-se com o seguinte bug:
“Ao tentar adicionar um produto específico a um carrinho, o mesmo, dentro do carrinho encontra-se com o preço, o "score" e a quantidade diferentes do que ele deveria ser.”

Quais processos, documentos ou alertas você faria? para quem o faria?

### 4️⃣ Bloco 4 – Proatividade em Processos (obrigatório)
Objetivo: entender como você cria e melhora fluxos de QA.

“A empresa não possui processo formal de QA. Hoje, as entregas vão direto do dev para produção.”

Como você estruturaria o fluxo de QA na empresa?:

- Tipos de teste que implementaria
- Ferramentas que sugeriria
- Métricas que acompanharia
- Como lidaria com versionamento e automação no futuro

### ✨ Bloco bônus - Mini desafio (opcional)
objetivo: testar suas habilidades em alguma linguagem/ferramenta

Implemente uma folha de testes, usando alguma linguagem de programação ou ferramenta. A ideia é testar os 4 processos gerais de um pedido de compras:

- Busca
- Cadastro
- Atualização
- Deleção

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