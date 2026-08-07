# Painel de Gamificação — WM Temas Técnicos

Aplicação estática (um único arquivo `index.html`) para calcular e exibir os
resultados da Gamificação por **pessoa** e por **filial**, consolidando as
4 semanas de um mês. Todo o processamento acontece no navegador do usuário
— nenhum arquivo é enviado para um servidor, então pode ser hospedada
gratuitamente no GitHub Pages.

## Como publicar no GitHub Pages

1. Crie um repositório no GitHub (pode ser privado, se preferir restringir
   o acesso à equipe).
2. Suba o arquivo `index.html` para a raiz do repositório (branch `main`).
3. Vá em **Settings → Pages**, em "Source" selecione a branch `main` e a
   pasta `/ (root)`, salve.
4. Em alguns minutos o GitHub fornece uma URL do tipo
   `https://<usuario>.github.io/<repositorio>/` — é esse link que deve ser
   compartilhado com o time.

Não há build, servidor ou dependência de backend: é só o arquivo `.html`.

## Como usar

1. **Respostas semanais** — exporte do Microsoft Forms um `.xlsx` para cada
   semana do mês (4 arquivos) e envie um em cada campo "Semana 1"…"Semana 4".
   Cada planilha deve ter as colunas padrão do Forms (`ID`, `Email`, `Nome`,
   etc.) mais uma coluna **`Filial`** e as colunas de pergunta daquela
   semana — igual ao padrão dos arquivos de exemplo enviados
   (`arq1`, `arq2`, `arq3` → `res`).
2. **Gabarito** — assim que pelo menos uma planilha semanal é carregada, o
   painel detecta automaticamente todas as perguntas encontradas e libera o
   botão **"Baixar modelo do gabarito"**. Esse modelo é um `.xlsx` com duas
   colunas, `Pergunta` e `Resposta Correta`, já com o nome de cada pergunta
   pré-preenchido — só é preciso completar a resposta correta de cada uma e
   enviar esse arquivo de volta no campo "Gabarito".
3. O painel calcula a pontuação automaticamente: **1 ponto por pergunta
   respondida corretamente** (comparação de texto, ignorando maiúsculas/
   minúsculas, acentos e espaços nas pontas). Perguntas sem gabarito
   cadastrado aparecem destacadas e não entram na pontuação até serem
   completadas.
4. Os resultados aparecem em 3 abas:
   - **Ranking individual** — pontuação por pessoa, por semana e total do
     mês, com gráfico do Top 10.
   - **Por filial** — pontos totais, média por participante e taxa de
     participação de cada filial, com gráfico comparativo.
   - **Detalhe semanal** — participação e pontuação de cada uma das 4
     semanas, para acompanhar a evolução do mês.
5. O botão **"Exportar consolidado (.xlsx)"** baixa uma planilha com três
   abas (Ranking Individual, Por Filial, Resumo Semanal) — útil para
   arquivar o resultado do mês ou compartilhar por e-mail.

## Sobre a coluna "Filial"

Cada planilha semanal deve conter a coluna `Filial` preenchida por pessoa
(pode ser adicionada manualmente ou via uma pergunta fixa no Forms). O
painel usa essa coluna para agrupar os resultados por unidade. Se uma
pessoa aparecer com filiais diferentes em semanas diferentes, prevalece a
última informada.

## Sobre o gabarito

O arquivo de gabarito deve ter o **mesmo texto da pergunta** usado como
cabeçalho de coluna nas planilhas semanais (é assim que o painel casa a
pergunta com a resposta correta). Por isso o fluxo recomendado é sempre
baixar o modelo gerado automaticamente pelo próprio painel, em vez de criar
o arquivo do zero.

## Limitações conhecidas

- Comparação de resposta é por igualdade de texto — bom para perguntas de
  múltipla escolha ou Sim/Não; para perguntas dissertativas, sem gabarito
  exato, a pergunta pode ficar sem pontuação automática.
- Se o mesmo e-mail responder mais de uma vez na mesma semana, os pontos de
  todas as respostas daquela semana são somados.
