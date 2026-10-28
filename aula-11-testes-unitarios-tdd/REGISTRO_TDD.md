# Registro do ciclo de TDD

Atividade: Sábado Acadêmico de 24/10 — Qualidade de Software.

Os cenários foram implementados um por vez. Em cada etapa foi executada a suíte completa, incluindo os quatro testes originais de `calcular_total`.

## Ciclo 1 — Taxa básica

**Comportamento escolhido:** 2 km e pedido de R$ 50,00 devem gerar taxa de R$ 5,00.

### Red

**Teste criado:** `test_cobra_cinco_reais_para_dois_km_e_pedido_de_cinquenta`.

**Motivo da falha:** a função ainda não existia no módulo `src.pedido`; a chamada produziu `AttributeError`.

**Resultado observado:** `1 failed, 4 passed`.

### Green

**Implementação realizada:** criar `calcular_taxa_entrega(distancia_km, total_pedido)` retornando somente `5`.

**Resultado observado:** `5 passed`.

### Refactor

A implementação tinha apenas um retorno e não exigiu alteração estrutural.

## Ciclo 2 — Quilômetro excedente

**Comportamento escolhido:** 4 km e pedido de R$ 50,00 devem gerar taxa de R$ 7,00.

### Red

**Teste criado:** `test_cobra_sete_reais_para_quatro_km_e_pedido_de_cinquenta`.

**Motivo da falha:** a implementação retornava sempre 5; o teste esperava 7 (`assert 5 == 7`).

**Resultado observado:** `1 failed, 5 passed`.

### Green

**Implementação realizada:** manter o retorno 5 até 3 km e, acima desse limite, calcular `5 + (distancia_km - 3) * 2`.

**Resultado observado:** `6 passed`.

### Refactor

O cálculo já estava direto e sem duplicação que justificasse uma alteração.

## Ciclo 3 — Entrega gratuita

**Comportamento escolhido:** 5 km e pedido de R$ 100,00 devem gerar taxa de R$ 0,00.

### Red

**Teste criado:** `test_entrega_gratis_para_cinco_km_e_pedido_de_cem`.

**Motivo da falha:** o cálculo pela distância retornava 9; o teste esperava 0 (`assert 9 == 0`).

**Resultado observado:** `1 failed, 6 passed`.

### Green

**Implementação realizada:** verificar primeiro `total_pedido >= 100` e retornar 0 nesse caso, antes de calcular a taxa pela distância.

**Resultado observado:** `7 passed`.

### Refactor

Foi revisada a estrutura final: retornos diretos, condição de gratuidade antes da cobrança e nenhum código repetido que justificasse extração. Não foi necessária outra alteração de código.

## Relatório final

O arquivo `relatorio-testes.txt` é gerado com a execução real do comando PowerShell:

```powershell
python -m pytest -v | Tee-Object -FilePath relatorio-testes.txt
```

São sete testes ao todo: os quatro originais e os três obrigatórios da taxa de entrega.

O desafio opcional de rejeitar distância negativa não faz parte desta implementação.
