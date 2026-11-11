# Revisão de Coesão, Coerência e Padronização do TCC

Este documento reúne os pontos de melhoria identificados na leitura cruzada de todos os capítulos e arquivos de configuração do projeto LaTeX (`macros.tex`, `main.tex` e capítulos 1 a 7), organizados por ordem de prioridade.

---

## 1. Prioridade Alta — Coerência Temporal e Estrutural (Resquícios do TCC 1 e Capa)

### 1.1. Parágrafo de estrutura do documento desatualizado (Introdução)
- **Onde:** `textuais/introducao.tex` (linha 13)
- **Problema:** O último parágrafo da abertura da Introdução ainda descreve o documento como um **projeto de TCC 1**, apresentando quatro divergências diretas com o texto atual:
  1. Chama o trabalho de *"planejamento deste projeto de TCC 1"*;
  2. Descreve a ordem das seções da Introdução como *Problema → Objetivos → Justificativa*, mas a ordem real no arquivo é `1.1 Justificativa` → `1.2 Problema de Pesquisa` → `1.3 Objetivos`;
  3. Afirma que a fundamentação teórica discute **três** trabalhos correlatos, quando a Seção 2.6 (`textuais/ref_teorico.tex`, linha 56) analisa **seis** trabalhos correlatos;
  4. Menciona um *"Cronograma de atividades previsto"* ao final do texto (inexistente no TCC final) e omite os Capítulos 4 (*Projeto do Sistema*), 5 (*O Sistema Test-Manager*), 6 (*Validação do Sistema*) e 7 (*Conclusão*).
- **Sugestão:** Reescrever esse parágrafo apresentando brevemente a organização real dos 7 capítulos do TCC final.

### 1.2. Tempo verbal no futuro e informalidade na Introdução
- **Onde:** `textuais/introducao.tex` (linha 9)
- **Problema:**
  - Uso do futuro (*"O sistema **será desenvolvido** utilizando a linguagem PHP..."*), destoando dos Capítulos 4 a 7, nos quais o sistema já foi construído e validado.
  - Menção informal ao orientador apenas pelo primeiro nome (*"...atende a uma solicitação direta do Professor Pedro..."*), quebrando o registro impessoal acadêmico.
- **Sugestão:** Ajustar o verbo para o passado (*"foi desenvolvido"*) e substituir *"solicitação direta do Professor Pedro"* por *"diretriz técnica da coordenação dos projetos de software do campus"* (ou *"orientação acadêmica do projeto"*).

### 1.3. Erros no texto da Capa e da Folha de Rosto (`macros.tex`)
- **Onde:** `macros.tex` (linhas 4, 5 e 11–16)
- **Problema:**
  1. **Linha 5:** `\curso{Curso de Analise e Desenvolvimento de Sistemas}` está sem acento em **Análise** (na capa e folha de rosto sai impresso `ANALISE`), além de divergir do nome completo usado na Conclusão (*Curso de Tecnologia em Análise e Desenvolvimento de Sistemas*).
  2. **Linha 12 (`\preambulo`):** Há duplicação de palavras: *"Coordenadoria do **Curso de Curso de** Tecnologia em Análise e Desenvolvimento de Sistemas..."*.
  3. **Linha 16 (`\preambulo`):** O grau acadêmico está escrito como *"obtenção do título de **Desenvolvedor e Analista de Sistema**"*, quando a titulação oficial conferida pelos cursos superiores de tecnologia (CST) em ADS é **Tecnólogo em Análise e Desenvolvimento de Sistemas**.
  4. **Linha 4:** `\instituicao{Instituto federal do espírito santo}` está com iniciais minúsculas (na capa o `\MakeUppercase` mascara, mas na ficha catalográfica/metadados aparece minúsculo).

---

## 2. Prioridade Média — Coesão Técnica e Consistência entre Capítulos

### 2.1. Contradição sobre a obrigatoriedade do *print* de tela nos defeitos
- **Onde:** `textuais/projeto.tex` (linha 67) vs. `textuais/sistema.tex` (linhas 34 e 122) e `textuais/resultados.tex` (linha 11)
- **Problema:**
  - No Capítulo 4 (`projeto.tex`, linha 67), afirma-se que o registro de defeito contém *"a captura de tela (print) **opcional**"*.
  - Já no Capítulo 6 (`resultados.tex`, linha 11), afirma-se *"exigência de cadastro de defeito com upload de captura de tela (print) no fluxo de reprovação"*, dando a entender que o anexo da imagem também é obrigatório.
- **Sugestão:** Uniformizar nos Capítulos 4, 5 e 6: deixar claro que **o registro do defeito** é obrigatório ao reprovar uma versão de teste, especificando de forma idêntica em todos os capítulos se o **anexo da imagem (`print`)** é obrigatório ou opcional.

### 2.2. Divergência nos nomes/quantidade de status de defeitos
- **Onde:** `textuais/projeto.tex` (linha 33, RF11) vs. `textuais/projeto.tex` (linha 69) e `textuais/sistema.tex` (linhas 58 e 122)
- **Problema:** O requisito `RF11` lista três estados para o defeito (*Aberto*, *Em Correção* e *Resolvido*), mas a descrição dos casos de uso e das telas nos Capítulos 4 e 5 menciona apenas os estados *Aberto* e *Resolvido*.
- **Sugestão:** Se o sistema possui o status intermediário *Em Correção* (ou *Em Andamento*), mencioná-lo também na descrição do fluxo em `sistema.tex`; caso contrário, alinhar o texto de `RF11` aos estados efetivamente implementados.

### 2.3. Ausência do Docker na fundamentação das tecnologias (Capítulo 2)
- **Onde:** `textuais/ref_teorico.tex` (Seção 2.5, linhas 33–53)
- **Problema:** A conteinerização com **Docker** aparece com destaque na Metodologia (Seção 3.2), na Arquitetura (Seção 4.1), na Implementação (Seção 5.1), na Verificação Técnica (Seção 6.1.1) e na Conclusão (Seções 7.1 e 7.5), mas não é apresentada na Seção `2.5 Tecnologias Utilizadas no Projeto` (que cobre PHP/Laravel, MVC, MySQL, HTML/CSS/Bootstrap e Git/GitHub).
- **Sugestão:** Incluir uma subseção curta `2.5.6 Conteinerização com Docker` no Referencial Teórico para sustentar teoricamente todas as menções posteriores.

### 2.4. Alinhamento dos construtos e citação do Modelo TAM (Capítulo 3 vs. Capítulo 6)
- **Onde:** `textuais/metodologia.tex` (Seção 3.3, linhas 31–35) vs. `textuais/resultados.tex` (linhas 7 e 15)
- **Problema:**
  1. Na Seção 3.3 (`metodologia.tex`), o Modelo TAM é apresentado sem citar a obra seminal `\cite{davis1989}` (que só aparece citada no Capítulo 6).
  2. Na Seção 3.3 listam-se apenas **duas** dimensões do TAM (*Utilidade Percebida* e *Facilidade de Uso Percebida*), enquanto na Seção 6.1.2 (`resultados.tex`, linha 15) o instrumento avalia **três** construtos gerais, adicionando *Intenção Comportamental de Uso* (Q7 e Q8).
- **Sugestão:** Adicionar `\cite{davis1989, venkatesh2000}` já na Seção 3.3 e incluir o terceiro item (*Intenção Comportamental de Uso*) na lista da Metodologia para espelhar exatamente a análise do Capítulo 6.

### 2.5. Referência cruzada chamando "Quadro" de "Tabela"
- **Onde:** `textuais/ref_teorico.tex` (linha 62)
- **Problema:** O texto diz *"A **Tabela** `\ref{tab:trabalhos_correlatos}` sintetiza..."*, gerando *"A Tabela 1 sintetiza..."* no PDF, mas o elemento flutuante logo abaixo é o **Quadro 1** (`\begin{quadro}`). Mais adiante, no Capítulo 6, existe a verdadeira **Tabela 1** (`tab:resultados_likert`).
- **Sugestão:** Trocar *"A Tabela `\ref{tab:trabalhos_correlatos}`"* por *"O Quadro `\ref{tab:trabalhos_correlatos}`"*.

---

## 3. Fluidez Textual — Redundâncias que Podem Ser Enxugadas

### 3.1. Repetição de argumentos e citações dentro da Introdução
- **Onde:** `textuais/introducao.tex` (linhas 5, 7, 17, 21 e 23)
- **Problema:** A crítica ao uso de planilhas/Google Docs, a perda de histórico de execução e o trio de citações `\cite{tebes2022, kokubum2025, medeiros2022}` repetem-se quase com a mesma estrutura frasal em três lugares seguidos: na abertura do capítulo, na `1.1 Justificativa` e no `1.2 Problema de Pesquisa`.
- **Sugestão:** Manter a contextualização geral mais enxuta na abertura, focar `1.2 Problema de Pesquisa` na lacuna operacional e na pergunta norteadora, e concentrar `1.1 Justificativa` nos impactos acadêmicos, pedagógicos e institucionais da solução para o campus.

### 3.2. Sobreposição entre as Seções 4.1 e 5.1 (Arquitetura)
- **Onde:** `textuais/projeto.tex` (linhas 5–9) e `textuais/sistema.tex` (linha 7)
- **Problema:** Os dois trechos explicam quase com as mesmas palavras o papel de *Model* (Eloquent ORM / MySQL), *View* (Blade / Bootstrap 5), *Controller* e o isolamento em contêineres Docker.
- **Sugestão:** Em `5.1`, substituir a reexplicação conceitual das camadas por uma retomada breve (*"Materializando a arquitetura MVC definida na Seção 4.1..."*) e ir direto aos detalhes de implementação (middlewares, sessão, BCrypt, CSRF e organização das rotas).

### 3.3. Títulos duplicados no Capítulo 7 ("Considerações Finais")
- **Onde:** `textuais/conclusao.tex` (linha 5 vs. linha 46)
- **Problema:** O capítulo possui `7.1 Considerações Finais` e `7.5 Considerações Finais do Autor`, gerando redundância no Sumário.
- **Sugestão:** Renomear `7.1` para `Síntese do Trabalho` (ou `Visão Geral dos Resultados`), ou integrar o fechamento de `7.5` ao final do capítulo sem precisar de duas seções com o mesmo nome.

### 3.4. Preservação de impessoalidade na discussão de $n = 1$ (Capítulo 6)
- **Onde:** `textuais/resultados.tex` (linhas 62, 66 e 119)
- **Problema:** A Seção 6.2 destaca que a coleta foi anônima, mas como houve apenas 1 participante no perfil Coordenador ($n = 1$), a linha 119 expõe individualmente todas as notas menores atribuídas por esse único respondente (*"nota 2 em Q8 e nota 3 em Q2, Q3 e Q4"*).
- **Sugestão:** Suavizar a redação na linha 119 sem listar cada nota individual do respondente único — por exemplo: *"explica-se pela avaliação mais cautelosa registrada na subamostra de coordenação, associada na questão aberta (Q18/Q19) à expectativa por um módulo prévio de Engenharia de Requisitos..."*.

---

## 4. Padronização Gráfica, Terminológica e Acabamento ABNT (`main.tex`)

1. **Padronização de estrangeirismos em itálico:**
   - Termos como *framework*, *tester*, *dashboard*, *deploy* e *upload* alternam entre itálico (`\textit{framework}`, `\textit{Testers}` nos Capítulos 1–2) e texto normal (`framework`, `Tester`, `upload` nos Capítulos 4–7). Convém adotar um critério único (pela norma ABNT, estrangeirismos não dicionarizados em português ficam em itálico; nomes próprios de papéis do sistema podem ficar com inicial maiúscula em redondo, desde que padronizados desde o Capítulo 1).
2. **Padronização de aspas em `projeto.tex` (linha 31):**
   - No requisito `RF09`, usaram-se aspas simples `` `aprovado' `` e `` `reprovado' ``, enquanto no restante do texto usam-se aspas duplas (`` ``...'' ``) ou itálico (`\textit{Aprovado}`).
3. **Padronização da linha de `Fonte:` em quadros e figuras:**
   - Os Quadros 2, 3, 4, 5 e 6 e a Tabela 1 usam a macro `\fonte{Elaborado pelo autor (2026).}` (que aplica `\footnotesize` padrão ABNT), enquanto o Quadro 1 (`ref_teorico.tex`, linha 83) e as Figuras 1 a 9 usam formatação manual com `\small` (`{\raggedright \small Fonte: ...}`). Usar `\fonte{...}` (ou `\footnotesize`) em todos uniformiza o tamanho da fonte das legendas inferiores.
4. **Linha horizontal solta após as Referências (`main.tex`, linhas 78–85):**
   - Logo abaixo de `\bibliography{bibliografia}`, há um bloco `\begin{minipage}{\textwidth} \rule{\textwidth}{0.5pt} ... \end{minipage}` vazio que imprime uma linha preta órfã no final da seção de Referências (última página do PDF). Recomenda-se remover as linhas 78–85 de `main.tex`.
5. **Elementos pré-textuais pendentes para a entrega final:**
   - **Lista de Tabelas (`main.tex`, linha 49):** `% \imprimirlistatabelas` está comentado, mas o documento possui a Tabela 1 no Capítulo 6 (`resultados.tex`).
   - **Resumo / Abstract e Palavras-chave (`main.tex`, linha 45; `pre_textuais/resumo.tex`; `macros.tex`, linhas 27–28):** ainda estão comentados e com o texto de exemplo do template.
   - **Banca e Ficha Catalográfica (`macros.tex`, linhas 21–38):** ainda contêm nomes fictícios (*Fulana de Tal*), ano `2019` e assuntos do template antigo (*Redes neurais / Expressão facial*).
