#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <locale.h>

main()
{
    setlocale(LC_ALL, "Portuguese");
    char palavra[100], linha[100], resposta = ' ', erros[100], palavra2[100], dica[100];
    int tentativas = 5, cont, tamanho, sair = 0, acerto = 0, erro = 0;
    printf("Digite a palavra a ser descoberta: ");
    gets(palavra);
    tamanho = strlen(palavra);
    printf("\nDigite a dica: ");
    fgets(dica, sizeof(dica), stdin);
    system("cls");
    for(cont = 0; cont!= 6;cont++){
     erros[cont] = ' ';
    }
    for(cont = 0; cont < tamanho; cont++)
    {
        linha[cont] = '_';
    }
    do
    {
        acerto = 0;
               if (sair != tamanho && tentativas != 0)
        {
            printf("A dica é: %s\n", dica);
            printf("Você tem %i tentativas restantes para descobrir a palavra\n", tentativas);
            printf("%s - %i letras \n",linha, tamanho);
            printf("Erros: %s \n", erros);
            printf("Digite uma letra: ");
            scanf(" %c", &resposta);
            for (cont = 0; cont < tamanho; cont++)
            {
                if (tolower(resposta) == tolower(palavra[cont]))
                {
                    acerto = 1;
                    linha[cont] = resposta;
                    sair = sair + 1;
                    cont++;
                }
            }
            if (acerto == 1)
            {
                printf("Você acertou a letra %c\n", resposta);
            }
            else
            {
                erros[erro] = resposta;
                erros[erro + 1] = ' -';
                erro = erro + 2;
                tentativas--;
                printf("Não há a letra %c na palavra\n", resposta);
            }
        }
         system("cls");
    }
    while (sair != tamanho && tentativas != 0);
    if (sair == tamanho)
    {
        printf("Parabéns! Você descobriu a palavra\n");
    }
    else
    {
        printf("Você não conseguiu descobrir a palavra dentro das tentativas estipuladas\n a palavra era %s\n", palavra);
    }
}
