# ATIVIDADE 3: ANÁLISE LÓGICA A PARTIR DE UM CASO CONCRETO


## Proposições

- **P**: Ana vai à festa.
- **Q**: Bruno vai à festa.
- **M**: Bruno traz música.
- **R**: A festa é animada.

## Condições Lógicas

1. Se Ana vai, então Bruno também vai: `P → Q`.
2. Se Ana ou Bruno vai, então a festa é animada: `(P ∨ Q) → R`.
3. Se Ana não vai, a festa só será animada se Bruno trouxer música: `¬P → (M → R)`.

```python
# ATIVIDADE 3: ANÁLISE LÓGICA A PARTIR DE UM CASO CONCRETO

# Definição das proposições:
# P: Ana vai à festa.
# Q: Bruno vai à festa.
# M: Bruno traz música.
# R: A festa é animada.

def evaluate_R(P, Q, M):
    # Verifica a condição P → Q
    if P and not Q:
        return None  # Condição violada, combinação inválida

    # Avalia R conforme as condições
    if P or Q:
        R = True
    elif not P:
        if M:
            R = True
        else:
            R = False
    else:
        R = False
    return R

# Gerando todas as combinações possíveis de P, Q, M
from itertools import product

print("P\tQ\tM\tR")
for P, Q, M in product([True, False], repeat=3):
    R = evaluate_R(P, Q, M)
    if R is None:
        result = "Inválido"
    else:
        result = "Verdadeiro" if R else "Falso"
    print(f"{P}\t{Q}\t{M}\t{result}")
