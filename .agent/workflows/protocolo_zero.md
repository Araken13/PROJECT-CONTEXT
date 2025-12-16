---
description: Protocolo de Segurança Anti-Alucinação e Regrounding. Use este comando para forçar o agente a reler o contexto atualizado do projeto e eliminar erros de memória.
triggers:
  - /pz
  - /protocolo_zero
  - /reground
---

# 🛡️ Protocolo Zero: Anti-Alucinação

Este workflow é uma medida de segurança para garantir que a IA esteja operando com a "verdade" atual do projeto, eliminando alucinações causadas por janelas de contexto expiradas ou suposições incorretas.

## Gatilhos de Ativação Automática

O agente deve considerar auto-executar este protocolo se:

1. Encontrar erros repetitivos de `FileNotFoundError` em arquivos que deveriam existir.
2. Sugerir bibliotecas ou frameworks que não constam no `requirements.txt` ou `package.json`.
3. Receber feedback negativo do usuário sobre "perda de contexto" ou "esqueceu o que fizemos".

## Passos de Execução

1. **Atualização do Contexto (Freshness)**
   - Executar o script otimizado para gerar o "PDR" do projeto.
   - Isso garante que qualquer mudança recente (git pull, edições manuais) seja capturada.

   ```bash
   python scripts/leitor_contexto_pdr.py
   ```

2. **Leitura do Contexto (Ingestion)**
   - O agente deve ler o arquivo gerado para carregar a estrutura atual na memória ativa.
   - *Nota: O arquivo foi otimizado para caber no contexto (~140kb).*
   - Ação: Ler arquivo `PROJECT_CONTEXT_PDR.txt`

3. **Confirmação (Ack)**
   - O agente deve informar explicitamente ao usuário:
     > "🔄 **Protocolo Zero Executado**: Contexto PDR atualizado e carregado. Estou sincronizado com a versão mais recente do código."

// turbo-all
