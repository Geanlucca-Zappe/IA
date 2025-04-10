# Metrô - Grafo de Estações

- **Barra Funda**
  - Palmeiras-Barra Funda
  - Marechal Deodoro
- **Palmeiras-Barra Funda**
  - Barra Funda
  - Paulista
  - Luz
- **Marechal Deodoro**
  - Barra Funda
  - Santa Cecília
- **Paulista**
  - Consolação
  - Palmeiras-Barra Funda
- **Luz**
  - Palmeiras-Barra Funda
  - Sé
  - República
- **Consolação**
  - Paulista
  - Clínicas
- **Santa Cecília**
  - Marechal Deodoro
  - República
- **Sé**
  - Luz
  - Anhangabaú
- **República**
  - Luz
  - Santa Cecília
  - Anhangabaú
- **Clínicas**
  - Consolação
  - Sumaré
- **Anhangabaú**
  - Sé
  - República
- **Sumaré**
  - Clínicas

## Função BFS (Busca em Largura - Caminho Mais Curto)

```python
def busca_em_largura(grafo, inicio, objetivo):
    fila = [[inicio]]  
    visitados = set()

    while fila:
        caminho = fila.pop(0)  
        no_atual = caminho[-1]

        if no_atual == objetivo:
            return caminho

        if no_atual not in visitados:
            visitados.add(no_atual)
            for vizinho in grafo.get(no_atual, []):
                novo_caminho = list(caminho)
                novo_caminho.append(vizinho)
                fila.append(novo_caminho)

    return None
