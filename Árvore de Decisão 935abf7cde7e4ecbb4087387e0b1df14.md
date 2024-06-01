# Árvore de Decisão

Status: In progress

## Arvore de Decisão

- Conceito
    
    ![Untitled](A%CC%81rvore%20de%20Decisa%CC%83o%20935abf7cde7e4ecbb4087387e0b1df14/Untitled.png)
    
    - Conhecimento é feito pela busca até a árvore n-ária
    - Cada nó interno representa a condição/decisão sobre os atributos
    - **As folhas são o atributo alvo**
        - Classes
        - Rótulos numéricos
    - ***Uma árvore de decisão pode fazer predições para qualquer tipo de entrada,  pois ela abrande todos os espaços de uma instancia***
    - ***Se não podada, tende a ter overfiting***
    - **Funciona com:**
        - ***Valores Numéricos***, há alguma condição maior que x, menor que x
        - ***Valores categóricos*** (classes), True or false
    
    ![Untitled](A%CC%81rvore%20de%20Decisa%CC%83o%20935abf7cde7e4ecbb4087387e0b1df14/Untitled%201.png)
    
    - Pros
        - Barato computacionalmente
        - Lida bem com ***valores que estão faltando***
        - Lida bem com ***features que são irrelevantes***

- Complexidade do Modelo e Indução da Árvore
    - ***A altura da árvore*** está totalmente ligada a ***complexidade do modelo***
    
    ![Untitled](A%CC%81rvore%20de%20Decisa%CC%83o%20935abf7cde7e4ecbb4087387e0b1df14/Untitled%202.png)
    
    - **Algoritmo de Divisão e conquista**
        - CART
        - I3D
    - Árvore é dividida em sub espaços; S1, S2 …, Sn
    - Recursivamente é gerada uma árvore de decisão para cada sub-espaço Si
    - ***Pare*** quando a ***única árvore que puder ser gerada para um sub-espaço contiver um único nó folha*** - > calculo das impurezas( **Entropia De Shannon ou Impureza de Gini**)
        - Quando ***o valor é o mesmo que o da classe*** que está sendo analisado
    - Pseudo Código:
        
        ```python
        Algoritmo Induz_Árvore(S):
            T ← árvore vazia
        
            se todos os exemplos em S são de uma mesma classe cj:
                faça a raiz de T ser um nó folha associado a cj
            senão:
                Xbest ← selecione o melhor atributo para particionar S
                faça a raiz de T ser um nó interno associado a Xbest
        
                para cada valor xi do atributo Xbest:
                    Ss ← o sub-espaço de S no qual todos os exemplos têm o valor Xbest = xi
                    St ← Induz_Árvore(Ss)
                    insira St na árvore T com uma aresta da raiz para St associada à decisão Xbest = xi
        
            retorne T
        ```
        
        **OBS: COMO ACHAR O MELHOR XBEST ?? THE BEST WAY TO SPLIT THE TREE??**
        
- Como são divididos os dados na árvore? (**Xbest)**
    
    ![Untitled](A%CC%81rvore%20de%20Decisa%CC%83o%20935abf7cde7e4ecbb4087387e0b1df14/Untitled%203.png)
    
    - **Entropia de Shannon** (Usa teoria da informação)
        
        ![Untitled](A%CC%81rvore%20de%20Decisa%CC%83o%20935abf7cde7e4ecbb4087387e0b1df14/Untitled%204.png)
        
    - **Gini impurity -  Exemplo do slide**
        
        ![Untitled](A%CC%81rvore%20de%20Decisa%CC%83o%20935abf7cde7e4ecbb4087387e0b1df14/Untitled%205.png)
        
        - Aplica Gini para cada atributo
        - Média ponderada de todos os resultados, ***o que tiver o gini com resultado mais próximo de zero, ou zero, é a melhor escolha*** (Xbest)
    - **Gini vs Entropia**
        - Nem sempre os dois métodos concordam
        - Podem produzir árvores diferentes
        - Na média, tendem a ter desempenhos bem parecidos
        
        ![Untitled](A%CC%81rvore%20de%20Decisa%CC%83o%20935abf7cde7e4ecbb4087387e0b1df14/Untitled%206.png)
        
    
    - Construção da árvore com ***atributos categóricos(gini) - na mão!***
        
        ![Untitled](A%CC%81rvore%20de%20Decisa%CC%83o%20935abf7cde7e4ecbb4087387e0b1df14/Untitled%207.png)
        
        - Solução em PDF:
            
            
        - Árvore de decisão final:
            
            ![Untitled](A%CC%81rvore%20de%20Decisa%CC%83o%20935abf7cde7e4ecbb4087387e0b1df14/Untitled%208.png)
            
- Mind map
- Implementação em Código(entropia):