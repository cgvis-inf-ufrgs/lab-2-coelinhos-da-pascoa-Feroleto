# Relatório - Coelinhos da Páscoa

> [!CAUTION]
> - Lembre-se que você <ins>**não pode utilizar ferramentas de IA para
>   escrever este relatório**</ins>

## Dados do aluno

- **Cartão UFRGS**: 00587076
- **Nome**: Guilherme Hilgert Feroleto

## Passos que eu segui para resolver o problema especificado (em formato de *"prompt"*)

> [!IMPORTANT]
> - Coloque aqui todas as informações necessárias para que alguém
>   (pessoa ou ferramenta de IA) possa reproduzir os seus passos para
>   solucionar o problema
> - Escreva em formato imperativo, como se fosse um *prompt* com as
>   instruções a serem seguidas na solução do problema
> - Seja objetivo e conciso: quanto *menos palavras* você utilizar,
>   melhor
> - Seja técnico e use terminologia adequada: assuma que quem irá ler
>   os seus passos possui conhecimento de Ciência da Computação e
>   Computação Gráfica
> - Caso você queira incluir informações "longas" (como algum *prompt*
>   grande usado com alguma ferramenta de IA), crie arquivos à parte e
>   adicione links no texto (por exemplo, crie o arquivo `PROMPTS.md`
>   e adicione um link markdown `[os prompts detalhados estão
>   aqui](PROMPTS.md)`)
> - Novamente, lembre-se que você *não pode utilizar ferramentas
>   de IA para escrever este relatório*

DEFINIÇÂO DO TAMANHO DOS OBJETOS
- defina o tamanho do coelho com Matrix_Scale para ficar menor do que o tamanho padrão do programa;
- defina o tamanho da esfera, também com Matrix_Scale para ficar com tamanho proporcional ao do vídeo de demonstração;
- transformar a esfera em um ovo, aumentando o valor da coordenada y, para ficar mais com um formato oval;

DEFINIÇÂO DE PARÂMETROS AUXILIARES
- defina o tamanho da órbita que vai guiar o movimento do coelho;
- defina o distância entre cada coelho, como são 16 no total, distância entre cada pode ser 2pi/16;
- definir vetor de 16 posições, com valores de 0, pi/2, pi, 3pi/2, que vão dar a posição do coelho no movimento ondulatório;
- definir vetor de 16 posições, com valores de 0f à 15f, que vai dar a posição inicial de cada coelho na órbita se multiplicado com a distância entre os coelhos;

DEFINIÇÃO DOS PARÂMETROS DO COELHO
- mudar a direção para a qual o coelho está olhando, utilizando Matrix_Rotate_Y(-1.5708f) -> rotação de 90 graus;
- defina o movimento ondulatório do coelho, utilando Matrix_Translate() com a função seno;
- defina a posição do coelho na órbita, com Matrix_Translate(), passando o valor do raio do círculo na posição x;
- defina a rotação na órbita, com Matrix_Rotate_Y, utilizando o tempo decorrido * 0.5f + orbit_offset -> orbit_offset define a posição incial do coelho ao longo da órbita;

DEFINIÇÃO DOS PARÂMETROS DOS OVOS
- defina a rotação do ovo ao redor do coelho no eixo Z, utilizando Matrix_Rotate_Z()
- defina o deslocamento inicial do ovo com Matriz_Translate(), com 0.5f no eixo Y;
- defina a rotação dos ovos em torno do coelho, com Matrix_Rotate_Z(), definindo as posições iniciais como time * 2.0f e time * 2.0f + pi (segundo ovo), para cada um começar de um lado diferente do coelho;
- definir movimento ondulatório dos ovos usando Matrix_Translate, basicamente copiar trajetória do coelho;
- definir posição do ovo na órbita, usando Matrix_Translate, com a órbita do coelho na coordena X, pode copiar mesma transformação do coelho;
- definir movimento na órbita usando Matrix_Rotate_Y, com time * 0.5f + orbit_offset -> copiar movimento do coelho;

CÓPIA DE MAIS COELHOS E OVOS
- copiar esse modelo de um coelho com dois ovos girando ao seu redor para ter 16 coelhos no total e 32 ovos;
- verificar valores do vetor de que definem a posição inicial do moviemento ondulatório -> vetor que repete valores de 0 até 3pi/2;
- se o valor for 0, é necessário adicionar uma nova tranformação nas transformações matriciais;
- adicionar rotação do coelho no seu próprio eixo Z usando Matrix_Rotate_Z, com time * 2.0f para definir velocidade da rotação;
- essa transformação deve ser adicionada entre a Matrix_Scale e Matrix_Rotate_Y, deve ser a segunda transformação feita;

## Principais dificuldades encontradas durante o desenvolvimento (formato livre)

As principais dificuldades que tive durante o desenvolvimento foram acertar a ordem correta das transformações matriciais, fazer o movimento ondulatório dos coelhos ficar correto e fazer os ovos acompanharem os coelhos de maneira correta;

## Você acha que conseguiu resolver o problema de forma adequada?

Acredito que consegui resolver o problema de maneira adequada, pois ficou bem semelhante com o vídeo do resultado esperado;

## Se você quiser compartilhar mais alguma coisa, coloque aqui:



## Se você possui alguma sugestão para o professor sobre esta atividade, coloque aqui:


