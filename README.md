# Qualidade dos Vinho

## O problema
O presente problema se refere aos dados de vinhos portugueses "Vinho Verde", que possuem
variantes de vinho branco e tinto. Devido a questões de privacidade, apenas variáveis
físico-químicas (input) e sensoriais (output) estão disponíveis (por exemplo, não há dados
sobre tipo de uva, marca do vinho, preço de venda, etc).

## Objetivo
Criar um modelo para estimar a qualidade do vinho.

### Estratégia de modelagem
Para modelagem dado que conjunto de dados não é muito grande, optei por não excluir nenhum valor por conveniência(e.g remoção de outliers), ao invés disso, decidi tratar as features que comprovadamente apresentavam valores não condizentes. Para o modelo, apesar de intuitivamente ser enxergado como um problema de classificação, optei por utilizar dos dois métodos(classificação e regressão) para mapear a variável resposta.
### Função de custo utilizada
Para os algoritmos de classificação, decidi utilizar de _cross-entropy_, dado que entropia é uma medida de desordem e a variável resposta é multi-classe.
Para os algoritmos de regressão, optei por utilizar de _mean squared error_, dado que não importa para o problema se a estimação errou por excesso(valores muito acima) ou por falta(valores muito abaixo).
### Modelo final
O modelo final utilizado foi o XGBoost, que utiliza da técnica de _Boosting_ em conjunto com árvores de decisão para otimização. Ele foi escolhido por apresentar os melhores resultados(acurácia e F1-score) após diversos modelos serem aplicados para o mesmo conjunto de dados.
### Validação do modelo
Para validação do modelo foi mensurado a acurácia e o F1-score em cima de uma parcela dos dados não utilizada no treinamento. A acurácia e F1-score foram escolhidos como métrica devido o modelo ter como objetivo a classificação dos dados. A acurácia foi escolhida por medir de forma eficiente os acertos(verdadeiros-positivos e verdadeiros-negativos) e o F1-score por apresentar a medida mais completa em relação aos estados-resposta da classificação, ou seja leva em consideração verdadeiros-positivos, verdadeiros-negativos, falsos-positivos e falsos-negativos.
### Resultados
Apesar do modelo apresentar capacidade de predição melhor que uma escolha aleatória(acurácia de 0.552), mesmo com a redução da variância da variável resposta, em vinhos classificados como ruins, medianos e bons, a performace do modelo deixa a desejar em comparação a resultados obtidos a outros conjuntos de dados, o que faz pensar que em questão de capacidade de entrega, em um aplicação de produção, este modelo não entregaria tanto valor.
A performace do modelo pode ser justificada pela:
* Pouca quantidade de dados;
* Conjunto de dados desbalanceados;
* Falta de features relacionadas a variável resposta;
* O próprio método questionável de avaliação de vinhos.

Apesar disso, o conjunto de dados apresentado permite um pouco mais exploração, deixando como planos para o futuro:
* Aplicação de métodos semi-supervisionados;
* Aplicação de métodos de detecção de anomálias para as classes menos ocorrentes;
* Aplicaççao de redes-neurais.
