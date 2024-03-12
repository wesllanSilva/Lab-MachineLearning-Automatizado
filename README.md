# Lab-MachineLearning-Automatizado
<h1>Explorando o Aprendizado de Máquina Automatizado no Microsoft AZURE</h1>
Neste Laboratório será usado um conjunto de dados de detalhes históricos de aluguel de bicicletas para treinar um modelo que prevê o número de aluguéis de bicicletas que devem ser esperados em um determinado dia, com base em características sazonais e meteorológicas.

Mais informações sobre como repelicar esse lab em:
https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html


Passo a Passo da solução 
1- Criada conta no portal azure 
2-Após criação da conta, criei um 'grupo de recursos' no Azure Machine Learning. ![image](https://github.com/wesllanSilva/Lab-MachineLearning-Automatizado/assets/62728922/158b4a97-1b6d-490e-bed4-7e1276e3b702)
3- Após Finalizada a criação do recurso  e  espaço de trabalho  criado,  será preciso acessar o 'estudio' ![image](https://github.com/wesllanSilva/Lab-MachineLearning-Automatizado/assets/62728922/2d2da4a0-86d5-4056-a557-25683a06a1ef)
4- Usando  o aprendizado de máquina automatizado para treinar um modelo(No estúdio de Aprendizado de Máquina do Azure, exibe a página ML automatizada (em Criação)).
![image](https://github.com/wesllanSilva/Lab-MachineLearning-Automatizado/assets/62728922/f7606ee8-75dd-4c76-9c86-fcb6465a3bd5)

5-Crie um novo trabalho de ML automatizado com as seguintes configurações, usando Avançar conforme necessário para progredir pela interface do usuário:

Configurações básicas:

-Nome do trabalho: mslearn-bike-automl
-Novo nome do experimento: mslearn-bike-rental
-Descrição: Aprendizado de máquina automatizado para previsão de aluguel de bicicletas
-Tags: nenhuma
-Tipo de tarefa & data:

Selecionar tipo de tarefa: Regressão
Selecionar conjunto de dados: crie um novo conjunto de dados com as seguintes configurações:
Tipo de dados:
Nome: bike-rentals
Descrição: Dados históricos de aluguer de bicicletas
Tipo: Tabular
Fonte de dados:
Selecionar de arquivos da Web
URL da Web:
URL da Web: https://aka.ms/bike-rentals
Ignorar validação de dados: não selecione
Configurações:
Formato de arquivo: Delimitado
Delimitador: Vírgula
Codificação: UTF-8
Cabeçalhos de coluna: Somente o primeiro arquivo tem cabeçalhos
Pular linhas: Nenhum
O conjunto de dados contém dados de várias linhas: não selecione
Esquema:
Incluir todas as colunas diferentes de Caminho
Revisar os tipos detectados automaticamente

Selecione Criar. Depois que o conjunto de dados for criado, selecione o conjunto de dados de aluguel de bicicletas para continuar a enviar o trabalho de ML automatizado.

Configurações da tarefa:

Tipo de tarefa: Regressão
Conjunto de dados: aluguel de bicicletas
Coluna de destino: Aluguéis (inteiro)
Definições de configuração adicionais:
Métrica primária: Erro quadrático médio da raiz normalizada
Explicar melhor modelo: Não selecionado
Use todos os modelos suportados: Nãoselecionado. Você restringirá o trabalho para tentar apenas alguns algoritmos específicos.
Modelos permitidos: selecione apenas RandomForest e LightGBM — normalmente você gostaria de tentar o maior número possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho.
Limites: expanda esta seção
Máximo de tentativas: 3
Máximo de tentativas simultâneas: 3
Nós máximos: 3
Limiar de pontuação métrica: 0,085 (de modo que, se um modelo atingir uma pontuação métrica quadrática média normalizada de 0,085 ou menos, o trabalho termina.)
Tempo limite: 15
Tempo limite de iteração: 15
Habilitar rescisão antecipada: Selecionado
Validação e teste:
Tipo de validação: Divisão de validação de trem
Porcentagem de dados de validação: 10
Conjunto de dados de teste: Nenhum
Computação:

Selecione o tipo de computação: Serverless
Tipo de máquina virtual: CPU
Camada de máquina virtual: Dedicado
Tamanho da máquina virtual: Standard_DS3_V2*
Número de instâncias: 1

Implantar e testar o modelo
Na guia Modelo para obter o melhor modelo treinado pelo seu trabalho de aprendizado de máquina automatizado, selecione Implantar e usar a opção Serviço Web para implantar o modelo com as seguintes configurações:
Nome: predict-rentals
Descrição: Prever aluguéis de ciclos
Tipo de computação: Instância de Contêiner do Azure
Habilitar autenticação: Selecionado
Aguarde o início da implantação - isso pode levar alguns segundos. O status de implantação para o ponto de extremidade de aluguel de previsão será indicado na parte principal da página como Em execução.
Aguarde até que o status Implantar seja alterado para Bem-sucedido. Isso pode levar de 5 a 10 minutos.
Testar o serviço implantado
Agora você pode testar seu serviço implantado.

No estúdio do Aprendizado de Máquina do Azure, no menu à esquerda, selecione Pontos de extremidade e abra o ponto de extremidade em tempo real de aluguéis de previsão.

Na página de ponto de extremidade em tempo real de aluguéis de previsão, exiba a guia Teste.

No painel Dados de entrada para testar o ponto de extremidade, substitua o modelo JSON pelos seguintes dados de entrada:


