## Classificando imagens com TensorFlow. 
Bom pra quem não sabe meu nome é Washington, não sou bom em explicação e principalmente em conceitos teoricos mas vou tentar explicar o maximo que posso. 
O intuito desse tutorial é classificar imagens, ou seja, utilizar a rede neural que o proprio tensorflow fornece e fazer nosso treinamento para reconher determinado objeto ou outro tipo de coisa que deseja. 
Nossa base de treinamento será figuras geometricas. Agora vamos lá ....

## O que é o TensorFlow ?

O Tensorflow é uma biblioteca open source oferecida pela Google, utilizada para o aprendizado de máquina.
Explicação mais rapida do oeste ...... Acho melhor vc ler essa parte <3.(Depois coloco mais informação sobre o tensorflow)

Links para Estudo:

[Material 1](https://medium.com/@dehhmesquita/classificando-textos-com-redes-neurais-e-tensorflow-5063784a1b31)

[Material 2](http://www.cienciaedados.com/big-data-deep-learning-google-tensorflow/)

[Material 3](https://www.youtube.com/user/sentdex)

[Material 4](https://www.youtube.com/channel/UCWN3xxRkmTPmbKwht9FuE5A/videos)

## Instalação
1- Instale o Docker(Caso não tenha a versão de instalação do windows que o docker suporta, procure o Toolbox docker)[Docker](https://docs.docker.com/toolbox/toolbox_install_windows/)

2- Instale o Anaconda versão 3.6 [Anaconda](https://www.anaconda.com/download/)

3- Após instalação do Anaconda Execute o Anaconda Navigator.

3.1- Terá uma opção na bara lateral chamada Environments clique.

3.2- Aparecerá um base(root) altere a opção de installed para not installed, procure os seguites pacotes e instale

*opencv,tensorflow e o GPU tb, matplotlib e numpy


Ufa deu trabalho mas agora vai ....

## Vamos pro treinamento 
Baixe os arquivos no repositorio que disponibilizei para fazer seu treinamento ... Abra a pasta geometria e veja 3 tipos de pastas e com ela três tipos de imagens que iram ser classificadas!!! Essa pasta é o nosso dataseet, com ela será feito o treinamento.
Como o tensorflow separa quem é quem ? vc percebeu que o nome das pastas estão diferentes correto ? então ele reconhece o nome das pastas e cada pasta será um categoria diferente do seu classificador. (Disse que sou horrivel explicando kkk qualquer duvida fale whatsapp).


## Agora vamos lá 

1-Abra o docker 

2-Execute esse comando irá criar um maquina ja com tensorflow todo instalado coisa linda u.u
```
docker run -it tensorflow/tensorflow:1.0.0 bash
```
Apos instalação digite o comando exit

3- cria uma pasta chamada tf_files, copie e o cole os arquivos que estão nesse repositorio na pasta tf_files!!! LEMBRANDO QUE ESTÁ PASTA SERA CRIADA NO LOCAL  C:\Users\"nomepc"\tf_files .... 



4- Execute o comando abaixo(BUMMMMM mudou o docker ne? hahaha estamos bem entao). Se deu errado, a causa foi que o caminho para acessar a pasta está diferente. 

```
docker run -it \
  --publish 6006:6006 \
  --volume ${HOME}/tf_files:/tf_files \
  --workdir /tf_files \
  tensorflow/tensorflow:1.0.0 bash 
```
  
5- Agora vamos pro treinamento, execute esse comando se começa a contar GG SÓ ESPERE

```
python train.py \
  --bottleneck_dir=tf_files/bottlenecks \
  --how_many_training_steps=30 \
  --model_dir=inception \
  --summaries_dir=training_summaries/basic \
  --output_graph=retrained_graph.pb \
  --output_labels=retrained_labels.txt \
  --image_dir=geometria
  ```
  
[![Demo](https://pbs.twimg.com/media/DgPYH5pX0AAzo0t.jpg:large)]

lembre se caso queira fazer o treinamento novamente e mudou O NOME DA pasta que tá seu dataseet mude tambem o image_dir= 
Outro ponto importante é o steps vc pode aumentar para melhorar seu treinamento de acordo com quantidade de imagens que tem, geralmente UM bom é 500 ou acima, mas como estou fazendo um treinamento simples vou colocar só 30(AQUE É AGILIDADE E TRABALHO). 
Procure na internet depois o que é overfitt!!! É um fator determinante para o classificador  SER bom, irei fazer uma explicação breve.
Pense comigo, vc em uma prova não estuda pelo livro, basicamente decora as respostas das provas anteriores do seu professor. Quando muda o contexto da questões voce se sente perdido e acaba errando. O mesmo vale para um classificador de imagem se voce só treina com respostas parecidas, a maquina não aprende apenas decora as informações e a taxa de acerto será ruim. HAHAHA ANALOGIA BARRIL ESPERO QUE ENTENDA. 


6 - Geralmente em uma dataseet maior isso iria demorar um bom tempo, mas não é o caso desse treinamento.

7- Após encerar o treinamento, irá executar o comando logo a seguir. Esse comando irá verificar a porcetagem que a imagem corresponde as três categorias treinadas, ou seja, quadrado, esfera e triangulo. Caso queira mudar a imagem a ser executada é só alterar o final do comando para a imagem que deseja.

```
python label_image.py quadrado.jpg
```

verifique se bateu o resultado e teste as outras fts que estão contidas fora do dataseet ...
[![Demo](https://pbs.twimg.com/media/DgPYLJaWkAAuvli.jpg)]

## UAU Tensorflow é massa
Realmente ajuda bastante em um classificador de imagens, mas não aconselharia para outros tipos de analise exemplo uma analise de sentimentos através de texto. Qual motivo? o tensorflow é bastante complexo e exige que vc escreva muito codigo. Use o keras e seja feliz, ele utiliza como base o tensorflow e apresenta metodos/bibliotecas já prontas.

## Pronto agora vamos LEnDA fazer jogos de computação visual, hahahah quero meu nome nos artigos <3 uheuheuhe aceito de boas euhHEUHehUE ZUERA



