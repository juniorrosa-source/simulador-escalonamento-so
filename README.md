# 💻 Simulador de Algoritmos de Escalonamento

**Trabalho Acadêmico | Desenvolvido em Dupla**
Disciplina de **Sistemas Operacionais** — Faculdade de Computação, **UFMS** (2026).

**Autores:** Heli Souza · Junior Rosa

---

## 📖 Sobre

Simulador em **Java** (interface textual) que executa e compara algoritmos clássicos de escalonamento de CPU. Lê os processos de um arquivo `.txt`, gera o log passo a passo da execução e exibe as estatísticas finais.

## ⚙️ Algoritmos

1. **FCFS** — First-Come, First-Served
2. **SJF Não Preemptivo** — Shortest Job First
3. **SJF Preemptivo (SRTF)** — Shortest Remaining Time First
4. **Prioridade** — menor número = maior prioridade
5. **Round Robin** — com *quantum* configurável
6. **Modo Comparativo** — executa todos sobre a mesma entrada

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
src/        → código-fonte (Simulador, Escalonador, Processo + 5 algoritmos)
exemplos/   → arquivos de teste (processos.txt, simples.txt)
compile.sh  → script de build e execução
```

## 📊 Saída

Para cada algoritmo, o simulador exibe:
- **Log de execução** (início, preempção, conclusão, CPU ociosa)
- **Tabela por processo** (chegada, burst, início, fim, espera, retorno)
- **Médias** de tempo de espera e retorno

---

📚 **UFMS — Sistemas Operacionais 2026** | Projeto de uso acadêmico.
