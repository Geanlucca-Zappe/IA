# Informações Importantes

- **Início:** Arad  
- **Objetivo:** Bucharest  
- Os valores nos caminhos representam a **distância entre cidades** (custo real).  
- A tabela à direita mostra as **distâncias em linha reta até Bucharest** (*heurística h(n)*).

---

## 1. Busca Gulosa (Greedy Best-First Search)

### Ideia:
- Sempre escolhe o vizinho com a **menor heurística** `h(n)`.
- **Não considera o custo acumulado** (distância real já percorrida).
- Foco em ir mais próximo do objetivo com base na **estimativa**.

### Execução:

**Estado inicial:** Arad  
**Heurística:** h(Arad) = 366

**Vizinhos:**
- Zerind (h = 374)
- Sibiu (h = 253) → menor
- Timisoara (h = 329)

Vai para **Sibiu**

---

**Estado:** Sibiu (h = 253)

**Vizinhos:**
- Arad (já visitado)
- Fagaras (h = 178) → menor
- Oradea (h = 380)
- Rimnicu Vilcea (h = 193)

Vai para **Fagaras**

---

**Estado:** Fagaras (h = 178)

**Vizinhos:**
- Sibiu (já visitado)
- Bucharest (h = 0)

Vai para **Bucharest**

---

### Caminho (Busca Gulosa):
**Arad → Sibiu → Fagaras → Bucharest**

---

## 2. Busca A* (A Estrela)

### Ideia:
- Usa: **f(n) = g(n) + h(n)**
  - `g(n)` = custo real acumulado até o nó  
  - `h(n)` = heurística (linha reta até Bucharest)
- Leva em conta o **caminho real + heurística**

### Execução:

**Estado inicial:** Arad  
- g(Arad) = 0  
- h(Arad) = 366  
- f(Arad) = 0 + 366 = 366

**Vizinhos:**
- Zerind → g = 75, h = 374, f = 449  
- Sibiu → g = 140, h = 253, f = 393  
- Timisoara → g = 118, h = 329, f = 447  

Vai para **Sibiu**

---

**Estado:** Sibiu  
- g = 140  
- h = 253  
- f = 393

**Vizinhos:**
- Fagaras → g = 239, h = 178, f = 417  
- Rimnicu Vilcea → g = 220, h = 193, f = 413  
- Oradea → g = 291, h = 380, f = 671  

Vai para **Rimnicu Vilcea**

---

**Estado:** Rimnicu Vilcea (g = 220)

**Vizinhos:**
- Pitesti → g = 317, h = 98, f = 415  
- Craiova → f = maior  
- Sibiu → já visitado  

Vai para **Pitesti**

---

**Estado:** Pitesti (g = 317)

**Vizinhos:**
- Bucharest → g = 418, h = 0, f = 418

Vai para **Bucharest**

---

### Caminho (Busca A*):
**Arad → Sibiu → Rimnicu Vilcea → Pitesti → Bucharest**

---

## Resumo Final

| Algoritmo       | Caminho encontrado                                     | Custo total                  |
|-----------------|--------------------------------------------------------|------------------------------|
| **Busca Gulosa**| Arad → Sibiu → Fagaras → Bucharest                    | 140 + 99 + 211 = **450**     |
| **Busca A\***   | Arad → Sibiu → Rimnicu Vilcea → Pitesti → Bucharest  | 140 + 80 + 97 + 101 = **418** |
