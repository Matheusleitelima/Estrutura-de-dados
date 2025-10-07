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
