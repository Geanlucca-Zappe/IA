# Centro

- **Saco dos Limões**
  - Trindade
  - Costeira
    - Aeroporto
    - Campeche
- **Agronômica**
  - Cacupé
    - Sambaqui
    - Canasvieiras
      - Ingleses
    - Jurerê


## Função BFS (Busca em Largura)

```pseudo
Função BFS(grafo, nó_inicial, objetivo):
    Criar uma fila (queue)
    Criar uma lista para nós visitados (visitados)

    Enfileirar nó_inicial na fila
    Enquanto a fila NÃO estiver vazia:
        nó_atual ← desenfileirar da fila
        Se nó_atual ainda não estiver em visitados:
            Adicionar nó_atual à lista de visitados

            Se nó_atual == objetivo:
                Imprimir "Objetivo encontrado:", nó_atual
                Retornar visitados

            Para cada vizinho em grafo[nó_atual]:
                Enfileirar vizinho na fila

    Imprimir "Objetivo não encontrado"
    Retornar visitados
