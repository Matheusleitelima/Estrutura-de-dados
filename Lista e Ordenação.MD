# 📘 Listas Lineares em C — Estáticas e Dinâmicas

Este documento explica o conceito de **listas lineares** na linguagem C, apresentando a diferença entre as **estáticas (vetores)** e as **dinâmicas (alocadas com ponteiros)**, com exemplos práticos e explicações.

---

## 🔹 Lista Linear Estática

Uma **lista estática** é uma estrutura de dados onde os elementos são armazenados **em posições contíguas de memória** e o **tamanho é fixo** — definido no momento da declaração.

- A memória é reservada de forma contínua.
- Não é possível aumentar ou diminuir o tamanho da lista durante a execução.
- O acesso aos elementos é feito diretamente por **índice**.

📦 **Exemplo prático:**  
Imagine uma prateleira com divisórias fixas.  
Cada espaço só comporta um item, e, quando todos os espaços estão ocupados, **não há como adicionar mais** sem remover outro.

l, l + c, l + 2c ...

cpp
Copiar código
Cada elemento ocupa uma posição de memória contígua.

### 🧠 Exemplo em C

```c
#include <stdio.h>

int main() {
    int numeros[5] = {10, 20, 30, 40, 50};

    printf("%d", numeros[2]);  // Imprime 30
    return 0;
}
📍 Resumo:

Lista com 5 posições fixas.

Não é possível alterar o tamanho após a criação.

🔹 Lista Linear Dinâmica
A lista dinâmica é uma estrutura que também armazena elementos em sequência,
mas pode crescer ou diminuir durante a execução do programa conforme necessário.

Usa ponteiros e funções de alocação dinâmica de memória:

malloc → aloca espaço inicial.

realloc → redimensiona mantendo os dados antigos.

free → libera a memória quando não for mais usada.

📦 Exemplo prático:
Imagine uma caixa dobrável que pode expandir ou diminuir o tamanho conforme você adiciona ou remove itens.

🧠 Exemplo em C
c
Copiar código
#include <stdio.h>
#include <stdlib.h>

int main() {
    // 1. Criar a lista com 3 posições
    int* numeros = (int*) malloc(3 * sizeof(int));

    // 2. Atribuir os valores iniciais
    numeros[0] = 10;
    numeros[1] = 20;
    numeros[2] = 30;

    // 3. Expandir a lista para 5 posições
    numeros = (int*) realloc(numeros, 5 * sizeof(int));

    // 4. Atribuir novos valores
    numeros[3] = 40;
    numeros[4] = 50;

    // Exibir os valores da lista
    for (int i = 0; i < 5; i++) {
        printf("%d ", numeros[i]);
    }

    // Liberar memória
    free(numeros);
    return 0;
}
📍 Resumo:

Pode crescer e diminuir conforme a necessidade.

A alocação de memória é feita em tempo de execução.

Exige o uso de ponteiros e funções específicas de gerenciamento de memória.

⚙️ Funções Importantes
Função	Descrição
malloc()	Aloca dinamicamente um bloco de memória.
realloc()	Redimensiona um bloco já alocado.
free()	Libera a memória previamente alocada.

📘 Conclusão
Tipo	Características	Vantagens	Limitações
Estática	Tamanho fixo e posições contíguas	Acesso rápido por índice	Não redimensionável
Dinâmica	Usa ponteiros e cresce conforme necessário	Flexível e eficiente no uso de memória	Mais complexa de implementar

📚 Listas Encadeadas em C

As listas encadeadas são estruturas de dados dinâmicas compostas por nós (structs), onde cada nó armazena um valor (dado) e um ponteiro que indica o próximo elemento da lista.
Elas permitem inserir e remover elementos de forma flexível, diferente dos vetores, que têm tamanho fixo.

🥚 Analogia simples

Pense em uma caça aos ovos de Páscoa 🐣:
Cada ovo está em um lugar diferente (cozinha, quarto, sala...), mas você precisa de uma pista (ponteiro) que te leve de um ovo ao próximo.
Assim funciona uma lista encadeada — cada elemento sabe onde está o próximo.

🧩 Estrutura básica de um nó
struct No {
    int dado;              // Onde guardamos a informação
    struct No* proximo;    // A seta que aponta para o próximo nó
};

➕ Inserindo em uma posição específica

Para inserir um novo elemento em uma posição específica da lista, você precisa:

Criar um novo nó.

Percorrer a lista até a posição desejada.

Ajustar os ponteiros para “encaixar” o novo nó na posição certa.

🔗 Tipos de listas encadeadas
1. Lista Encadeada Simples

Cada nó aponta apenas para o próximo elemento da lista.

struct No {
    int dado;
    struct No* proximo;
};

2. Lista Duplamente Encadeada

Cada nó aponta tanto para o próximo quanto para o anterior, permitindo percorrer a lista nos dois sentidos.

struct No {
    int dado;
    struct No* proximo;
    struct No* anterior;
};

3. Lista Circular Simples

O último nó aponta de volta para o primeiro, formando um ciclo.

struct No {
    int dado;
    struct No* proximo; // o último aponta para o primeiro
};

4. Lista Circular Duplamente Encadeada

Cada nó aponta para o próximo e o anterior, e o último nó aponta para o primeiro (e vice-versa).

struct No {
    int dado;
    struct No* proximo;
    struct No* anterior;
};

💡 Observações

As listas encadeadas são úteis quando há muitas inserções e remoções dinâmicas.

Elas consomem mais memória que um vetor, pois armazenam ponteiros.

São amplamente usadas em pilhas, filas e implementações de árvores.

# 🧠 Operações em Listas Encadeadas (C)

Este material apresenta as principais operações realizadas em uma **lista encadeada simples** em linguagem C: **inserção**, **remoção** e **percorrimento**.

---

## 📦 Estrutura do Nó

Cada nó da lista contém um valor (`dado`) e um ponteiro (`proximo`) que aponta para o próximo elemento.

```c
struct No {
    int dado;
    struct No* proximo;
};
```

---

## ➕ Inserção no Início da Lista

A função abaixo insere um novo elemento **no início** da lista encadeada.

```c
void inserirNoInicio(struct No** inicio, int valor) {
    struct No* novo = (struct No*) malloc(sizeof(struct No));
    novo->dado = valor;
    novo->proximo = *inicio;
    *inicio = novo;
}
```

🧩 **Explicação resumida:**  
1. Aloca memória para o novo nó.  
2. Define o valor (`dado`) e faz o novo nó apontar para o antigo início.  
3. Atualiza o ponteiro de início para o novo nó.  

---

## ❌ Remoção do Início da Lista

A função remove o **primeiro elemento** da lista, liberando a memória alocada.

```c
void removerDoInicio(struct No** inicio) {
    if (*inicio != NULL) {
        struct No* temp = *inicio;
        *inicio = (*inicio)->proximo;
        free(temp);
    }
}
```

🧩 **Explicação resumida:**  
1. Verifica se a lista não está vazia.  
2. Armazena o ponteiro do primeiro nó em `temp`.  
3. Move o ponteiro `inicio` para o próximo nó.  
4. Libera a memória do nó removido.  

---

## 🔁 Percorrer e Listar os Elementos

A função percorre toda a lista, exibindo os valores armazenados em cada nó.

```c
void listar(struct No* inicio) {
    struct No* atual = inicio;
    while (atual != NULL) {
        printf("%d\n", atual->dado);
        atual = atual->proximo;
    }
}
```

🧩 **Explicação resumida:**  
Percorre a lista do início até o final, imprimindo cada elemento até encontrar `NULL`.

---

## 🧩 Exemplo de Uso

```c
#include <stdio.h>
#include <stdlib.h>

struct No {
    int dado;
    struct No* proximo;
};

void inserirNoInicio(struct No** inicio, int valor);
void removerDoInicio(struct No** inicio);
void listar(struct No* inicio);

int main() {
    struct No* inicio = NULL;

    inserirNoInicio(&inicio, 10);
    inserirNoInicio(&inicio, 20);
    inserirNoInicio(&inicio, 30);

    printf("Lista atual:\n");
    listar(inicio);

    removerDoInicio(&inicio);
    printf("\nApós remover o primeiro elemento:\n");
    listar(inicio);

    return 0;
}
```

---

## 🧾 Resultado Esperado

```
Lista atual:
30
20
10

Após remover o primeiro elemento:
20
10
```

---

## 🧰 Conceitos Envolvidos

- Ponteiros e alocação dinâmica (`malloc` e `free`)  
- Estruturas (`struct`)  
- Passagem por referência (`**inicio`)  
- Manipulação de listas encadeadas  

---

📘 **Autor:** Matheus Leite  
💡 **Tema:** Estruturas de Dados – Listas Encadeadas  

# Busca Linear em C

A **busca linear** é um algoritmo utilizado para procurar um item em uma lista ou vetor, verificando cada elemento sequencialmente até encontrar o valor desejado.

---

## Exemplos Práticos

### 1. Busca Linear em Vetor

```c
int buscaLinear(int lista[], int tamanho, int valor) {
    for (int i = 0; i < tamanho; i++) {
        if (lista[i] == valor) {
            return i; // Retorna o índice onde encontrou o valor
        }
    }
    return -1; // Retorna -1 se não encontrou
}
```

### 2. Busca Linear em Lista Encadeada

```c
struct No {
    int dado;
    struct No* proximo;
};

int buscaLinearLista(struct No* inicio, int valor) {
    int pos = 0;
    struct No* atual = inicio;
    while (atual != NULL) {
        if (atual->dado == valor) {
            return pos; // Retorna a posição onde encontrou
        }
        atual = atual->proximo;
        pos++;
    }
    return -1; // Retorna -1 se não encontrou
}
```

---

## Vantagens e Desvantagens

**Vantagem:**

* Simples de implementar e entender.

**Desvantagem:**

* Não é eficiente para listas grandes, pois precisa percorrer todos os elementos no pior caso.


