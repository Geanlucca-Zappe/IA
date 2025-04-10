# Busca Gulosa - Implementação em Python

## Ideia:
- Usa somente a heurística `h(n)` para tomar decisões.
- Sempre escolhe o vizinho com **menor valor heurístico**.
- **Não considera o custo real** entre os nós (g(n)).

---

## Código:

```python
def busca_gulosa(nos, heuristicas, arestas, inicio, objetivo):
    visitados = [False] * len(nos)
    caminho = []
    atual = inicio

    while atual != objetivo:
        caminho.append(atual)
        visitados[atual] = True

       
        vizinhos = [
            (dest, heuristicas[dest])
            for (orig, dest, custo) in arestas
            if orig == atual and not visitados[dest]
        ]

        if not vizinhos:
            print("Não há caminho para o objetivo.")
            return

       
        proximo = min(vizinhos, key=lambda x: x[1])[0]
        atual = proximo

    caminho.append(objetivo)

    caminho_legivel = " -> ".join([str(n) for n in caminho])
    print("Caminho encontrado:", caminho_legivel)
