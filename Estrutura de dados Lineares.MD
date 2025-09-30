# Estrutura de Dados

Estrutura de dados, é um metodo de organização de forma eficiente. 

Estrutura de dados lineares: Vetores(Posição fixa) lista(sequencial) Pilhas(o ultimo a entrar eo primeiro a sair) filas(o primeiro que chega eo primeiro a sair) 

lista - gerenciar os contatos do celular  
fila: gerenciar pedidos de um site ecormece  
pilha: Control z do teclado  

## Sintaxe:
```c
struct Tarefa{
	char descricao[100];
	int prioridade;
	struct Tarefa* proxima; \\
};


## 🔹 Estruturas de Dados Lineares
- Organizam elementos em sequência, formando uma linha lógica contínua.  
- Cada elemento (exceto o primeiro e o último) tem um antecessor e um sucessor.  
- Facilitam o acesso sequencial.  
- Exemplos: **vetores (arrays)**, **listas ligadas**, **pilhas (stacks)** e **filas (queues)**.  
- Uso comum: ordenação, processamento em série, manipulação de listas, execução cronológica de tarefas e controle de operações empilhadas.

---

## 🔹 Estruturas de Dados Não Lineares
- Organizam elementos em forma de **hierarquia** (árvores) ou **rede complexa** (grafos).  
- Permitem múltiplas conexões entre os dados.  
- Não há uma sequência única de acesso.  
- Exemplos: **árvores** e **grafos**.  
- Uso comum: problemas envolvendo caminhos, conexões e tomadas de decisão, como sistemas de arquivos, mapas, redes sociais ou transporte.

