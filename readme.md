# Diagnóstico Médico com Raios-X de Tórax usando Deep Learning

Bem-vindo à aplicação de IA para diagnóstico médico!

Nesta aplicação, construímos um classificador de imagens de raios-X de tórax utilizando a biblioteca Keras e técnicas de deep learning, com o objetivo de identificar 14 diferentes condições patológicas.

## Objetivos do Projeto

- Pré-processar e preparar um conjunto de dados de raios-X do mundo real.
- Utilizar aprendizado por transferência para treinar um modelo DenseNet121 para classificação de imagens de raios-X.
- Lidar com o desequilíbrio de classes no conjunto de dados.
- Mensurar o desempenho do modelo utilizando a métrica AUC (Área Sob a Curva) da curva ROC.
- Visualizar a atividade do modelo usando GradCAMs.

## Conjunto de Dados

O projeto utiliza o conjunto de dados "ChestX-ray8", que contém 108.948 imagens de raios-X de visão frontal de 32.717 pacientes. Cada imagem foi rotulada para identificar até 14 condições patológicas diferentes, que foram anotadas por quatro radiologistas para 5 das patologias.

Fornecemos um subconjunto de ~1000 imagens para treinamento, validação e teste:

- `nih/train-small.csv`: 875 imagens para treinamento
- `nih/valid-small.csv`: 109 imagens para validação
- `nih/test.csv`: 420 imagens para teste

## Principais Bibliotecas Utilizadas

- **Numpy** e **Pandas**: Manipulação de dados
- **Matplotlib** e **Seaborn**: Visualização de dados
- **Keras**: Construção de modelos de deep learning com TensorFlow

## Etapas do Projeto

### 1. Preparação de Dados

- **Prevenção de Vazamento de Dados**: Garantimos que a divisão dos dados foi realizada no nível do paciente para evitar que informações dos mesmos pacientes apareçam em conjuntos de treinamento, validação e teste.
- **Aumento de Dados**: Utilizamos a classe `ImageDataGenerator` do Keras para preparar os dados, incluindo normalização e transformação para um formato de três canais (RGB).

### 2. Desenvolvimento do Modelo

- Utilizamos um modelo pré-treinado DenseNet121 para aproveitar o aprendizado de transferência.
- O modelo foi treinado para classificar as imagens em uma ou mais das 14 condições patológicas.

### 3. Lidando com Desequilíbrio de Classes

O conjunto de dados apresenta um grande desequilíbrio de classes. Para lidar com isso, implementamos uma função de perda ponderada que ajusta a contribuição de cada classe para a função de perda durante o treinamento.

### 4. Avaliação do Modelo

Utilizamos as métricas AUC e ROC para avaliar o desempenho do modelo. Quanto maior a área sob a curva ROC, melhor o desempenho do modelo na classificação das condições patológicas.

### 5. Visualização com GradCAM

Utilizamos a técnica GradCAM para visualizar onde o modelo "olha" ao fazer suas predições, permitindo identificar as áreas mais importantes na imagem para cada condição patológica.

## Como Executar

1. Clone o repositório.
2. Instale as dependências listadas no `requirements.txt`.
3. Execute o notebook Jupyter fornecido para treinar e avaliar o modelo.
4. Utilize as funções `predict_generator` e `compute_gradcam` para gerar previsões e visualizações.

## Referências

- [Artigo CheXNet](https://arxiv.org/abs/1711.05225)
- [Artigo CheXpert](https://arxiv.org/pdf/1901.07031.pdf)
- [Artigo ChexNeXt](https://journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.1002686)

## Contribuindo

Sinta-se à vontade para contribuir com melhorias para este projeto. Envie um pull request ou abra uma issue para discutir possíveis mudanças.

## Licença

Este projeto é licenciado sob os termos da licença MIT.
