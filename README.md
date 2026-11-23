# Versionamento de Dados e Modelos — Aula ML

## Objetivo

Este projeto demonstra o versionamento de dados e modelos de Machine Learning utilizando Git e DVC, incluindo correção de rótulos, treinamento, avaliação e restauração de versões anteriores.

## Requisitos

- Python 3
- Git
- DVC

## Armazenamento DVC

Os arquivos de dados e modelos são armazenados em um diretório externo ao repositório, configurado como `../dvc-storage`.

Para reproduzir a restauração em outro ambiente, configure um armazenamento DVC acessível contendo os objetos versionados.

## Restaurar uma versão

Clone o repositório:

```bash
git clone https://github.com/JG-Araujo/aula-ml.git
cd aula-ml
```

Selecione a versão desejada:

```bash
git switch --detach modelo-r1
```

Recupere os arquivos:

```bash
python -m dvc pull
```

Para restaurar a versão corrigida, utilize as tags `dados-v2` e `modelo-r2`, conforme necessário.