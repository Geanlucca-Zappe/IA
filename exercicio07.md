# PROBLEMA: Controle Inteligente de Aquecimento de uma Cafeteira

## 🔎 Descrição do problema
Uma cafeteira precisa manter a bebida quente sem superaquecer ou gastar energia à toa.  
Um controle ON/OFF simples pode causar flutuações de temperatura.

**Solução:**  
Utilizar **lógica fuzzy** para controlar de forma suave a potência do aquecedor com base em:
- Temperatura atual da bebida
- Variação da temperatura ao longo do tempo (derivada)

---

## 🔢 ENTRADAS (Sensores)

### 1. Sensor de Temperatura 
- Mede a temperatura atual da bebida  
- **Universo:** [20 °C, 100 °C]  

#### Conjuntos Fuzzy:
- Frio
- Morno
- Quente

#### Funções de Pertinência:
- **Frio:** máximo em 20 °C, 0 em 50 °C  
- **Morno:** 0 em 40 °C e 80 °C, máximo em 60 °C  
- **Quente:** 0 em 60 °C, máximo em 100 °C  

---

### 2. Variação da Temperatura
- Estimada pela diferença entre duas leituras em intervalo fixo  
- **Universo:** [-5, +5]

#### Conjuntos Fuzzy:
- Esfriando Rápido
- Estável
- Aquecendo

#### Funções de Pertinência:
- **Esfriando:** máximo em -5, 0 em -1  
- **Estável:** pico em 0, 0 em -1 e +1  
- **Aquecendo:** 0 em +1, máximo em +5  

---

## ⚙️ SAÍDA (Atuador)

### Aquecedor (PWM via transistor)
- **Universo:** [0, 255] (nível PWM)

#### Conjuntos Fuzzy:
- Baixa Potência
- Média Potência
- Alta Potência

#### Funções de Pertinência:
- **Baixa:** máximo em 0, 0 em 100  
- **Média:** 0 em 50 e 200, pico em 127  
- **Alta:** 0 em 150, máximo em 255  

---

## 📜 REGRAS FUZZY

| Temperatura | Variação     | Potência Aquecedor |
|-------------|--------------|---------------------|
| Frio        | Esfriando    | Alta Potência       |
| Morno       | Esfriando    | Média Potência      |
| Quente      | Estável      | Baixa Potência      |
| Morno       | Estável      | Média Potência      |
| Frio        | Estável      | Alta Potência       |
| Quente      | Aquecendo    | Baixa Potência      |
| Morno       | Aquecendo    | Baixa Potência      |

---

## 🧠 FUNCIONAMENTO DO SISTEMA

1. O **Arduino** lê a temperatura atual via sensor.
2. Calcula a **variação da temperatura** com base em medições anteriores.
3. A **lógica fuzzy** interpreta os valores de entrada e aplica as regras fuzzy.
4. O sistema ajusta o **PWM** para controlar a potência do aquecedor.
5. O objetivo é **manter a bebida quente**, com o **mínimo de oscilação** de temperatura e o **menor consumo de energia** possível.

---

