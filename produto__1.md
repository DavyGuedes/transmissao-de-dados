# Modelo de Arquitetura de Camadas

> Transmissão de Dados
>
>Professor De. Emanuel B. Rodrigues

## Equipe

- Marcos Davy
- Wesley Carneiro
- Matthews Jones
- Marcos Martin
- Matheus Guimarães

## Introdução

A Internet é  uma rede que interconecta  milhões de dispositivos computacionais ao redor do mundo. Não há  muito tempo, esses dispositivos eram principalmente computadores de mesa, estações  de trabalho Linux e os tão falados servidores, surgindo outros tipo no decorrer do tempo, como:

- dispositivos celulares, videogames etc
- e dispositivos não convencionais, como uma lâmpada elétrica, cortinas inteligentes e outros aparelhos conectados a rede no contexto da __Internet das Coisas__

Esses dispositivos, também chamado de _hosts_ ou sistemas finais, são conectados entre si por enlaces (links) de comunicação e comutadores de __pacotes__.

Quando um host possui dados para serem transmitidos a outro sistema final, o sistema emissor segmente esses dados e adiciona _bytes_ de cabeçalho a cada segmento. Já usando o jargão de rede de computadores, tais pacotes, são enviados através da rede ao sistema final de destino, onde são reagregados aos dados originais.

Um comutador de pacotes encaminha o pacote que está chegando em um de seus enlaces de comunicação de entrada para um de seus enlaces de comunicação de saída. Dos diversos tipos de comutadores de pacotes, dois recebem destaque na Internet de hoje:
    - os roteadores
    - e os comutadores de camada (ou _switches_)

Esses dois tipos de comutadores encaminham pacotes a seus destinos finais.

> As redes comutadas por pacotes (que transportam pacotes) são, de muitas maneiras, semelhantes às redes de transporte de rodovias, estradas e cruzamentos (que transportam veículos).

## O que é um Protocolo?

> Uma analogia humana

Em uma comunicação humana, temos:

- emissor: aquele que transmite a mensagem, falada, escrita ou gestual
- receptor: aquele que recebe a mensagem

__Exemplos:__

- conversações em telefones
- conversas com outras pessoas
- solicitação de serviços em autarquias

__Ideia chave:__

- envio de _mensagens_ 
- _ações_ quando a mensagem é recebida

De modo semelhante, também aplica-se tais conceitos:

- emissor: dispositivo que envia a mensagem
- receptor: dispositivo que decodifica a mensagem enviada pelo transmissor
- mensagem: as informações
- meio físico
- protocolo: conjunto de regras que definem o que, para onde, de onde etc.

> Para que a comunicação entre duas ou mais máquina ocorra, as máquinas devem utilizar o mesmo protocolo

- máquinas envolvidas
- regras para comunicações entre as máquinas
- governam as comunicações na Internet

__Ideia chave:__

- _formato_ da mensagem
- _sequenciamento_ das mensagens
- _ações_

> Protocolo é o conjunto de regras sobre o modo como se dará a comunicação entre as partes envolvidas. Protocolo é a "língua" dos computadores, ou seja, uma espécie de idioma que segue normas e padrões determinados. É através dos protocolos que é possível a comunicação entre um ou mais computadores.[¹](https://pt.wikibooks.org/wiki/Redes_de_computadores/Protocolos_e_servi%C3%A7os_de_rede)



## Modelo _OSI_ (Open System Interconnection Model)

- Define e é usado para entender como um dado é transferido de um computador a outro.
- Cada camada contém um pacote de protocolos.

### Camada de Aplicação:

- Usada pelos aplicativos que usam a internet (ex: Chrome, Firefox, Skype, Outlook), 
- Protocolos servem por exemplo para transferência de arquivos (FTP), navegação web (HTTP/HTTPs), e-mails (SMTP) e terminais virtuais (Telnet).

### Camada de Apresentação: 

- Manipulação dos dados.
- Há uma tradução de uma sequência de números e caracteres em linguagem de máquina. (bits)
- Após a tradução de ASCII para binário (por exemplo) há uma compressão desses dados.
- Após a compressão há a encriptação para proteção dos dados.
- Quando chega ao remetente, acontece a desencriptação.
- Protocolos usados nessa camada: SSL (Secure Socket Layer)

### Camada  de Sessão:

- Presença de _APIs_ (Application Program Interfaces).
- Computador se conecta a um servidor (rede), em que há uma função chamada autenticação que é basicamente a pergunta: quem é você?, que é respondida através de um username e password.
- Após a autenticação, há a autorização, que é o processo usado pelo servidor para acesso de tal arquivo que o computador está querendo acessar.
- É nessa camada que é dado os endereços dos arquivos que estão sendo baixados, por exemplo.
- Após a autorização ocorre o manejo da sessão, que é colocar os arquivos do servidor em seus devidos locais, como por exemplo, uma imagem e um texto em um site.

### Camada de transporte.

- Três estágios: Segmentação, Controle de Fluxo e Controle de Erros.
- Segmentação: 
   - O dado recebido na camada de sessão é dividido em segmentos menores de dados.
   - Cada dado menor contém uma número da porta e um número de sequência.
   - Número da porta redireciona para a aplicação correta.
   - Número de sequência garante a ordem dos dados.
- _Controle de Fluxo_: 
   - Controla o fluxo de quantidade de bits que será transmitida. (XXXX Mbps)
   - Exemplo: um servidor opera a 100 Mbps e um celular a 10 Mbps, ao baixar um arquivo desse servidor pelo celular, ele começa a transmitir o dado a 50 Mbps, o que é maior que o limite do celular. Então, através da camada de transporte do celular ele diz ao servidor a diminui para 10 Mbps.
- _Controle de Erros_:
   - Se algum segmento de dado não chega até o destino, a camada de transporte utiliza um requerimento repetido automático para recuperar esses dados perdidos ou corrompidos.
      - Um grupo de bits chamado checksum é adicionado à cada segmento para descobrir o segmento corrompido.
   - Protocolos usados pela camada: _TCP_ (Transmission Control Protocol) e _UDP_ (User Datagram Protocol), no qual o segundo é mais rápido pois não provê de feedback.
   - Serviços usados pela camada: Connection-oriented Transmission, Connectionless Transmission, que trabalham com os protocolos acima, respectivamente.

### Camada de Rede:

- As  unidades de dados que operam entre rede 1 e rede 2 de uma transmissão de dados é chamado de Pacotes.
- Função da camada: Endereçamento lógico, Determinação de caminhos e Roteamento.
- _Endereçamento Lógico_:
   - Protocolos de rede _IPv4_ & _IPv6_.
   - Tanto o TX quanto o RX tem um endereço de IP próprio.
   - Os pacotes de dados contém os dois IP’s e o segmento de dados.
- Roteamento:
   - Citar exemplo do Facebook 
   - Máscara de rede se une ao IPv4 e IPv6 para completar o recebimento do pacote de dados.
   - _Determinação de Caminhos_:
      - Escolhe o melhor caminho entre os caminhos possíveis 

### Camada de Dados:

- Os pacotes de dados criados na camada de rede são enviados até essa camada.
- Existem dois tipos de endereçamento: lógico e endereçamento físico.
   - Lógico: é realizado na camada de rede.
   - Físico: é realizado na camada de dados.
- O endereçamento físico é o da placa de rede (formato exemplo: 62.34.DF.3A.87.C9) da fabricante.
- Protocolos usados: Ethernet, Wi-Fi, ATM, frame relay.
- Frame é chamado o conjunto dos dois endereçamentos e do segmento de dados junto com sua cauda.
- Um frame é transmitido ao outro computador pelos seguintes meios: cabo de cobre, fibra ótica ou ar.
- Funções da camada: acessar a mídia (cabo, fibra ótica ou ar) por uma técnica chamada framing (com o uso dos frames), controlar como os dados são recebidos da mídia (media access control & error detection).

### Camada Física:
- Os sinais são transmitidos de acordo com o meio:
   - Para cabo de cobre: sinais elétricos.
   - Para fibra ótica: sinais de luz.
   - Para ar: ondas eletromagnéticas.
   
   
| Modelo OSI | Modelo TCP/IP | Modelo Híbrido |
| --- | --- | --- |
| Aplicação | Aplicação | Aplicação |
| Apresentação | | |
| Sessão | | Transporte |
| Transporte | Transporte | Inter-rede |
| Rede | Internet | Host/Rede |
| Enlace de Dados | Interface Física | Enlace de Dados |
| Física | | Física |

## Encapsulamento e Desencapsulamento

### Introdução
Encapsulamento, é processo do qual os dados são passados desde a camada de aplicação até a camada física.

A camada de aplicação fornece os meios para conectividade ponto-a-ponto entre indivíduos na rede humana usando redes de dados.

Quando o computador envia dados, ele viaja através de uma pilha de camadas, cada camada do modelo OSI encapsula os dados adicionando um cabeçalho e às vezes um “resumo” dos dados no próprio dados. Essa empacotamento é chamado de encapsulamento dos dados. 

### Camada de aplicação
Dados de usuários são iniciados na camada de aplicação, no lado de quem envia os dados.
Quando os dados são movidos para a camada abaixo de apresentação, eles são codificados ou comprimidos por um formato padronizado, as vezes até criptografado. Após os dados do usuários serem convertidos por um formato padrão comum, ele é movido para a camada de seção.

### Camada de sessão
Na camada de sessão, identificador de sessão (session ID) é anexado nos dados.
Nesse ponto, todos os dados são apenas um grande bloco de dados.
Agora os dados são passados para a camada de transporte, (mantenha em mente que dados encapsulados são chamados por nomes diferentes no momento que são movidos mais para as camadas mais baixas da pilha de camada)
Esses nomes são os chamados unidades de protocolo de dados (Protocol Data Unit) ou PDU.

### Camada de transporte
Na camada de transporte, os dados são quebrados em diferentes blocos menores, então esse mesmo dado passa a representar um dos muitos blocos de dados maiores. Então cada bloco é adicionado com um cabeçalho, que contém a porto de destino, porto de origem, número sequencial e outras informações.

Combinando tudo, um novo pacote de dados é criado, um novo pacote de dados é chamado Segmento, se o modelo TCP está sendo usado, ou Datagram se UDP é usado.

Um segmento viaja para a próxima camada inferior, a camada de rede, onde um novo cabeçalho com IP é adicionado. 

### Camada de rede
Cabeçalho com IP contém o endereço IP destinatário, o endereço IP fonte e outras informações. Na camada de rede, na camada de rede um novo pacote IP também é criado.

Quando o pacote IP é passado para a camada de vinculação de dados, o processo se repete. Um novo cabeçalho é adicionado, e um resumo dos dados são também adicionados ao final do pacote.

Uma nova unidade de dados do protocolo, ou Frame como é chamado, é construído. O cabeçalho do Frame contém o endereço MAC (media access control address) do destinatário, ou endereço fonte MAC e outras informações de controle. Um resumo dos dados marca o fim do Frame, e também é usado como checagem de erro pacote.

### Camada física
O Frame então é enviado para a camada física, onde é traduzido em um tipo de sinal específico, seja elétrico, ondas de rádio ou luz. Esse Frame então torna-se um tipo de sinal que representa uma série de zeros ou uns, que os números binários, esse é o motivo por qual nas camadas físicas os dados são frequentemente chamados de Bits. O cartão de Interface da Rede ou NIC (Network Interface Card) prepara esses sinais e envia-los em um meio de transmissão, frequentemente o meio de transmissão é a Internet.

Agora, no lado do destinatário, existe processo de Desencapsulação.

### Desencapsulamento
A camada física lê cada um dos Bits e interpretá-los como um Frame, e transfere-o para a camada de conexão de dados, onde tanto o cabeçalho do Frame quanto um resumo são checados, se o endereço MAC é checado e nenhum erro é encontrado, o Frame é descartado e o pacote IP é retirado e entregue para a camada de rede.
Na camada de rede, o endereço IP é examinado e checado, e se o endereço IP coincide, o Segmento é retirado do pacote IP e o endereço IP é retirado, o segmento é então passado para a camada de Transporte.
Na camada de transporte, onde o cabeçalho do segmento é examinado, um número do porta é olhado e o segmento é então movido para a aplicação apropriada pelo número da porta. Nesse ponto, um endereço ID é usado, qualquer descompressão e decodificação no algoritmo é aplicado se for o caso, e criptografia é removida, e o dado é restaurado para a forma original, onde então é apresentado para a camada de aplicação.

### Conclusão
Para finalizar, encapsulamento de dados se trata de um processo de criar e empacotar os dados do usuário com controle da informação, camada por camada. E desencapsulamento de dados se trata de retirar as informações de controle e restaurar os dados originais do usuário.

## Modelo TCP/IP

### Introdução

Primeiro é importante notar que os computadores não precisam estar ligados na mesma rede. Ou seja, o host A pode estar conectado em uma rede 
Wi-fi (através de um protocolo que utilize essa lógica na sua camada de acesso) enquanto o host B está conectado a uma rede que utiliza a lógica
ethernet (cabo de rede). Essas redes são chamadas de **subnetworks**. Esses protocolos na camada de acesso dão a capacidade dos hosts enviarem
dados através da subnetwork para um host na mesma rede ou, no caso do receptor estar conectado em outra subnetwork, para um roteador que irá 
encaminhar esses dados.



O protocolo IP é implementado em todos os end-systems (hosts) e em todos os roteadores. O protocolo TCP, por sua vez, só precisa ser
implementado nos hosts. Isso acontece porque o protocolo IP, na camada de rede, é o responsável por transmitir os dados de um computador 
pro outro, enquanto o protocolo TCP, na camada de transporte, só é responsável por levar os dados da rede para a aplicação e vice-versa. Como os roteadores
não têm aplicações que vão se utilizar dos dados, o protocolo TCP é desnecessário para eles.


**tl;dr**: O que dá a capacidade dos dados poderem atravessar diferentes tipo de conexões (ou seja, de um computador conectado no wi-fi conseguir receber dados de um computador conectado no cabo de rede) é o roteador. IP tem que ser implementado em todos os computadores que os dados passam. TCP apenas no emissor e receptor.


### Operações no modelo TCP/IP
Suponha que um processo que está ligado à porta 3 do host A queira enviar dados para um processo associado à porta 2 do host B.

Primeiro, a aplicação em A envia os dados para o TCP, mandando ele enviar para host B, porta 2. Isso é o salto da camada de aplicação para
a camada de transporte.

Segundo, o protocolo TCP vai enviar os dados para o protocolo IP, pedindo para que ele envie para o host B. Note que ele
não especifica a porta, já que o trabalho do IP é apenas levar até o host B. Salto da camada de transporte para a de internet.

Terceiro, o protocolo IP envia os dados para o protocolo que rege a camada de acesso à rede (ex: wi-fi, ethernet etc), com instruções para os dados serem
levados para um roteador J, a primeira parada no caminho de A até B.

Para emitir esses comandos, cada um dos protocolos, informações de controle tem que ser transmitidas juntos dos dados que estão sendo
enviados. No nosso exemplo, quando o TCP recebe os dados originais da aplicação em A, eles são quebrados em várias partes para 
serem mais manejáveis. Depois, a cada um desses blocos o TCP adiciona informações de controle, chamadas de header. O conjunto de dados + 
header é chamado de **TCP segment**. Alguns exemplos de informações no header são: porta de destino, origem, um numero para facilitar a
ordenação dos blocos de dados, checksum para verificar a existência de erros na transmissão etc. 

Depois, quando os TCP segments chegarem na camada de internet, o protocolo IP irá adicionar o seu próprio header, 
criando o chamado **IP datagram** (não me pergunte porque são nomes diferentes).
Um exemplo de informação nesse header é o endereço do host final (B). 

Por fim, o protocolo da camada de acesso à rede irá adicionar o seu próprio header, criando finalmente o **packet**.

Depois de todos os headers terem sido adicionados aos dados originais, os dados estão finalmente prontos para viajar. Assim, no nosso exemplo
a primeira parada é o roteador J. Nele, o header da camada de acesso à rede vai ser descartado (pois já cumpriu seu papel de levar até o roteador J)
e o IP datagram vai ser analisado para saber qual é o próximo passo. Ao analisar o IP datagram, o roteador saberá que tem que mandar o datagram
para o host B. Para fazer isso, o datagram é de novo aumentado com um header de acesso à rede. 

No host B, acontece finalmente o processo reverso. Cada header é retirado, e os bits remanescentes são levados para a camada seguinte, até que
apenas o dado original seja mandado para a aplicação original.

**tl;dr** Os dados são particionados e cada um dos protocolos adiciona infos de controles, chamadas de headers. Os dados viajam para o 
roteador, que examina para onde tem que mandar os dados e troca apenas o header da camada de acesso à rede. Depois, o dado viaja até o 
destino e lá é retirado todos os headers e apenas os dados originais são enviados para a aplicação.

### TCP vs UDP

UDP é um protocolo mais simples da camada de transporte. Ele não garante a entrega, preservação da sequência correta ou proteção contra
duplicação dos dados, com o objetivo de um procedimento enviar dados para outro procedimento com o menor mecanismo de protocolo possível.
Seu header só contém a porta de origem, destino e um checksum de uso opcional para a verificação de erros.


### IPv4 vs IPv6

O protocolo IPv4 foi por décadas a base para o modelo TCP/IP. Seu header é formado de 160 bits. No entanto, em 96 foi padronizado o protocolo
IPv6. O principal motivo para o seu desenvolvimento é a necessidade de mais endereços. O IPv4 usa 32 bits para especificar um endereço. Com o
crescimento explosivo da internet nos últimos anos, esse tamanho de endereço ficou insuficiente. IPv6 usa 128 bits. Além disso, existe outros
fatores como a transmissão de um packet para muitos destinos de uma só vez, a unicidade dos endereços etc.
