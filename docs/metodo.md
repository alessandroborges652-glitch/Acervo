# Método de Fichamento do Acervo

Documento de protocolo. Define como cada obra anexada ao acervo deve ser fichada,
para que todos os fichamentos sejam consistentes entre si e possam ser cruzados.

**Leia este documento antes de fichar qualquer obra nova.**

---

## 1. Princípio central: rastreabilidade

Toda afirmação em um fichamento precisa ter origem identificável. Três marcadores
obrigatórios:

- `[OBRA]` — está no material lido. Sempre acompanhado da localização (capítulo,
  seção ou página).
- `[COMENTÁRIO]` — interpretação, contextualização ou crítica acrescentada por
  Claude. Não é o que o autor disse.
- `[NÃO ENCONTRADO]` — o tema foi procurado no material e não estava lá. Registrar
  isso vale tanto quanto registrar o que foi achado, porque evita atribuir ao autor
  uma posição que ele não tomou.

Nunca preencher lacuna do material com conhecimento geral apresentado como se
fosse da obra. Se a obra não trata do assunto, o fichamento diz isso.

## 2. Estrutura padrão de um fichamento

Cada obra gera **um arquivo próprio** em `claude/fichamentos/<slug>.md`.

### Cabeçalho

```
Obra: [autor(es). Título. Edição. Editora, ano.]
Tipo: [livro-texto | artigo original | revisão sistemática | meta-análise | posicionamento oficial]
Identificador: [ISBN, DOI ou PMID quando houver]
Temas do acervo cobertos: [ver lista de temas no índice]
Extensão lida: [integral | parcial — especificar quais capítulos/seções]
Qualidade do arquivo: [texto nativo | OCR | escaneado sem OCR]
Data do fichamento:
```

O campo **Extensão lida** é obrigatório e não pode ser omitido. Um fichamento
parcial que se apresenta como completo é pior do que nenhum fichamento.

### Nível 1 — Conteúdo fiel à obra

Acompanha a estrutura do original, preservando o raciocínio e a terminologia do
autor. Deve conter:

- **Argumento central** — a tese que a obra sustenta, em poucas linhas.
- **Percurso capítulo a capítulo** (livros) ou **método e resultados** (artigos):
  o que cada parte estabelece.
- **Conceitos-chave com a definição do próprio autor**, não com a definição
  genérica da área. Quando autores diferentes usam o mesmo termo de forma
  diferente, isso importa.
- **Dados, números, faixas e protocolos** apresentados, com a localização exata.
  São o que será citado depois em prescrição.
- **Base de evidência** — em que tipo de estudo o autor se apoia, e onde ele
  próprio sinaliza incerteza.

### Nível 2 — Tradução para a prescrição

O mesmo conteúdo, reorganizado pela pergunta "o que isso muda no treino que eu
monto na segunda-feira":

- **O que muda na montagem do treino** — decisões concretas afetadas.
- **Números aplicáveis** — faixas de séries, repetições, RIR, descanso, frequência,
  progressão, sempre indicando a população estudada (treinados x destreinados,
  idade, sexo), porque a transferência depende disso.
- **Como justificar a escolha ao aluno** — a explicação em linguagem acessível,
  sem perder a precisão.
- **Erros de prescrição que essa obra ajuda a identificar** — práticas comuns que
  o material contradiz.
- **Limites de aplicação** — onde o autor extrapola, opina ou generaliza além do
  que os dados sustentam. Toda obra tem esse ponto; registrá-lo é o que permite
  leitura crítica em vez de adesão.

### Rodapé — Conexões

- **Concorda com:** [outras obras do acervo, com o ponto de convergência]
- **Diverge de:** [outras obras do acervo, com o ponto exato da divergência]
- **Complementa:** [obras que cobrem o que esta deixa de fora]

Este rodapé é o que transforma arquivos isolados em acervo. Sempre que um
fichamento novo divergir de um já existente, a divergência também é registrada no
índice.

### Seção final — Simplificando o estudo

Sempre a última seção. É o mesmo conteúdo dos Níveis 1 e 2 reescrito em **linguagem
direta, para leitura rápida** — sem carimbos, sem tabelas, sem citação de página.
Serve para reler antes de um atendimento e para explicar a obra a quem não vai ler o
fichamento inteiro.

Subtópicos fixos:

- **A ideia em uma frase** — o que a obra sustenta, em uma frase.
- **O que o estudo mostrou** — os achados centrais, um parágrafo curto cada,
  começando pela conclusão em negrito.
- **O que muda no treino** — as decisões concretas, separadas por tipo de aluno
  quando fizer sentido.
- **Coisas que o estudo derruba** — lista numerada de crenças comuns que o material
  contradiz.
- **O que este estudo não responde** — os limites em linguagem simples.

Duas regras que sustentam a seção:

1. **Nada de novo aparece aqui.** Se um argumento não está nos Níveis 1 e 2, ele não
   entra — simplificar é reescrever, não acrescentar.
2. **Abrir com a ressalva** de que os dados, as citações e a localização por página
   estão nas seções acima. Sem isso, a seção simplificada pode ser confundida com a
   parte rastreável do fichamento.

O que já existe em outra seção — o parágrafo de explicação ao aluno, por exemplo — não
se repete aqui.

## 3. Regras de citação

- Citar sempre com localização verificável: `(cap. 4, p. 112)`, `(seção 3.2)`,
  `(Tabela 2)`. Nunca citar sem indicar onde.
- Se o PDF não tiver numeração de página confiável, usar capítulo e seção e
  registrar isso no cabeçalho.
- Transcrição literal entre aspas e curta. O fichamento é síntese, não cópia.
- Ao responder perguntas usando o acervo, citar o fichamento **e** a localização
  na obra original, para que a fonte primária possa ser conferida.

## 4. Fluxo de trabalho por obra anexada

1. Verificar se o arquivo é legível (texto nativo, OCR ou escaneado sem camada de
   texto — este último precisa de OCR antes).
2. Ler o material, integral ou nas seções relevantes.
3. Produzir o fichamento no formato acima, em `claude/fichamentos/<slug>.md`.
4. Atualizar o **índice do acervo**: acrescentar a obra, mapear os temas que ela
   cobre, registrar divergências novas e remover os temas que deixaram de ser lacuna.
5. Relatar ao final: o que foi lido, o que ficou de fora e por quê.

## 5. Restrição de escopo

Este acervo apoia decisões de treinamento físico. Duas fronteiras a respeitar nos
fichamentos e nas respostas construídas a partir deles:

- Conteúdo de nutrição serve para orientação geral de hábitos e para o diálogo com
  nutricionista — não para prescrição de dieta.
- Conteúdo sobre lesões e populações clínicas serve para adaptar treino e
  reconhecer quando encaminhar — não para diagnóstico ou tratamento.

Quando uma pergunta atravessar essas fronteiras, a resposta deve dizer isso
explicitamente em vez de responder como se não houvesse limite profissional.
