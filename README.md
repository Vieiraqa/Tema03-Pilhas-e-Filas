#include <stdio.h>

#define MAX 5

int main() {
    char tipos[MAX] = {'T','O','L','I','I'}; // tipos iniciais
    int ids[MAX]  = {0,1,2,3,4};             // IDs iniciais
    int qtd = 5;                             // fila cheia inicialmente
    int nextID = 5;                          // próximo id

    int opcao;

    while (1) {
        printf("\nFila: ");
        for (int i = 0; i < qtd; i++) {
            printf("[%c%d] ", tipos[i], ids[i]);
        }
        for (int i = qtd; i < MAX; i++) {
            printf("[   ] ");
        }
        printf("\n");

        printf("\n1 - Jogar Peça\n");
        printf("2 - Inserir Nova Peça\n");
        printf("0 - Sair\n");
        printf("Escolha: ");
        scanf("%d", &opcao);

        if (opcao == 0) {
            printf("Saindo...\n");
            break;
        }

        if (opcao == 1) {  
            // jogar peça
            if (qtd == 0) {
                printf("Fila vazia! Nada para jogar.\n");
            } else {
                printf("Jogando peça: [%c%d]\n", tipos[0], ids[0]);

                // desloca à esquerda
                for (int i = 0; i < qtd - 1; i++) {
                    tipos[i] = tipos[i+1];
                    ids[i] = ids[i+1];
                }
                qtd--; // diminui a quantidade
            }
        }

        else if (opcao == 2) {
            // inserir nova peça
            if (qtd == MAX) {
                printf("Fila cheia! Nao e possivel inserir.\n");
            } else {
                char novoTipo;
                printf("Digite o tipo da nova peça (I,O,T,L): ");
                scanf(" %c", &novoTipo);

                tipos[qtd] = novoTipo;
                ids[qtd] = nextID++;
                qtd++;

                printf("Peça inserida!\n");
            }
        }

        else {
            printf("Opcao invalida!\n");
        }
    }

    return 0;
}
