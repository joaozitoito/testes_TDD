# Projeto João Vítor Goes - Aula 11

## 1. Preparar o ambiente

```bash
python --version
python -m pip install -r requirements.txt
python -m pytest --version
python -m pytest -q
```

## 2. Exercicio formativo

Implementar, usando TDD:

```python
calcular_taxa_entrega(distancia_km, total_pedido)
```

### Regras obrigatorias

1. Ate 3 km, a taxa de entrega e R$ 5.
2. Acima de 3 km, acrescentar R$ 2 por quilometro excedente.
3. Pedidos a partir de R$ 100 possuem entrega gratuita.

### Tres cenarios obrigatorios

- 2 km e pedido de R$ 50: taxa de R$ 5;
- 4 km e pedido de R$ 50: taxa de R$ 7;
- 5 km e pedido de R$ 100: taxa de R$ 0.

### Desafio opcional

- distancia negativa deve gerar `ValueError`.

## 3. Processo esperado

Para cada comportamento:

1. escreva somente o teste desse comportamento;
2. execute e confirme a falha (Red);
3. implemente o minimo necessario (Green);
4. execute toda a suite;
5. passe ao proximo comportamento;
6. ao final, melhore a estrutura sem alterar o comportamento (Refactor).

Nao implemente as tres regras de uma vez.

## 4. Registro do ciclo

Use `REGISTRO_TDD.md` para registrar pelo menos um ciclo completo.

## Observacao sobre venv

Na proxima aula sera utilizado `venv`, um ambiente virtual isolado que mantem os pacotes do projeto separados dos demais projetos Python.

## 5. Solucao e relatorio desta atividade

A funcao esta em `src/pedido.py`. Os tres testes obrigatorios estao em
`tests/test_taxa_entrega.py`; os quatro testes originais foram preservados.
O arquivo `REGISTRO_TDD.md` registra os tres ciclos executados.

No PowerShell, dentro desta pasta, instale as dependencias e gere o relatorio:

```powershell
python -m pip install -r requirements.txt
python -m pytest -v | Tee-Object -FilePath relatorio-testes.txt
```

Resultado esperado: sete testes aprovados. O relatorio incluido foi feito
com Python 3.12.14 e pytest 9.2.0.

Projeto-base do professor:
https://github.com/lucianozanuz/pbl-qualidade-software-2026-2/tree/main/praticas/aula-11-testes-unitarios-tdd
