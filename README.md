<p align="center">
  <img src="https://img.shields.io/badge/python-3.8+-blue.svg" />
  <img src="https://img.shields.io/badge/PyTorch--Geometric-orange.svg" />
  <img src="https://img.shields.io/badge/status-em--desenvolvimento-yellow.svg" />
</p>

# 🧬 Predição de Interações Medicamentosas usando RGCN

Este projeto implementa uma Rede Neural em Grafo Relacional (RGCN) para prever interações e efeitos colaterais em cenários de polifarmácia. O modelo utiliza estruturas químicas representadas por Morgan Fingerprints (1024 bits) e decodifica as interações através de um operador DistMult.

## 📌 Visão Geral

Prever como duas drogas interagem é um desafio crítico na medicina moderna. Com mais de 1317 tipos de relações (efeitos colaterais) e um grafo altamente denso de conexões, este modelo busca identificar padrões em dados esparsos para prever novos links de interação.

## 🏗️ Arquitetura do Modelo

O modelo foi otimizado para lidar com a alta esparsidade dos dados de entrada (95% de zeros nos fingerprints):

- Camada de Projeção Linear: Reduz a dimensionalidade inicial de 1024 bits para um espaço latente denso.
- Batch Normalization: Estabiliza o aprendizado e evita a explosão de gradientes.
- RGCN (Relational GCN): Duas camadas de convolução relacional que capturam a topologia do grafo.
- Decoder DistMult: Um operador de triplas (h, r, t) que calcula a probabilidade de uma interação existir com base nos embeddings das drogas e da relação.

## 📊 Dataset

- Nós: 645 drogas únicas.
- Arestas: ~4.6 milhões de conexões.
- Relações: 1317 tipos de efeitos colaterais.
- Features: 1024-bit Morgan Fingerprints.

## 🚀 Como Executar

1. Execute todas as células do notebook 'processamentoDeDados.ipynb'
2. Confira se o arquivo 'dados_prontos.pt' foi gerado 
3. Execute todas as células do notebook 'rgcn.ipynb'

## 📈 Lições Aprendidas
Durante o desenvolvimento, enfrentamos e resolvemos desafios comuns em GNNs:

Muro do 0.69 (Loss Plateau): Resolvido com a inclusão de camadas de normalização e ajuste de Learning Rate.

Overfitting: Controlado através da implementação de Dropout e aumento do Weight Decay.

Esparsidade: Tratada com uma camada de projeção inicial para amplificar o sinal químico das drogas.

## 👥 Autores

- Eduardo Oliveira Carvalho
- Guilherme Ferreira Martins Ramos
- Lucas Tuon de Matos
