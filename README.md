# IA-900-Lab02
## Processo de execução realizado pelo laboratório:

1. **Criação da conta no Azure:**
   - Clique em "Criar um recurso" e selecione "Machine Learning".
   - Nas configurações, utilize o seguinte padrão:
     - Resource Group: Nomenclatura para agrupar os recursos.
     - Name: Nome do workspace.
     - Region: Escolha a região (Recomendado: Norte americana).
     - StoraAccount, Key Vault, Application Insights e Container Registry podem ser mantidos como estão.
   - As outras abas (Networking, Encryption, Identity e Tags) não precisam ser alteradas.
   - Após a conclusão, vá para "Review+create", verifique os dados e clique em "Create".

   Este processo pode levar algum tempo. Na página de "Overview", você pode verificar o progresso.

2. **Configuração do ML automatizado:**
   - Clique em "Go to resource" e depois em "Launch Studio".
   - No menu esquerdo, clique em "ML automatizado" e depois em "Novo trabalho de ML automatizado".
   - Preencha os campos conforme as informações do seu projeto.
   - Escolha a opção "Regression" na aba "Select task type".
   - Clique em "Next" e preencha os campos, selecionando "Tabular" como o tipo.
   - Escolha a opção "From web files" e insira a URL dos dados: [https://aka.ms/bike-rentals](https://aka.ms/bike-rentals).
   - Verifique as configurações do arquivo (Delimitado, Vírgula, UTF-8) e clique em "Next".
   - Confira os dados na aba final e clique em "Create".

3. **Configuração do treinamento:**
   - Selecione os dados criados e clique em "Next".
   - Defina a coluna target como "rentals (Integer)".
   - Em "Configurações adicionais", selecione "NormalizedRootMeanSquaredError" como a métrica principal.
   - Escolha os modelos "RandomForest" e "LightGBM" e feche a aba de configurações adicionais.
   - Expanda a visão de limite e ajuste os parâmetros:
     - Max Trials: 3
     - Max concurrent trials: 3
     - Max nodes: 3
     - Metric score threshold: 0.085
     - Experiment timeout: 15m
     - Interation timeout: 15m
   - Marque "Enable early termination" e escolha "Train validation split" como tipo de validação.
   - Avance até a aba de confirmação e aguarde o treinamento, que pode levar até 15 minutos.

4. **Validação dos dados e métricas:**
   - Clique em "Jobs" no menu lateral e selecione o modelo.
   - Na aba "Overview", encontre as métricas no menu lateral esquerdo.

5. **Criação de um endpoint:**
   - Crie um modelo e importe-o para a aba "Endpoint".
