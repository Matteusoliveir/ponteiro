#include <stdio.h>
#include <stdlib.h> // Para malloc

// Definição da estrutura do nó
typedef struct lista {
    int dado;
    struct lista *link;
} no;

// Função para criar a lista
no *crialista(int n) {
    no *ini, *p, *ult;
    int valor;
    ini = ult = NULL;

    for (int i = 1; i <= n; i++) {
        printf("\nDigite o valor %d da lista: ", i);
        scanf("%d", &valor);

        p = (no*) malloc(sizeof(no));
        if (p == NULL) {
            printf("Erro de alocação de memória!\n");
            return ini;
        }

        p->dado = valor;
        p->link = NULL;

        if (ult != NULL)
            ult->link = p;
        else
            ini = p;

        ult = p;
    }

    return ini;
}

// Função para escrever a lista
void escrevelista(no *p) {
    printf("\nConteúdo da lista:\n");
    while (p != NULL) {
        printf("%d -> ", p->dado);
        p = p->link;
    }
    printf("NULL\n");
}

int main() {
    no *primeira;
    int n;

    printf("Criando uma lista encadeada\n");

    do {
        printf("Entre com o número de nós: ");
        scanf("%d", &n);
    } while (n < 0);

    primeira = crialista(n);

    if (primeira != NULL)
        escrevelista(primeira);
    else
        printf("Lista vazia ou erro na criação.\n");

    return 0;
}
