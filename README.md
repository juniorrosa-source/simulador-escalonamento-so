<h1 align="center">💻 Simulador de Algoritmos de Escalonamento</h1>

<p align="center">
  <img src="docs/banner.svg" alt="Banner do Simulador" width="100%"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Java-8%2B-007396?style=flat-square&logo=openjdk&logoColor=white"/>
  <img src="https://img.shields.io/badge/Plataforma-Linux%20%7C%20macOS%20%7C%20Windows-2c3e50?style=flat-square"/>
  <img src="https://img.shields.io/badge/UFMS-Sistemas%20Operacionais%202026-005faf?style=flat-square"/>
  <img src="https://img.shields.io/badge/Status-Concluído-2ea44f?style=flat-square"/>
</p>

> **Trabalho Acadêmico | Desenvolvido em Dupla**
> Disciplina de **Sistemas Operacionais** — Faculdade de Computação, **UFMS** (2026).
>
> **Autores:** Heli Souza · Junior Rosa

---

## 📖 Sobre

Simulador em **Java** (interface textual) que executa e compara algoritmos clássicos de escalonamento de CPU. Lê os processos de um arquivo `.txt`, gera o log passo a passo da execução e exibe as estatísticas finais.

## ⚙️ Algoritmos

| # | Algoritmo | Tipo | Critério |
|---|-----------|------|----------|
| 1 | **FCFS** | Não preemptivo | Ordem de chegada |
| 2 | **SJF** | Não preemptivo | Menor burst |
| 3 | **SRTF** | Preemptivo | Menor tempo restante |
| 4 | **Prioridade** | Não preemptivo | Menor número = maior prioridade |
| 5 | **Round Robin** | Preemptivo | *Quantum* configurável |
| 6 | **Comparativo** | — | Executa todos na mesma entrada |

### Exemplo visual — Round Robin (quantum = 4)

<p align="center">
  <img src="docs/gantt.svg" alt="Diagrama de Gantt — Round Robin" width="100%"/>
</p>

## 📄 Formato do Arquivo de Entrada

```text
QUANTUM=20

# Nome  Chegada  Burst  Prioridade
P1      0        200    3
P2      40       180    1
P3      100      140    4
```

- Linhas com `#` são comentários.
- `QUANTUM=` define o quantum (ms) do Round Robin.
- Campo `prioridade` é opcional.

## 🚀 Como Executar

**Pré-requisito:** Java 8+

**Linux / macOS:**
```bash
chmod +x compile.sh
./compile.sh exemplos/processos.txt
```

**Windows:**
```cmd
mkdir bin
javac -d bin src\*.java
java -cp bin Simulador exemplos\processos.txt
```

## 🗂️ Estrutura

```
simulador-escalonamento-so/
├── src/        → código-fonte (Simulador, Escalonador, Processo + 5 algoritmos)
├── exemplos/   → arquivos de teste (processos.txt, simples.txt)
├── docs/       → ilustrações (banner, gantt)
└── compile.sh  → script de build e execução
```

## 📊 Saída

Para cada algoritmo, o simulador exibe:
- **Log de execução** — início, preempção, conclusão, CPU ociosa
- **Tabela por processo** — chegada, burst, início, fim, espera, retorno
- **Médias** — tempo de espera e tempo de retorno

```
========================================
  ALGORITMO: FCFS – First-Come, First-Served
========================================

--- Registro de Execução ---
  [t=0]   P1 iniciado (burst=200)
  [t=200] P1 concluído
  [t=200] P2 iniciado (burst=180)
  ...

--- Estatísticas Finais ---
Processo   Chegada    Burst      Início       Fim          Espera       Retorno
P1         0          200        0            200          0            200
P2         40         180        200          380          160          340
...

Tempo médio de espera  : 312.86 ms
Tempo médio de retorno : 449.43 ms
```

---

<p align="center">
  📚 <b>UFMS — Sistemas Operacionais 2026</b> · Projeto de uso acadêmico
</p>
