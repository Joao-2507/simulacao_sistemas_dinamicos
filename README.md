
<div align="center">

# ⚙️ Simulação de Sistemas Dinâmicos com Python

### Aplicações de Equações Diferenciais Ordinárias (EDOs)

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

</div>

---

## 📖 Sobre o projeto

Este projeto foi desenvolvido na disciplina de **Computação Numérica**, da Universidade Federal do Rio Grande do Norte (UFRN).

O objetivo é aplicar o **Método de Euler** na resolução numérica de Equações Diferenciais Ordinárias (EDOs), permitindo simular e analisar o comportamento de sistemas dinâmicos ao longo do tempo.

Foram estudados dois sistemas físicos:

1. **Sistema de Tanques Acoplados:** análise da evolução temporal da concentração de um soluto em dois tanques interconectados.
2. **Pêndulo Duplo:** simulação do movimento de um sistema mecânico não linear composto por duas massas conectadas por hastes rígidas.

Os resultados são apresentados por meio de gráficos de evolução temporal e retratos de fase.

---

## 🎯 Objetivos

- Implementar o Método de Euler para resolução de EDOs.
- Simular o comportamento de sistemas dinâmicos.
- Analisar a evolução temporal das variáveis de estado.
- Construir diagramas de fase.
- Investigar características de estabilidade e comportamento não linear.
- Interpretar os resultados obtidos numericamente.

---

## 🧮 Fundamentação matemática

### Método de Euler

O Método de Euler é um procedimento numérico utilizado para aproximar soluções de equações diferenciais ordinárias a partir de condições iniciais conhecidas.

Considerando uma equação diferencial:

$$
\frac{dy}{dt} = f(t,y)
$$

A aproximação pelo Método de Euler explícito é dada por:

$$
y_{n+1} = y_n + h f(t_n,y_n)
$$

Em que:

- $y_n$: valor aproximado da variável no instante atual.
- $y_{n+1}$: valor aproximado no instante seguinte.
- $h$: passo de integração.
- $f(t_n,y_n)$: derivada avaliada no instante atual.

O método é aplicado sucessivamente para determinar a evolução temporal do sistema.

---

## 🧪 Questão 1 — Sistema de Tanques Acoplados

### Descrição do problema

O primeiro sistema consiste em dois tanques interconectados, nos quais ocorre o transporte de um soluto por meio do fluxo de líquido.

O tanque 1 recebe uma solução com concentração conhecida, enquanto parte do líquido é transferida para o tanque 2.

O objetivo é determinar como as concentrações evoluem ao longo do tempo.

### Modelagem matemática

O sistema é descrito pelas seguintes equações diferenciais:

**Tanque 1:**

$$
\frac{dC_1}{dt} =
\frac{Q_{in}}{V_1}(C_{in}-C_1)
-
\frac{Q_{12}}{V_1}C_1
$$

**Tanque 2:**

$$
\frac{dC_2}{dt} =
\frac{Q_{12}}{V_2}(C_1-C_2)
-
\frac{Q_{out}}{V_2}C_2
$$

Em que:

- $C_1$ e $C_2$: concentrações dos tanques.
- $V_1$ e $V_2$: volumes dos tanques.
- $Q_{in}$: vazão de entrada.
- $Q_{12}$: vazão entre os tanques.
- $Q_{out}$: vazão de saída.
- $C_{in}$: concentração de entrada.

### Parâmetros utilizados

| Parâmetro | Valor |
|---|---|
| Volume do tanque 1 | 100 L |
| Volume do tanque 2 | 100 L |
| Vazão de entrada | 10 L/min |
| Vazão entre os tanques | 8 L/min |
| Vazão de saída | 1 L/min |
| Concentração de entrada | 1 g/L |
| Concentrações iniciais | 0 g/L |
| Tempo de simulação | 100 min |
| Passo de Euler | 0,01 min |

### Implementação numérica

As concentrações são atualizadas pelo Método de Euler:

$$
C_{1,n+1} = C_{1,n} + h\frac{dC_1}{dt}
$$

$$
C_{2,n+1} = C_{2,n} + h\frac{dC_2}{dt}
$$

### Resultados e discussão

A implementação apresenta:

- Evolução temporal das concentrações dos dois tanques.
- Retrato de fase relacionando as concentrações.
- Campo vetorial indicando a direção da evolução do sistema.

A análise permite observar que o tanque 1 responde mais rapidamente à entrada de soluto, enquanto o tanque 2 apresenta uma resposta mais gradual devido à dependência do fluxo proveniente do primeiro tanque.

O comportamento observado indica uma tendência de convergência para um estado de equilíbrio, caracterizando uma resposta estável para os parâmetros utilizados.

---

## 🔬 Questão 2 — Pêndulo Duplo

### Descrição do problema

O segundo sistema consiste em um pêndulo duplo formado por duas massas conectadas por hastes rígidas e sem massa, submetidas à ação da gravidade.

Diferentemente do sistema de tanques, o pêndulo duplo apresenta comportamento não linear, podendo demonstrar elevada sensibilidade às condições iniciais.

O objetivo é simular as posições e velocidades angulares das massas ao longo do tempo.

### Modelagem matemática

O sistema é descrito pelas variáveis de estado:

$$
\mathbf{x} =
\begin{bmatrix}
\theta_1 \\
\omega_1 \\
\theta_2 \\
\omega_2
\end{bmatrix}
$$

Em que:

- $\theta_1$: posição angular da primeira haste.
- $\theta_2$: posição angular da segunda haste.
- $\omega_1$: velocidade angular da primeira haste.
- $\omega_2$: velocidade angular da segunda haste.

As velocidades angulares são definidas por:

$$
\omega_1 = \frac{d\theta_1}{dt}
$$

$$
\omega_2 = \frac{d\theta_2}{dt}
$$

As acelerações angulares são calculadas a partir das equações não lineares do movimento do pêndulo duplo.

### Aplicação do Método de Euler

As velocidades angulares são atualizadas por:

$$
\omega_{1,n+1} = \omega_{1,n} + h\alpha_{1,n}
$$

$$
\omega_{2,n+1} = \omega_{2,n} + h\alpha_{2,n}
$$

As posições angulares são atualizadas por:

$$
\theta_{1,n+1} = \theta_{1,n} + h\omega_{1,n}
$$

$$
\theta_{2,n+1} = \theta_{2,n} + h\omega_{2,n}
$$

Em que $\alpha_1$ e $\alpha_2$ representam as acelerações angulares.

### Parâmetros utilizados

| Parâmetro | Valor |
|---|---|
| Massa 1 | 1 kg |
| Massa 2 | 1 kg |
| Comprimento da haste 1 | 1 m |
| Comprimento da haste 2 | 1 m |
| Gravidade | 9,81 m/s² |
| Ângulo inicial 1 | 1,55 rad |
| Ângulo inicial 2 | 1,05 rad |
| Velocidades angulares iniciais | 0 rad/s |
| Tempo de simulação | 20 s |
| Passo de Euler | 0,0001 s |

### Resultados e discussão

A implementação apresenta três representações gráficas:

**1. Evolução temporal dos ângulos**

Apresenta o comportamento das posições angulares das duas hastes durante a simulação.

**2. Evolução temporal das velocidades angulares**

Permite observar as variações das velocidades angulares em função do tempo.

**3. Retrato de fase**

Relaciona as posições e velocidades angulares, permitindo visualizar a complexidade das trajetórias.

Os resultados mostram um comportamento oscilatório complexo, característico de sistemas mecânicos não lineares.

As trajetórias simuladas apresentam variações irregulares, evidenciando a influência do acoplamento entre as hastes.

O pêndulo duplo é um sistema que pode apresentar comportamento caótico, dependendo das condições iniciais e dos parâmetros adotados.

---

## 🛠️ Tecnologias utilizadas

- **Python:** implementação das simulações numéricas.
- **NumPy:** operações matemáticas e manipulação de vetores.
- **Matplotlib:** visualização gráfica dos resultados.
- **Jupyter Notebook:** desenvolvimento e organização das implementações.

---

## 📂 Estrutura do projeto

```text
simulacao-sistemas-dinamicos-python/
│
├── README.md
├── Unidade3_oficial.ipynb
├── Projeto_U3.pdf
└── requirements.txt
```

---

## 🚀 Como executar

1. Clone ou baixe o repositório.
2. Instale Python e Jupyter Notebook.
3. Instale as dependências:

```bash
pip install numpy matplotlib notebook
```

4. Abra o notebook:

```bash
jupyter notebook Unidade3_oficial.ipynb
```

5. Execute as células sequencialmente.

O notebook contém as implementações dos dois sistemas, incluindo os cálculos numéricos e a geração dos gráficos.

---

## 📌 Conclusão

O projeto demonstrou a aplicação do Método de Euler na resolução numérica de sistemas dinâmicos descritos por Equações Diferenciais Ordinárias.

No sistema de tanques acoplados, foi possível observar a evolução das concentrações e a tendência de convergência para um estado de equilíbrio.

No pêndulo duplo, foram observadas trajetórias oscilatórias complexas, associadas ao comportamento não linear do sistema.

A comparação evidencia a versatilidade dos métodos numéricos na análise de diferentes fenômenos físicos, destacando a importância da simulação computacional para compreender sistemas dinâmicos.

---

## 👨‍💻 Autor

**João Victor Salústio**

Estudante de Engenharia da Computação — UFRN

[GitHub](https://github.com/Joao-2507) | [Currículo Lattes](http://lattes.cnpq.br/7048388853999078)
