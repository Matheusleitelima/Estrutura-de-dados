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


