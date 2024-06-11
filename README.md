
![icn01 (1)](https://github.com/drsmarcella/focusOnStudy/assets/135395043/d136985e-07c0-4b06-a1da-7c2086edf76c) ![logo](https://github.com/drsmarcella/focusOnStudy/assets/135395043/1c361e76-87a1-4cb0-9b23-0718171d9955)






#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>
#include <unistd.h>

// Função para verificar o código de desbloqueio
int verificarCodigo(char* codigo) {
    const char* codigoCorreto = "1234"; // Código de bloqueio
    return strcmp(codigo, codigoCorreto) == 0;
}

// Função para bloquear a tela
void bloquearTela(int tempo) {
    printf("Sistema bloqueado por %d horas. Bons estudos e mantenha o foco!\n", tempo);
    sleep(tempo); // Simula o tempo de bloqueio
    printf("Tempo de estudo terminou.\n");
}

// Função para abrir aplicativo de emergência
void acionarEmergencia() {
    printf("Emergência acionada! Abrindo aplicativo...\n");
    // Simula a abertura de um aplicativo (substitua pelo comando apropriado para o seu SO)
    // No Linux, poderia ser: system("xdg-open <caminho_do_aplicativo>");
    // No Windows, poderia ser: system("start <caminho_do_aplicativo>");
    // No MacOS, poderia ser: system("open <caminho_do_aplicativo>");
    system("Whatsapp"); // Exemplo: abre o aplicativo do Whatsapp
    printf("Aplicativo aberto. Bloqueando novamente em 60 segundos...\n");
    sleep(10); // Dá um tempo antes de re-bloquear
    printf("Re-bloqueando o sistema.\n");
}

// Função principal
int main() {
    int tempoEstudo;
    char codigo[10];
    char emergencia[10];

    printf("Digite o tempo (em horas) que deseja estudar: ");
    scanf("%d", &tempoEstudo);

    printf("Digite o código de bloqueio: ");
    scanf("%s", codigo);

    if (verificarCodigo(codigo)) {
        bloquearTela(tempoEstudo);
    } else {
        printf("Código incorreto. Programa encerrado.\n");
        return 1;
    }

    printf("Digite o código de desbloqueio: ");
    scanf("%s", codigo);

    if (verificarCodigo(codigo)) {
        printf("Sistema desbloqueado. Bom trabalho!\n");
    } else {
        printf("Código incorreto.\n");
        printf("Digite 'emergencia' para acionar o aplicativo de emergência ou qualquer outra coisa para encerrar: ");
        scanf("%s", emergencia);

        if (strcmp(emergencia, "emergencia") == 0) {
            acionarEmergencia();
            bloquearTela(tempoEstudo);
        } else {
            printf("Programa encerrado.\n");
        }
    }

    return 0;
}
