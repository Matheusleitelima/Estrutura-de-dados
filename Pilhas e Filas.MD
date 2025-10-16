# Introdução a Filas

## Conceito
A **fila** é uma estrutura de dados do tipo **FIFO (First In, First Out)** — ou seja, **o primeiro a entrar é o primeiro a sair**.

## Características
- O **primeiro elemento** da fila inicia na **posição 0**.  
- A fila é percorrida do **início (0)** até o **fim (última posição ocupada)**.  
- Exemplo de fila com tamanho 6 (índices de 0 a 5):
- **0** → Início da fila  
- **4** → Fim da fila  
- **5** → Final do vetor (limite máximo da estrutura)

# Lógica Circular

## Conceito
A **fila circular** é uma variação da fila tradicional, usada quando o **array tem tamanho fixo** e não pode receber mais elementos além do seu limite.

## Funcionamento
- A fila ocupa posições de **0 a 5** (por exemplo).  
- Quando o **último elemento** é preenchido, o **próximo elemento** deve ser inserido **no início do vetor**, aproveitando o espaço liberado por remoções anteriores.  
- Essa abordagem evita o desperdício de espaço em memória.

## Lógica de Implementação

A ideia principal é **fazer o índice “voltar” ao início** quando ultrapassar o limite máximo do vetor.  
Isso é feito usando o **operador módulo (%)**:

```c
f->fim = (f->fim + 1) % MAX;
# Operações Essenciais em Filas

As principais operações realizadas em uma fila são:  
- **Inserir (enqueue)**  
- **Retirar (dequeue)**  
- **Verificar (peek ou espiar)**  

Todas as funções precisam trabalhar de forma **integrada**, realizando verificações de estado — como identificar se a fila está **cheia** ou **vazia** — para garantir que o código funcione corretamente.  
Uma fila bem manipulada evita falhas e torna os processos mais **previsíveis, organizados e eficientes**.

---

## Inserir (Enqueue)

```c
void inserir(Fila *f, Elemento e) {
    if (filaCheia(f)) // Impede inserção se estiver cheia
        return;

    f->itens[f->fim] = e;            // Insere no final
    f->fim = (f->fim + 1) % MAX;     // Atualiza circularmente o índice
    f->total++;                      // Incrementa a contagem de elementos
}
Retirar (Dequeue)
Elemento retirar(Fila *f) {
    Elemento vazio = {-1};               // Valor padrão caso a fila esteja vazia
    if (filaVazia(f)) 
        return vazio;                    // Evita remoção se estiver vazia

    Elemento e = f->itens[f->inicio];    // Armazena o item a ser removido
    f->inicio = (f->inicio + 1) % MAX;   // Atualiza o índice de início
    f->total--;                          // Diminui o total
    return e;                            // Retorna o item removido
}
Verificar (Peek / Espiar)
Elemento espiar(Fila *f) {
    Elemento vazio = {-1};              // Valor padrão se a fila estiver vazia
    if (filaVazia(f))
        return vazio;                   // Impede acesso indevido

    return f->itens[f->inicio];         // Retorna o elemento da frente
}

# Declaração, Implementação e Uso da Fila

## Criando uma Fila

### Estrutura de Dados do Elemento

```c
typedef struct {
    char nome[30];
    int idade;
} Pessoa;
Estrutura da Fila
c
Copiar código
#define MAX 5

typedef struct {
    Pessoa itens[MAX];
    int inicio;
    int fim;
    int total;
} Fila;
A estrutura da fila contém:

itens → array fixo que armazena os elementos.

inicio → posição do primeiro elemento da fila.

fim → posição onde o próximo elemento será inserido.

total → quantidade de elementos atualmente na fila.

Inicializar a Fila
c
Copiar código
void inicializarFila(Fila *f) {
    f->inicio = 0;
    f->fim = 0;
    f->total = 0;
}
Inicializa a fila definindo todos os índices e o total de elementos como zero.

Verificar Fila Cheia e/ou Vazia
c
Copiar código
int filaCheia(Fila *f) {
    return f->total == MAX;
}

int filaVazia(Fila *f) {
    return f->total == 0;
}
Essas funções ajudam a controlar o estado da fila, evitando erros durante inserções e remoções.

Inserir (Enqueue) e Remover (Dequeue)
Inserir
c
Copiar código
void inserir(Fila *f, Pessoa p) {
    if (f->total == MAX) {
        printf("Fila cheia. Não é possível inserir.\n");
        return;
    }
 
    f->itens[f->fim] = p;
    f->fim = (f->fim + 1) % MAX;
    f->total++;
}
Adiciona um novo elemento ao final da fila, respeitando a lógica circular.

Remover
c
Copiar código
void remover(Fila *f, Pessoa *p) {
    if (filaVazia(f)) {
        printf("Fila vazia. Não é possível remover.\n");
        return;
    }

    *p = f->itens[f->inicio];             
    f->inicio = (f->inicio + 1) % MAX;     
    f->total--;                        
}
Remove o primeiro elemento da fila, atualizando o início de forma circular.

Mostrar Fila
c
Copiar código
void mostrarFila(Fila *f) {
    printf("Fila: ");
    for (int i = 0, idx = f->inicio; i < f->total; i++, idx = (idx + 1) % MAX) {
        printf("[%s, %d] ", f->itens[idx].nome, f->itens[idx].idade);
    }
    printf("\n");
}
Exibe todos os elementos da fila na ordem atual, facilitando a visualização e a depuração de erros.

Conclusão
Compreender como declarar, inicializar e manipular filas é essencial para manter a organização sequencial dos dados.
Os conceitos de fila cheia, vazia, inserção e remoção formam a base do seu funcionamento.

Mostrar a fila no console ajuda a entender visualmente o comportamento da estrutura e identificar possíveis erros.
Além disso, o uso de estruturas bem definidas e funções organizadas favorece o reuso e a escalabilidade em projetos, sejam eles simples ou complexos.


