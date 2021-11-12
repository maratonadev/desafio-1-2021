[![](https://img.shields.io/badge/IBM%20Cloud-powered-blue.svg)](https://cloud.ibm.com)
[![](https://img.shields.io/discord/734849242153222221?logo=discord)](https://discord.gg/yJYmTGDWKH)

# Desafio 01 | Bantotal

- [1. Sobre a Bantotal](#1-sobre-a-bantotal)
  - [1.1. Introdução](#11-introdução)
  - [1.2. Premiação](#12-premiação)
- [2. Desafio de negócio](#2-desafio-de-negócio)
- [3. Objetivo](#3-objetivo)
- [4. Tecnologias aplicadas](#4-tecnologias-aplicadas)
- [5. Desenvolvimento da solução](#5-desenvolvimento-da-solução)
  - [5.1. Pré-requisitos](#51-pré-requisitos)
  - [5.2. Resumo das tarefas](#52-resumo-das-tarefas)
  - [5.3. Desenvolvimento](#53-desenvolvimento)
- [6. Submissão](#6-submissão)
- [7. Sobre a avaliação](#7-sobre-a-avaliação)

## Para te ajudar

- [Material de Apoio](#material-de-apoio)

## 1. Sobre a Bantotal

### 1.1. Introdução

Bantotal é a plataforma bancária líder na América Latina, que resolve as operações de
missão crítica das Instituições Financeiras de forma simples e precisa.

A plataforma bancária Bantotal entrou no mercado em 1991 e tornou-se líder na
América Latina. Sua sede se encontra no Uruguai, onde também estão localizados seu
Departamento de Pesquisa e Desenvolvimento, seu Centro de Serviços de Manutenção
global e seu Centro de Treinamento. Possui escritórios comerciais e de serviços em:
Argentina, Chile, Colômbia, México, Peru e Uruguai. Seus Centros de
Desenvolvimento de Software estão localizados no Peru e no Uruguai.

### 1.2. Premiação

Será dado como premiação pela Bantotal, para cada uma das duas melhores pessoas
classificadas no desafio Bantotal, um Vale-Presente no valor de US$ 500.

## 2. Desafio de negócio

Cada vez que um cliente solicita um empréstimo a uma instituição financeira, diversos processos e controles internos são acionados, necessários para a avaliação da solicitação recebida. Desta forma, são analisadas manualmente muitas informações relacionadas com o perfil do cliente, destinos de crédito, atividade de trabalho, rendimentos, condições de habitação, entre outros dados demográficos. Além disso, a instituição utiliza os chamados bureaus de crédito para conhecer o histórico de crédito do cliente, a fim de definir o perfil de crédito do cliente. Em conjunto com outros registros próprios, informações de outros créditos, grau de conformidade e comportamento dos produtos contratados, a instituição aprova um valor a ser emprestado e um prazo para sua devolução ou rejeita a solicitação.

## 3. Objetivo

O desafio consiste em criar um modelo de inteligência artificial capaz de realizar uma análise de risco para predizer se um empréstimo a um cliente deve ser feito ou não. Para isso, espera-se a utilização de um modelo de Machine Learning capaz de realizar uma classificação. O modelo pode ser desenvolvido na plataforma [Watson Studio](https://cloud.ibm.com/catalog/services/watson-studio), e deve ser publicado em uma instância [Watson Machine Learning](https://cloud.ibm.com/catalog/services/machine-learning). O modelo deverá ser treinado com os conjuntos de dados disponibilizado nesse repositório, contendo dados de clientes de bancos, como dados demográficos, sobre suas contas e sobre o empréstimo que querem realizar.

## 4. Tecnologias aplicadas

Para este desafio serão utilizados os seguintes serviços da IBM Cloud:

- [Watson Studio](https://cloud.ibm.com/catalog/services/watson-studio), também conhecido como Cloud Pak for Data as a Service. Esse serviço permite o uso de uma gama de ferramentas relacionadas à Ciência de Dados, inclusive execução de Jupyter Notebooks com processadores na nuvem.

- [Watson Machine Learning](https://cloud.ibm.com/catalog/services/machine-learning) (WML). Esse serviço provê uma série de recursos para construção, treinamento e publicação de modelos de Machine Learning. Para validação do desafio pedimos que os participante enviem seus modelos em forma de uma publicação no WML. Dessa forma, conseguimos testar o modelo por meio de chamadas HTTP.

Recomendamos o uso da linguagem [Python](https://www.python.org/), com [Jupyter Notebooks](https://jupyter.org/), e por isso disponibilizamos exemplos de código com essas ferramentas para uso no Watson Studio. No entanto, o participante é livre para utilizar a linguagem e ferramenta que quiser para a resolução do desafio, contanto que consiga publicar o modelo no [Watson Machine Learning](https://cloud.ibm.com/catalog/services/machine-learning). Você pode verificar os _frameworks_ suportados [nesta página](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/pm_service_supported_frameworks.html?context=analytics&audience=wdp).

## 5. Desenvolvimento da solução

### 5.1. Pré-requisitos

Para realizar esse desafio você deverá cumprir os seguintes pré-requisitos:

- [Registrar-se na Maratona Behind the Code](https://maratona.dev/?register=true) e confirmar seu e-mail de cadastro;
- Possuir uma [conta na IBM Cloud](https://ibm.biz/Bdf8dW), podendo ser a conta Lite ou Pay-As-You-Go (não é necessário registrar-se no evento com o mesmo e-mail utilizado para criar sua conta na IBM Cloud).

### 5.2. Resumo das Tarefas

1. Instanciar os serviços do desafio na IBM Cloud: Watson Machine Learning (obrigatório), e Object Storage e Watson Studio (opcionais);
2. Caso for utilizar Watson Studio, baixar [o projeto](../../assets/project.zip) e importá-lo no seu serviço;
3. Ler e executar as instruções contidas no [Jupyter Notebook](../../assets/notebooks);
4. Alterar, validar e testar o seu modelo de Machine Learning, até estar satisfeito com o resultado;
5. Criar um deployment no Watson Machine Learning com o seu modelo;
6. Efetuar a submissão na [página do desafio](https://maratona.dev/challenges/1).

### 5.3. Desenvolvimento

O desafio consiste na elaboração de um modelo de Machine Learning para predição de risco de empréstimo, baseado em informações bancárias. Você deverá explorar os dados, tratá-los, e construir o modelo para predição.

O modelo deve receber como entrada os seguintes dados:

```json
[
  "ID",
  "CHECKING_BALANCE",
  "PAYMENT_TERM",
  "CREDIT_HISTORY",
  "LOAN_PURPOSE",
  "LOAN_AMOUNT",
  "EXISTING_SAVINGS",
  "EMPLOYMENT_DURATION",
  "INSTALLMENT_PERCENT",
  "SEX",
  "OTHERS_ON_LOAN",
  "CURRENT_RESIDENCE_DURATION",
  "PROPERTY",
  "AGE",
  "INSTALLMENT_PLANS",
  "HOUSING",
  "EXISTING_CREDITS_COUNT",
  "JOB_TYPE",
  "DEPENDENTS",
  "TELEPHONE",
  "FOREIGN_WORKER"
]
```

E como saída um valor binário que representa se o empréstimo deve ser permitido ou não (0 para não, 1 para sim).

**Atenção**: os dados disponibilizados neste desafio são fictícios, qualquer correlação com a realidade é mera coincidência.

Para começar, siga o passo-a-passo abaixo para importar o projeto do desafio com os dados e o Notebook em seu Watson Studio. Alternativamente, você pode executar o [Notebook](../../assets/notebooks/notebook-pt.ipynb) em outros ambientes também. No Notebook você encontrará todas as instruções para criar um modelo e publicá-lo no Watson Machine Learning.

#### Importando um projeto ao Watson Studio

Primeiro, [crie uma instância de Watson Studio](https://cloud.ibm.com/catalog/services/watson-studio) em sua conta da IBM Cloud, caso já não tenha, e entre na página inicial do [IBM Cloud Pak for Data as a Service](https://dataplatform.cloud.ibm.com/) através da instância.

Baixe o arquivo [project.zip](../../assets/project.zip) encontrado nesse repositório.

Na página inicial na seção `Work with data`, clique em `Create a project`.

![criando-projeto](https://s3.br-sao.cloud-object-storage.appdomain.cloud/maratona-static/create-project.png)

Após abrir a nova página, clique em `Create a project from a sample or file`.

![criando.png](https://s3.br-sao.cloud-object-storage.appdomain.cloud/maratona-static/creating.png)

Clique em `Drop a file here or browse for file to upload` ou arraste o seu arquivo para a área destacada.

![selecionando-arquivo](https://s3.br-sao.cloud-object-storage.appdomain.cloud/maratona-static/select-file.png)

Depois de fazer o upload, dê um nome ao seu projeto e uma descrição se quiser.

![nomeando](https://s3.br-sao.cloud-object-storage.appdomain.cloud/maratona-static/name.png)

Pronto!

Agora é só ir no seu projeto e na aba `Assets` para ver os arquivos e Notebooks listados.

![assets.png](https://s3.br-sao.cloud-object-storage.appdomain.cloud/maratona-static/assets.png)

A partir daqui, você poderá abrir o Notebook em seu projeto e seguir as instruções contidas nele para realizar o desafio.

## 6. Submissão

Com o modelo pronto, e online em uma instância de Watson Machine Learning, o último passo é realizar a submissão. Será aceita somente uma submissão para o desafio, então teste bem antes de fazer o envio.

Para realizar a submissão, você deverá acessar a página do desafio: [https://maratona.dev/challenges/1](https://maratona.dev/challenges/1) e enviar as credenciais do seu serviço, juntamente com um arquivo `.zip`, de até 10MB, contendo o código fonte da solução (lembre-se de remover dependências e datasets para não ocupar espaço). A página fará um teste para verificar que as credenciais estão corretas.

As avaliações só começarão a ocorrer após a primeira semana do desafio. No momento da submissão, as credenciais para acesso à sua solução serão guardadas, e usadas para avaliação posteriormente. **Não exclua nenhum serviço utilizado para o desafio antes da avaliação!** Se os serviços cujas credenciais foram enviadas não estiverem disponíveis na data de avaliação, a submissão ficará com nota zero. Nesse caso, uma nova submissão será permitida.

Você poderá acompanhar o status da submissão acessando a [página do desafio](https://maratona.dev/challenges/1), logando na sua conta.

## 7. Sobre a avaliação

Uma semana após o início do desafio, nosso sistema de avaliação automática começará as avaliações. Ele irá utilizar as credenciais enviadas para realizar testes no modelo enviado, e calcular uma pontuação numérica de 1 até 100, baseada na métrica [F<sub>1</sub>](https://en.wikipedia.org/wiki/F-score). Sua solução deve obrigatoriamente estar hospedada no Watson Machine Learning, e o arquivo `.zip` enviado deve conter todo o código utilizado para obter a solução. Caso contrário, a pontuação será zerada.

Caso o desafio seja entregue dentro do prazo de envio (até 21 de novembro), o participante receberá uma bonificação de 10% da pontuação total (10 pontos), independendo do resultado de seu desafio. A pontuação máxima possível, portanto, é 110 (100 de avaliação + 10 de bônus).

Após o prazo de envio, o participante ainda poderá realizar sua submissão até dia 12 de dezembro, mas sem receber o bônus.

**Atenção**: nos reservamos o direito de zerar a pontuação de uma submissão caso:

- O código fonte enviado não seja coerente com os resultados obtidos dos testes no modelo.
- Seja detectado plágio, de um ou mais participantes. Nesse caso, todos os participantes com a solução igual terão sua pontuação no desafio zerada.

## Material de apoio

- [Documentação do Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-overview.html)
- [Assuma o controle dos seus dados com o Watson Studio](https://developer.ibm.com/br/articles/overview-e-summary-ibm-watson-studio/)
- [Introdução ao IBM Watson Studio](https://developer.ibm.com/br/articles/introduction-to-ibm-watson-studio/)
- [Introdução ao IBM Cloud Pak for Data](https://developer.ibm.com/br/articles/get-started-with-ibm-cloud-pak-for-data/)
- [Desenvolva modelos de aprendizado de máquina com e sem AutoML](https://developer.ibm.com/br/articles/compare-model-building-with-and-without-automated-machine-learning/)
- [Técnicas de Modelagem Preditiva](https://developer.ibm.com/br/articles/ba-predictive-analytics2/)
- [Desenvolva um modelo preditivo de aprendizado de máquina de forma rápida e fácil com o IBM SPSS Modeler](https://developer.ibm.com/br/tutorials/desenvolva-um-modelo-preditivo-de-aprendizado-de-mquina-de-forma-rpida-e-fcil-com-o-ibm-spss-modeler/)
- [Resolva um problema de negócios e preveja uma inadimplência de empréstimo usando um conjunto de dados de risco de crédito alemão](https://developer.ibm.com/br/patterns/resolva-um-problema-de-negcios-e-preveja-uma-inadimplncia-de-emprstimo-usando-um-conjunto-de-dados-de-risco-de-crdito-alemo/)
- [Visualizar dados com Python ](https://developer.ibm.com/br/patterns/visualize-data-with-python/)
- [Crie um indicador de previsões do mercado de ações](https://developer.ibm.com/br/patterns/predicting-the-stock-market-in-watson-studio/)
- [Gere um notebook Python para modelos de pipeline usando AutoAI](https://developer.ibm.com/br/patterns/autoai-code-generation/)
- [Crie fluxos para analisar e prever dados em tempo real](https://developer.ibm.com/br/patterns/live-streaming-of-iot-data-predictions-using-streaming-analytics/)
- [Crie uma solução preditiva](https://developer.ibm.com/br/articles/ba-predictive-analytics3/)
- [Use uma solução preditiva](https://developer.ibm.com/br/articles/ba-predictive-analytics4/)
- [O que é Análise Preditiva?](https://developer.ibm.com/br/articles/ba-predictive-analytics1/)

Você também pode acessar o Discord oficial da Maratona 2021 para realizar perguntas e/ou interagir com outros participantes: [Discord](https://discord.gg/yJYmTGDWKH).

## License

Copyright 2021 Maratona Behind the Code

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
