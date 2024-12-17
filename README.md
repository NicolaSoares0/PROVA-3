Jantar dos Filósofos Distribuído

Este projeto implementa uma solução distribuída para o Problema do Jantar dos Filósofos utilizando Java e as interfaces ServerSocket e Socket. O servidor central gerencia os recursos compartilhados, enquanto os clientes simulam os filósofos que pensam e comem.


Execução do Projeto

Passo 1: Compilar o Código

compile todas as classes do projeto em um terminal com ##javac Cliente.java

Passo 2: Iniciar o Servidor

Inicie o servidor central que gerencia os recursos com  ##java ServidorRecursos

Passo 3: Iniciar os Clientes

Em terminais separados, execute os clientes para simular os filósofos. Use o comando:

java ClienteFilosofo

Cada filosofo se conectará ao servidor, receberá um ID único  alternando entre os estados de pensar e comer
