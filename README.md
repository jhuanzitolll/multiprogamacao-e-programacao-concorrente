
# multiprogamacao-e-programacao-concorrente
texto explicando os conceitos

## Sistemas de multiprogramação 
Um conceito fundamental em sistemas operacionais é o conceito de processo. Um processo é basicamente um programa em execução. Ele consiste de um programa executável, os seus dados e pilha, o seu stack pointer e registradores, enfim todas as informações necessárias para executar o programa. 
Periodicamente o sistema operacional decide se a execução de um processo deve ser interrompida e a execução de um outro processo deve ser iniciada--pela razão do primeiro já ter tido mais do que a sua 'fatia' de tempo de CPU. Em um sistema de multiprogramação a CPU fica se alternando entre a execução de vários processos, cada um por dezenas ou centenas de milisegundos. 

Um processo pode estar em um dos seguintes estados: 
1. Running: usando a CPU naquele instante; 
2. Ready: pronto para ser executado, temporariamente parado para que outro processo possa ser executado; e 
3. Blocked: impossibilitado de ser executado até que algum evento externo ocorra.

Em um sistema de multiprogramação temos frequentemente a situação onde vários processos estão prontos para serem executados. Quando mais de um processo está ready, o sistema operacional deve decider qual processo deve ser executado primeiro. A parte do sistema operacional que toma esta decisão é chamada de scheduler, e o algoritmo que é usado é chamado de scheduler algorithm. A cada interrupçao do relógio o sistema operacional toma o controle e decide se o processo que está sendo executado deve continuar a ser executado ou deve ser suspenso para que outro processo passe a ser executado. A estratégia que permite que um processo que está sendo executado seja suspenso temporariamente é chamada de preemptive schedule. 
Existem scheduling algoritms que assumem que todos os processos são iguais. Entretanto, existem muitas pessoas que possuem e administram centros de computação que discordam disto. Por exemplo, em um centro de computação de uma universidade pode ser dada a mais alta prioridade aos processos de diretores, depois aos de professores, depois aos de secretarias, depois aos de porteiros, ...e finalmente aos de alunos. Isto é chamado de um priority schedule (alguns podem chamar isto de injustiça). 
Para evitar que processos que têm alta prioridade fiquem sendo executados indefinidamente o scheduler pode baixar a prioridade do processo que esta sendo executado a cada interrupção do relógio. 
Alguns priority schedulers fazem uso de classes de prioridade. Os processos na classe de prioridade mais baixa podem ser executados sem serem suspensos por no máximo uma QUANTA (uma quantidade de tempo de CPU). Processos na próxima classe de prioridade pode ser executado por no máximo duas QUANTAS, e assim por diante. Sempre que um processo usa toda as QUANTAS alocadas para ele este processo é rebaixado de classe. 
Quando um processo deseja imprimir um arquivo, ele coloca o nome do arquivo em um diretório especial chamado de spooler directory. Um outro processo, o printer daemon, periodicamente verifica se existe algum arquivo a ser impresso, se existir ele imprime o arquivo e remove o nome do arquivo do diretório spooler. 
