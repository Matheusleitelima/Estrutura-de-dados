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


# Tipos de Estruturas de Dados – Lineares

## 🔹 Vetores
- Posições fixas.  
- Funcionam como caixas numeradas, em que cada posição guarda um valor.  

📌 **Exemplo:** tabela de notas de alunos em um sistema acadêmico.  
Cada posição do vetor representa a nota de um aluno específico.

---

## 🔹 Listas
- Estruturas flexíveis.  
- Semelhantes a vetores, mas cada elemento aponta para o próximo, como um colar de contas.  

📌 **Exemplo:** histórico de navegação em um navegador de internet, onde cada página visitada é ligada à próxima.

---

## 🔹 Pilhas
- Regra: **LIFO (Last In, First Out)**.  
- O último elemento que entra é o primeiro a sair.  

📌 **Exemplo:** desfazer ações (`Ctrl + Z`).

---

## 🔹 Filas
- Regra: **FIFO (First In, First Out)**.  
- O primeiro elemento que entra é o primeiro a sair.  

📌 **Exemplo:** fila de pedidos em um sistema de e-commerce.

Tipos de estruturas de dados – não lineares


