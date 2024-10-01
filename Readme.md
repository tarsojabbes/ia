# Treinamento de um Modelo para Classificação de Tweets com Discursos de Ódio

Membros: Lucas de Medeiros Soares, João Henrique Almeida Xavier e Tarso Jabbes Lima de Oliveira

## Estrutura do Projeto

```bash
.
├── Dados
│   ├── 2019-05-28_portuguese_hate_speech_binary_classification.csv
│   ├── results_data2.csv
│   ├── test_data2.csv
│   ├── custom.csv
│   ├── custom_result.csv
│   └── train_data2.csv
├── Readme.md
├── Scripts
│   ├── Amostra.ipynb
│   ├── Avaliação.ipynb
│   ├── Bert.ipynb
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

## Ordem dos Notebooks

Para entender o projeto, a ordem do desenvolvimento foi:
1. Amostra.ipynb: contém os códigos necessário para tratar nossa amostra de dados, bem como dividí-la em treino/teste/avaliação.
2. Bert.ipynb: contém o código que avalia como o BERTimbau performa sem o fine tuning.
3. Treinamento.ipynb: contém o código que realiza o fine tuning do BERTimbau e verifica sua acurácia
4. Classificador.ipynb: contém o código que rotula nosso dataset de avaliação, e verifica a acurácia para tweets customizados que criamos
5. Avaliacao.ipynb: contém o código que verifica a acurária para nosso dataset de avaliação e monta a matriz de confusão

### Link do Dataset

O dataset utilizado pode ser encontrado no Kaggle: [Brazilian Portuguese Hate Speech Dataset](https://www.kaggle.com/datasets/hrmello/brazilian-portuguese-hatespeech-dataset?resource=download)

### Dataset

O dataset contém 5670 tweets escritos em Português e com a classificação indicando se há ou não discurso de ódio nele. A coluna `text` é o tweet em si e `hatespeech_comb` é a label para a presença de conteúdo odioso. O dataset originalmente não estava balanceado, mas fizemos o processo de balanceamento usando undersampling.

## Exemplos da base de dados

### Tweets com discurso de ódio
- @_iglira bom dia macaco branco haha
- "@_SsarahA @Ebandeira_ isso n ta errado, mas épesquisa de gente burra, a mulher trabalha menos que o homem"
- "abri a janela tava uma gorda no apartamento da frente olhando pra baixo e chorando, acho que caiu a empadinha dela"
- A Burra da mulher esqueceu o celular no ônibus e ta chorando aqui no busão queria não rir
- aff pq vc pinta o cabelo........td mundo sabe q vermelho e loiro só fica bom em tom de pele clara

### Tweets sem discurso de ódio
- @_carmeloneto Estes incompetentes não cuidam nem do povo brasileiro e nem dos poucos refugiados que aqui estão.
- aaaaaaa eu quero falar no meu trabalho sobre refugiados mas não sei se vou conseguir
- "Abaixo, apenas alguns exemplos de manifestação a favor do direito ao orgulho hetero."
- acho que o cara da redação do Enem deveria perder pontos pq não ficou claro o sabor do miojo
- @agdabritto Quero saber tudooo como foi o diaaaa!

### Tamanho da Amostra

- Total de amostras: 5670
- Tamanho dos dados balanceados:
  - Dados de treino: ~2000 linhas
  - Dados de teste: -500 linhas
  - Dados de avaliação: 1074 linhas


## Nosso dataset customizado
| query | label|
|--|--|
Essas pessoas só sabem reclamar. Não deveriam nem estar aqui bando de pretos.|1
Sempre a mesma coisa com esse grupo. Eles são a vergonha do país odeio esses nordestinos que não sabem votar!,|1
Esses incompetentes só atrapalham. Não servem pra nada!|1
Não acredito que deixam esse tipo de gente ter voz. É ridículo!|1
Gente assim deveria ser expulsa daqui. Não merecem estar entre nós.|1
O problema da nação é mulher que não sabe de nada e opina em tudo. Por que não resolvem isso logo?|1
Se esse grupo sumisse o mundo seria bem melhor quem suporta essa cabeça de caixa dagua|1
O que esperar desse tipo de pessoa? Só sabem destruir tudo.|1
Esses preguiçosos vivem às custas dos outros e do bolsa familia que lula manda. Lamentável!|1
Pessoas assim não têm lugar na nossa sociedade. Um absurdo total!|1
Eu realmente acredito que podemos construir um mundo melhor juntos.|0
É incrível como a diversidade faz a vida mais rica e interessante|0
Precisamos de mais amor e respeito no mundo. Tudo começa com empatia|0
Cada pessoa tem algo único a oferecer. Vamos valorizar isso|0
Admiro como algumas pessoas são resilientes e enfrentam os desafios|0
O importante é sempre procurar aprender com as diferenças|0
Devemos nos unir para criar uma sociedade mais justa e acolhedora|0
Nada supera o poder da gentileza. Pequenos gestos fazem a diferença|0
A troca de ideias é o que nos faz crescer como sociedade. Vamos dialogar mais|0
A empatia e o respeito são fundamentais para um convívio saudável|0


## Métricas do Treinamento

```json

 'eval_loss': 1.455265760421753,
 'eval_accuracy': 0.712,
 'eval_runtime': 14.6547,
 'eval_samples_per_second': 34.119,
 'eval_steps_per_second': 4.299,
 'epoch': 5.0

```


### Tempo de Treinamento

- **Duração Total:** 14 minutos
