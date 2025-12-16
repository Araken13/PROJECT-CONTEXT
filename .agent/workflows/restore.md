---
description: Reconstrói (hidrata) a estrutura de arquivos do projeto a partir de um arquivo de contexto único (PDR ou SUMMARY). Útil para migrar projetos entre ambientes sem git clone.
triggers:
  - /restore
  - /teleport
  - /hydrate
---

# 🏗️ Protocolo Restore: Hidratação de Projeto

Este workflow permite regenerar todos os arquivos físicos do projeto a partir de um "backup de texto" (Context File).

## Pré-requisitos

1. O arquivo de contexto (ex: `PROJECT_CONTEXT_SUMMARY.txt`) deve estar na raiz.
2. O script `scripts/construtor_projeto.py` deve estar acessível (se não estiver, o agente deve criá-lo primeiro).

## Passos de Execução

1. **Verificar Existência do Construtor**
   - O agente verifica se `scripts/construtor_projeto.py` existe.
   - Se não existir, o agente deve criar o arquivo com o código padrão de "Hidratação".

2. **Identificar Arquivo Fonte**
   - Procurar por `PROJECT_CONTEXT_SUMMARY.txt` ou `PROJECT_CONTEXT_PDR.txt`.

3. **Executar Reconstrução**
   - Rodar o script apontando para o arquivo fonte.

   ```bash
   python scripts/construtor_projeto.py PROJECT_CONTEXT_SUMMARY.txt
   ```

4. **Regrounding (Opcional)**
   - Após criar os arquivos, recomenda-se rodar o `/pz` (Protocolo Zero) para confirmar que o ambiente está saudável.
