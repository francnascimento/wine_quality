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
### Resultados
