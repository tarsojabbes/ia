
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

### Dataset

O dataset contém 5670 tweets escritos em Português e com a classificação indicando se há ou não discurso de ódio nele. A coluna `text` é o tweet em si e `hatespeech_comb` é a label para a presença de conteúdo odioso. O dataset originalmente não estava balanceado, mas fizemos o processo de balanceamento usando undersampling.

## Exemplos da base de dados

### Tweets com discurso de ódio
@_iglira bom dia macaco branco haha,1
"@_SsarahA @Ebandeira_ isso n ta errado, mas épesquisa de gente burra, a mulher trabalha menos que o homem",1
"abri a janela tava uma gorda no apartamento da frente olhando pra baixo e chorando, acho que caiu a empadinha dela",1
A Burra da mulher esqueceu o celular no ônibus e ta chorando aqui no busão queria não rir,1
aff pq vc pinta o cabelo........td mundo sabe q vermelho e loiro só fica bom em tom de pele clara,1

### Tweets sem discurso de ódio
@_carmeloneto Estes incompetentes não cuidam nem do povo brasileiro e nem dos poucos refugiados que aqui estão.,0
aaaaaaa eu quero falar no meu trabalho sobre refugiados mas não sei se vou conseguir,0
"Abaixo, apenas alguns exemplos de manifestação a favor do direito ao orgulho hetero.",0
acho que o cara da redação do Enem deveria perder pontos pq não ficou claro o sabor do miojo,0
@agdabritto Quero saber tudooo como foi o diaaaa!,0

### Tamanho da Amostra

- Total de amostras: 5670
- Tamanho dos dados balanceados:
  - Dados de treino: 2502 linhas
  - Dados de avaliação: 1074 linhas


## Métricas do Treinamento

```json

 'eval_loss': 1.455265760421753,
 'eval_accuracy': 0.712,
 'eval_runtime': 14.6547,
 'eval_samples_per_second': 34.119,
 'eval_steps_per_second': 4.299,
 'epoch': 5.0

```

## Configuração da Máquina Utilizada para Treinamento

- **Processador:** Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz
- **Memória RAM:** 32 GB (DDR4 2666MHz)
- **GPU:** NVIDIA Geforce RTX 2080 Ti 11GB

### Tempo de Treinamento

- **Duração Total:** 10 minutos e 42 segundos
