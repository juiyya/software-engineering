# Software Engineering – Design Patterns

Projeto Risk Solutions: plataforma de vistorias e laudos para uma rede de franquias de fábricas de plataformas petrolíferas.

## Checkpoint: instruções

1. Identificar o maior condicional por tipo do projeto.
2. Desenhar o diagrama de sequência de um cenário que passa por esse condicional, somente com objetos e mensagens.
3. Responder em uma frase: que variação um padrão absorveria nesse ponto?
4. Escolher um padrão (Strategy, Factory Method, Observer, Adapter, Decorator) ou "nenhum ainda".
5. Registrar a decisão no ADR, inclusive se a decisão for não aplicar um padrão.

Padrões considerados:

- Comportamentais: Strategy, Observer
- Criacional: Factory Method
- Estruturais: Adapter, Decorator

## Checkpoint: resultado do grupo

1. **Maior condicional:** a validação das respostas do checklist contra as normas da apólice. Cada norma é de um tipo (sim/não, valor com limite ou data) e a resposta é avaliada de forma diferente conforme o tipo. Sem padrão, vira um `switch` sobre o tipo da norma dentro da `CalculadoraRisco`.
2. **Diagrama de sequência:** [images/diagrama_sequencia_validacao_normas.png](images/diagrama_sequencia_validacao_normas.png). As mensagens 4 a 6 são os ramos do condicional.
3. **Variação absorvida:** a regra de validação que muda conforme o tipo da norma (sim/não, valor com limite, data).
4. **Padrão escolhido:** Strategy.
5. **ADR:** [docs/adr/0001-strategy-validacao-normas.md](docs/adr/0001-strategy-validacao-normas.md). Ele também explica por que revisamos a decisão anterior ("nenhum ainda") e por que Factory Method, Observer, Adapter e Decorator ficaram de fora.

## Arquivos

| Arquivo | Conteúdo |
|---|---|
| `Risk_Solutions.docx` | Documento de visão do negócio |
| `CP 2 SOFTWARE ENGINEERING.docx` | Entrega do checkpoint de design patterns |
| `docs/adr/` | Registros de decisão de arquitetura |
| `images/diagram.png` | Diagrama de casos de uso |
| `images/diagrama_sequencia.png` | Sequência geral: preenchimento, assinaturas e auditoria |
| `images/geracao checklist dinamico.png` | Sequência da geração do checklist dinâmico (Astah: `geracao checklist dinamico.asta`) |
| `images/diagrama_sequencia_validacao_normas.png` | Sequência do cenário que passa pelo condicional (este checkpoint) |
| `DesignPatterns.ipynb` | Estudo dos cinco padrões, com o exemplo de política de desconto por porte de empresa |

O diagrama geral usa `Frontend`, `Main Process`, `Worker` e `PostgreSQL`; os outros detalham objetos internos do backend (`ServicoVistoria`, `CalculadoraRisco`, repositórios). São níveis de detalhe diferentes do mesmo sistema.
