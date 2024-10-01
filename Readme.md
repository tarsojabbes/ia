
# Treinamento de um Modelo para Classificação de Tweets com Discursos de Ódio

## Estrutura do Projeto

```bash
.
├── Dados
│   ├── 2019-05-28_portuguese_hate_speech_binary_classification.csv
│   ├── results_data.csv
│   ├── test_data.csv
│   └── train_data.csv
├── Readme.md
├── Scripts
│   ├── Amostra.ipynb
│   ├── Avaliação.ipynb
│   ├── Classificador.ipynb
│   └── Treinamento.ipynb
└── model
    ├── config.json
    ├── model.safetensors
    ├── special_tokens_map.json
    ├── tokenizer.json
    ├── tokenizer_config.json
    ├── training_args.bin
    └── vocab.txt
```

## Descrição do Projeto

Este projeto consiste no treinamento de um modelo de classificação para identificar tweets com discursos de ódio em português. Utilizando o dataset disponibilizado no Kaggle, realizamos o fine-tuning do modelo `neuralmind/bert-base-portuguese-cased` para melhorar sua performance nesta tarefa específica.

### Link do Dataset

O dataset utilizado pode ser encontrado no Kaggle: [Brazilian Portuguese Hate Speech Dataset](https://www.kaggle.com/datasets/hrmello/brazilian-portuguese-hatespeech-dataset?resource=download)

### Tamanho da Amostra

- Total de amostras: 5670
- Tamanho dos dados balanceados:
  - Dados de treino: 3968 linhas
  - Dados de avaliação: 1702 linhas



## Métricas do Treinamento

```json

  "eval_loss": 1.1703320741653442,
  "eval_accuracy": 0.7884130982367759,
  "eval_runtime": 8.647,
  "eval_samples_per_second": 91.824,
  "eval_steps_per_second": 11.565,
  "epoch": 5.0

```

## Configuração da Máquina Utilizada para Treinamento

- **Processador:** Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz
- **Memória RAM:** 32 GB (DDR4 2666MHz)
- **GPU:** NVIDIA Geforce RTX 2080 Ti 11GB

### Tempo de Treinamento

- **Duração Total:** 10 minutos e 42 segundos
