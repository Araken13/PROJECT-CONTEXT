# 🌌 Project Context & Teleport System

![Python Version](https://img.shields.io/badge/python-3.8+-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

**Project Context** é um conjunto de ferramentas essenciais para desenvolvedores que trabalham com **Agentes de IA** (Code Assistants). Ele resolve dois grandes problemas:

1. **Memória Infinita**: Gera um contexto otimizado (PDR - Priority Document Ranking) do seu projeto para que a IA entenda todo o código sem alucinações.
2. **Teletransporte de Projetos**: Permite empacotar um projeto inteiro em um único arquivo de texto (`.txt`) e reconstruí-lo em qualquer outro ambiente (Docker, Nuvem, Outra Máquina) sem precisar configurar Git, chaves SSH ou dependências complexas.

---

## 📦 O Que Está Incluído?

| Componente | Função |
|------------|--------|
| **`orquestrador.py`** | 🎮 O Painel de Controle (CLI). É por onde você começa. |
| **`scripts/leitor_contexto_pdr.py`** | 📸 **Gerador**: Tira uma "foto" inteligente do projeto, ignorando lixo (`node_modules`, `venv`) e priorizando docs e código. |
| **`scripts/construtor_projeto.py`** | 🏗️ **Reconstrutor**: Lê a "foto" e recria o projeto físico (arquivos e pastas) no destino. |
| **`auto_leitor.py`** | 🤖 **Sentinela**: Monitora alterações em tempo real e atualiza o contexto para a IA automaticamente. |

---

## 🚀 Guia Rápido (Cenário Perfeito)

Imagine que você está desenvolvendo um App Complexo e quer pedir ajuda a uma **IA Avançada** ou mover o projeto para um servidor isolado.

### Passo 1: Orquestrar (Na Origem)

Execute o menu principal:

```bash
python orquestrador.py
```

Escolha a opção **[1] GERAR Contexto**.
*Resultado*: Um arquivo `PROJECT_CONTEXT_PDR.txt` é criado. Ele contém seu projeto inteiro.

### Passo 2: O Salto

Leve **apenas** este arquivo `.txt` e a pasta `scripts/` para o seu novo ambiente (ou anexe no chat da IA).

### Passo 3: Materializar (No Destino)

No novo ambiente, execute:

```bash
python orquestrador.py
```

Escolha a opção **[2] RESTAURAR Projeto**.
*Resultado*: O script lê o texto e **materializa** toda a estrutura de pastas, arquivos Python, React, Configurações, idênticos ao original.

---

## 🤖 Uso com Agentes de IA

Para garantir que seu Agente (Cortex, Cline, Devin) nunca se perca:

1. Mantenha o `auto_leitor.py` rodando em um terminal background.
2. Sempre que a IA disser "não vejo esse arquivo", digite o comando de regeneração (se configurado) ou deixe o auto-leitor trabalhar.
3. Use o arquivo `PROJECT_CONTEXT_PDR.txt` como a **Fonte da Verdade** no prompt do sistema.

### Comandos de Agente (Workflows)

Este repositório inclui definições de workflows para agentes compatíveis:

- `/pz` (Protocolo Zero): Força a IA a reler o contexto atualizado.
- `/restore`: Instrui a IA a executar a reconstrução do projeto.

---

## 🛠️ Instalação e Requisitos

A única dependência é **Python 3**. Nenhuma biblioteca externa (`pip install`) é estritamente necessária para as funções core, garantindo portabilidade máxima.

```bash
# Clone este repositório de ferramentas na raiz do seu projeto ou em uma subpasta
git clone https://github.com/SeuUsuario/project-context.git
```

---
*Desenvolvido para Hackathons, Migrações Rápidas e Integração com LLMs.*
