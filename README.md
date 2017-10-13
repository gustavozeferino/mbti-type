# mbti-type
https://www.kaggle.com/datasnaek/mbti-type/

# Personality types classification problem

## Considerações iniciais

No passado, para um problmea similar a este, utilizei Python para limpar e indexar os termos, R para os modelos estatísticos incluindo SVD, SQL para armazenar o modelo (scores tf-idf, etc) e Python novamente para executar o classificar (via chamada de linha de comando)
Para esta tarefa, escolhi utilizar somente sklearn que, mesmo provavelmente não sendo o melhor para produção, é um ambiente rápido para prototipação.

Um desafio a parte é instalar scipy no Windows (meu ambiente atualmente). Depois de diversas tentativas na mão, a solução final foi excluir tudo e instalar Anaconda. Resolveu.

## Estratégias inicias para o problema

As etapas iniciais para este tipo de problema se resuma a:
 * limpar a base de dados
 * aplicar algum tipo de ponderação
 * treinar e validar um classificador
 * Ajuste fino (tunning)

### Limpeza da base

Básico:

 * O separador "|||" foi introduzido para organizar a base, então ele deve ser removido. (feito)
 * Como o terno somente importa, colocar o texto em `lowercase` elimina ter dois termos iguais com escrita diferente
 * Outro procedimento na mesma linha é remover acentos, caracteres especiais, etc.
 * Quanto mais perto de um texto para pessoas, há necessidade de remover stopwords e correção de sinônimos

Focados no problema
* Remoção de tags de HTML, XML, etc.
* substituir os links pelo título da páginas que eles direcionam (mesmo que seja um vídeo, geralmente a páginas tem um título)
* Substituir os links pelo texto da página em questão (menos prioritário já que introduz muito ruído)

### Ponderação

 * Para texto, basicamente se resume a aplicar TF-IDF para "corrigir" a matriz de frequências e ter scores que diferencie mais os termos e seu impacto no documento
 * Entre as principais configurações do TF-IDF está a configuração do seu kernel de cálculo. Algo que sempre testo é a aplicação de logaritmo no cálculo (suavização se houver muita repetição de termos)
 * Aplicar SVD sobre a matriz de TF-IDF é algo a se considerar já que isto é muito utilizado em classificadores de texto incluíndo mecanismos de busca como o Google.


### Classificar

 * Dado que a base foi limpa e ponderada, é testar qual classificar se sai melhor e fazer seu ajuste. A maior parte do trabalho se concentra nas etapas anteriores







