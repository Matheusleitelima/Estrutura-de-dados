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
