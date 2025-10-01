# Uso de Structs e Encapsulamento de Dados em C

## 📌 Struct
- Uma **struct** reúne vários tipos de dados diferentes em uma única estrutura.  
- É útil quando precisamos organizar informações relacionadas.

### Exemplo:
Um **prontuário médico** pode conter: nome, idade e alergia.

```c
struct Prontuario {
    char nome[50];
    int idade;
    char alergia[100];
};
```

---

## 📦 Encapsulamento
- O **encapsulamento** significa "empacotar" esses dados em uma única entidade.  
- Todos os dados ficam organizados e agrupados dentro da struct.

---

## 📝 Sintaxe Geral

```c
struct Nome {
    tipo_de_dado variavel[tamanho];
    int idade;
    float media;
};
```

### Exemplo:
```c
struct Aluno {
    char nome[50];
    int idade;
    float media;
};
```

---

## 🔖 Usando `typedef`
- O `typedef` cria um **apelido** para a struct, facilitando o uso.  

```c
typedef struct {
    char nome[50];
    int idade;
    float media;
} Aluno;
```

Agora podemos declarar diretamente:
```c
Aluno aluno1 = {"João", 20, 8.5};
```

---

## 🎯 Acessando os Dados da Struct

```c
printf("Aluno: %s\n", aluno1.nome);
```

---

## 🖥️ Exemplo Completo

```c
#include <stdio.h>

// Definindo a estrutura do tipo Aluno
typedef struct {
    char nome[50];
    int idade;
    float media;
} Aluno;

int main() {
    // Criando uma variável do tipo Aluno
    Aluno aluno1 = {"João", 20, 8.5};

    // Exibindo os dados do aluno
    printf("Aluno: %s\nIdade: %d\nMédia: %.2f\n", aluno1.nome, aluno1.idade, aluno1.media);

    return 0;
}
```

---

## ✅ Vantagens do uso de structs
- Boa **organização** dos dados.  
- **Menos repetição** de código.  
- Fácil **reutilização**.  
- Permite criar **estruturas complexas**.  
