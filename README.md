# Engineering Student Journey - EDA

Este projeto realiza uma Análise Exploratória de Dados (EDA) com base no conjunto de dados **"Engineering Student Journey"** disponível no Kaggle. O objetivo é identificar padrões e fatores que influenciam o desempenho acadêmico e empregabilidade de estudantes de engenharia.

---

## Sobre o Dataset

- Fonte: [Kaggle - Engineering Student Journey](https://www.kaggle.com/datasets/rakeshkapilavai/engineering-student-journey)
- Registros: 300+
- Campos: Curso, GPA, Habilidades Técnicas, Participação em Clubes, Presença, Estágio, CTC, Empregabilidade e mais.
---

## Sumário


- Student ID:	Identificador único de cada aluno (UUID) String	Identificador
- Name:	Nome do estudante (anonimizado)	String	Identificador
- Age:	Idade do estudante	Integer	Numérica
- Gender:	Gênero do estudante (Male/Female)	Categórica	Demográfica
- Branch:	Curso acadêmico (CSE, ECE, MECH)	Categórica	Acadêmica
- Average GPA:	Média geral de GPA (0-10)	Float	Numérica
- Backlogs:	Número de reprovações	Integer	Acadêmica
- Attendance (%):	Porcentagem de presença nas aulas	Float	Acadêmica
- Clubs:	Clubes extracurriculares (Robotics, Coding)	String	Extracurricular
- Skills:	Habilidades técnicas (Python, ML)	String	Técnica
- Internship Done:	Fez estágio? (Yes/No)	Categórica	Profissional
- Internship Domain:	Área de estágio (Software, Research)	Categórica	Profissional
- Placement Status:	Foi contratado? (Placed/Not Placed)	Categórica	Resultado
- Placement Domain:	Área de contratação (Software, Core Eng.)	Categórica	Resultado
- CTC (LPA)	Salário: anual em LPA (0 se não foi contratado)	Float	Resultado
- Alumni Path:	Caminho após graduação (e.g., Job, Higher Studies)	Categórica	Pós-graduação
- Sem1 GPA - Sem8 GPA:	GPA por semestre (0-10)	Float	Acadêmica

---
## Perguntas a serem respondidas:

1. Quais cursos possuem maior média de GPA?
2. Alunos com mais presença na aula possuem maior GPA?
3. Estudantes com certas habilidades possuem maior salário(CTC)?
4. Qual a porcentagem de alunos que conseguem emprego após a formação?

---

## Metodologia (EDA)

As análises foram realizadas em Python com Pandas, Matplotlib e Seaborn, organizadas em etapas:

1. **Pré-processamento**
   - Remoção de valores faltantes ou "Não informado"
   - Explosão de campos com múltiplos valores (Skills, Clubs)

2. **Visualizações**
   - Boxplots para detecção de outliers
   - Gráficos de dispersão para correlação
   - Barras para ranking de CTC por habilidades, clubes e cursos
   - Gráficos categóricos para empregabilidade (por idade, gênero e estágio)

3. **Insights**
   - CTC tem baixa correlação com GPA isolado
   - Combinações de skills e clubes impactam significativamente o CTC
   - Estudantes de cursos como Engenharia Elétrica e IT se destacam em empregabilidade

---

## Perguntas Orientadoras e Conclusões

### 1. Quais cursos possuem maior média de GPA?
> Observa-se que, a paridade academica é extremamente alta e bem distribuída, indicando grande consistência de desempenho em todos os cursos com diferença de GPA de no máximo 0.15 pontos. De todo modo, temos que o curso de Engenharia Civil possui a maior média de GPA com aproximadamente 7.05 pontos, enquanto Ciências da Computação possui a menor média com 6.90 pontos. Além disso, há tendência fraca de correlação negativa em relação a taxa de reprovação dos cursos com o GPA mais baixo.

### 2. Alunos com mais presença possuem maior GPA?
> Analisando a porcentagem de presença de um aluno é possível concluir que há pouco relação entre esses dois fatores. Além disso, os gráficos de dispersão demonstram que de fato há pouca variação entre as notas dos alunos entre dois semestres distintos, isto é, um aluno que tirou uma boa nota no primeiro semestre tem altas chances de manter a mesma nota no semestre seguinte.

### 3. Estudantes com certas habilidades possuem maior CTC?
> Sim. Ao realizar o boxplot dos valores de CTC, podemos notar que 50% dos estudantes possuem um CTC entre 0 e 12,5 LPA, ou seja, estão classificados entre “ruim” e “bom” segundo a escala adotada. Não foram identificados outliers significativos nesse conjunto de dados.
Para confirmar a hipótese de que o GPA estaria diretamente relacionado ao CTC, optei por criar um gráfico de dispersão entre essas variáveis. Contudo, conforme observado, a correlação entre GPA e CTC é baixa, indicando pouca conexão direta.
Diante disso, comecei a analisar se outros fatores poderiam influenciar o CTC, como a participação em clubes acadêmicos e as Hard Skills desenvolvidas ao longo da graduação. Observou-se que, ao considerar apenas um clube ou uma única hard skill isoladamente, o CTC máximo encontrado é de aproximadamente 6 LPA, classificado como “ruim”.
Por isso, decidi avaliar combinações desses fatores para entender seu impacto no CTC. As combinações de clubes e hard skills associadas aos maiores valores médios de CTC foram, respectivamente:

Clubes: Literary Society, Cultural Club, Coding Club — CTC médio de 17,52 LPA

Hard Skills: Data Science, Python, Web Development, Machine Learning, Java — CTC médio de 19,99 LPA

Esses resultados sugerem que a combinação de múltiplas habilidades técnicas e envolvimento em diversos clubes pode estar mais relacionada a um maior retorno salarial, do que o desempenho acadêmico isolado.

### 4. Qual a porcentagem de alunos que conseguem emprego após a formação?
> Ao analisar possíveis relações que podem levar a não empregabilidade dos estudantes recém formados, houve uma distribuição bem simétrica dos valores, não houve distinção de idade, gênero ou realização do estágio. No entanto, quanto as pessoas que conseguiram emprego, foi possível observar uma tendência de maior taxa de sucesso em áreas de trabalho ligadas a software e engenharia fundamental. Além disso, alunos do curso de Engenharia Elétrica e IT tiveram maiores resultados ao obter emprego em comparação com os demais cursos
---
## Conclusão Geral

Apesar de pequenas variações entre os cursos, o desempenho acadêmico (GPA) é bem distribuído, com a Engenharia Civil apresentando a maior média e Ciências da Computação a menor. A presença nas aulas demonstrou ter pouca relação com o GPA, e o desempenho entre semestres é consistente.
Não foi identificada correlação significativa entre GPA e salário (CTC). Em vez disso, a combinação de múltiplas hard skills (como Python, Machine Learning e Java) e participação em diversos clubes extracurriculares demonstrou forte relação com maiores salários, indicando que essas experiências têm maior impacto no sucesso profissional do que o desempenho acadêmico isolado.
Quanto à empregabilidade, aproximadamente metade dos alunos conseguiu emprego após a graduação, sem correlação clara com idade, gênero ou estágio. No entanto, os que atuaram em áreas de software ou engenharia fundamental, especialmente vindos dos cursos de Engenharia Elétrica e IT, apresentaram maior taxa de inserção no mercado.
