# Comparação entre as versões dos dados e modelos

## 1. Versões avaliadas

Foram comparadas duas versões do classificador de chamados:

- **r1:** treinado com o dataset `chamados-v1`, que continha um erro de rotulagem no chamado de ID 006.
- **r2:** treinado com o dataset `chamados-v2`, após a correção do rótulo do chamado de ID 006 de `comum` para `urgente`.

## 2. Resultados da avaliação

Os dois modelos foram avaliados utilizando a mesma partição de teste, sem alteração do arquivo `split.csv`.

| Métrica | Modelo r1 | Modelo r2 |
|---|---:|---:|
| Acurácia | 0,75 | 1,00 |
| Recall — comum | 1,00 | 1,00 |
| Recall — urgente | 0,50 | 1,00 |

O modelo r2 apresentou melhoria na acurácia, que passou de 75% para 100%. O recall da classe urgente também passou de 50% para 100%, enquanto o desempenho na classe comum permaneceu em 100%.

## 3. Integridade e restauração

A restauração da tag `modelo-r1` foi realizada em uma cópia limpa do repositório, utilizando `git clone`, `git switch --detach modelo-r1` e `python -m dvc pull`.

A verificação SHA-256 confirmou a integridade dos três arquivos restaurados:

| Arquivo | SHA-256 esperado |
|---|---|
| `data/chamados.csv` | `590bbe63f34ea4fdd0e1cb1df9000c24c733714a14f78e5efb9938ea77123445` |
| `data/split.csv` | `6a29e570c9ea2461b48f1697380cccd79e8a26ab9f34037232299e33e1ef85f1` |
| `models/model.json` | `72a3a67936139a3473838a6dcfa7aae1acb4c23467be1ef1056d51d485b94840` |

Os três arquivos foram validados com sucesso na restauração.

## 4. Decisão

**Decisão: aceitar o modelo r2.**

A versão corrigida apresentou melhoria no desempenho geral e, principalmente, no reconhecimento de chamados urgentes, sem reduzir o recall da classe comum.

Além disso, a comparação foi realizada mantendo a mesma partição de teste, permitindo avaliar a mudança sem alterar o conjunto de dados utilizado na validação.

## 5. Conclusão

A atividade demonstrou como Git e DVC podem ser utilizados em conjunto para versionar código, dados e modelos. Também foi possível registrar diferentes versões, comparar resultados, armazenar artefatos e restaurar uma versão anterior com integridade verificada.