# exercPipe
Primeiro houve a importação das bibliotecas que irão ser usadas, definiu a quantidade de mensagens para dois.
Logo no inicio do MAIN foram definidas as variaves. A variavel pipeFileDescriptors é justamente para indicar o 0 (zero) para ler e 1 (um) para escrever. 
a Variavel returnStatus vai ser usada para identificar se o retorno vai ser -1 (em caso de erro)
as variaves char [QTD_MESSAGES][20] = {"Maria", "Joao andou a noite"}; vai definir a primeira frase MARIA e a segunda como JOAO ANDOU A NOITE
char readMessages[20]; vai definir a função de leitura
memset vai definir a memoria que irá ser reservada para o uso

o returnStatus = pipe(pipeFileDescriptors); vai ser usado para a confirmação se o correu tudo bem com a função pipe

    if (returnStatus == -1) {
        printf("Error when create pipe\n");
        return 1;
    }
se aconteceu algum erro ele retorna -1 e consequentemente o fim do programa com o 1

agora vem a função principal do programa que vai ocorrer o uso do pipe

    for (int i = 0; i < QTD_MESSAGES; i++) {
        printf("Writing Message %d is %s\n", i, writeMessages[i]);
        write(pipeFileDescriptors[1], writeMessages[i], sizeof(char) * 20);
        read(pipeFileDescriptors[0], readMessages, sizeof(char) * 20);
        printf("Reading Message %d is %s\n", i, readMessages);
    }
   
no For ele só está definmindo que ocorrerá duas vezes que é o tamanho da QTD_MESSAGES.
ele mostra ao usuario que a mesagem esta escrita, depois ele faz o write para escrever e logo usa o pipe para transmitir essa escrita para variavel writeMessages e ja reserva o valor de char*20 que é o numero de caracteres pedidos logo no inicio. Depois com o Read para ler a mensagem transimitda pelo pipe e depois faz o print. Repete esse processo para a frase 2
