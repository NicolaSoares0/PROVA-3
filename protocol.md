Descrição Geral
Este protocolo define a comunicação entre o servidor centralizado e os clientes filósofos no sistema do Jantar dos Filósofos Distribuído. Ele utiliza mensagens de texto simples trocadas através de sockets. O servidor gerencia os recursos compartilhados ("garfos"), enquanto os clientes alternam entre os estados de pensar e comer.

Regras Gerais
IDs Únicos: O servidor garante IDs únicos para cada cliente.
Sincronização: O cliente deve aguardar respostas do servidor antes de enviar novas mensagens.
Mensagens Inválidas: Mensagens desconhecidas resultam em uma resposta ERROR UNKNOWN_COMMAND.
Garfos Limitados: O servidor só concede recursos (dois garfos) se disponíveis.

1. Conexão Inicial
Cliente → Servidor

HELLO
O cliente solicita a conexão inicial com o servidor.
Servidor → Cliente

HI <ID>
O servidor responde com um ID único atribuído ao cliente.
ID: Número inteiro que identifica o cliente.

2. Reconexão
Cliente → Servidor

RECONNECT <ID>
O cliente tenta se reconectar ao servidor informando seu ID.
Servidor → Cliente

RECONNECTED <ID>
O servidor confirma a reconexão e reconhece o ID.
Ou, em caso de falha:

ERROR UNKNOWN_ID

3. Registro de Pensamento
Cliente → Servidor

THINKING <ID>
O cliente informa ao servidor que está no estado de pensar.
Servidor → Cliente


THINK_OK
O servidor confirma o registro do estado de pensamento.

4. Solicitação de Recursos (Garfos)
Cliente → Servidor

REQUEST
O cliente solicita dois recursos (garfos) para entrar no estado de comer.
Servidor → Cliente

GRANTED
O servidor confirma a concessão dos recursos.
Ou, caso não haja recursos disponíveis:

DENIED

5. Devolução de Recursos
Cliente → Servidor

RETURN <ID>
O cliente informa ao servidor que terminou de comer e devolve os recursos.
Servidor → Cliente

RETURN_OK
O servidor confirma que os recursos foram liberados com sucesso.

6. Mensagens de Erro
Caso o servidor receba uma mensagem inválida, ele responde com:

plaintext
Copiar código
ERROR UNKNOWN_COMMAND

Considerações Finais
Este protocolo simples e eficiente garante a coordenação entre clientes (filósofos) e o servidor, assegurando a sincronização do acesso aos recursos compartilhados.
