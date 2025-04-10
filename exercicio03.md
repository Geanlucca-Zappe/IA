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

## Função DFS (Busca em Profundidade)

```pseudo
Função DFS(grafo, nó_atual, objetivo, visitados):
    Se nó_atual ainda não está em visitados:
        Adicionar nó_atual à lista de visitados

        Se nó_atual == objetivo:
            Imprimir "Objetivo encontrado:", nó_atual
            Retornar Verdadeiro

        Para cada vizinho em grafo[nó_atual]:
            Se DFS(grafo, vizinho, objetivo, visitados) retornar Verdadeiro:
                Retornar Verdadeiro

    Retornar Falso
