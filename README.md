# Laboratório de Redes de Computadores — Packet Tracer e Camada de Enlace

Projeto acadêmico desenvolvido para a disciplina de **Laboratório de Redes de Computadores**, com o objetivo de observar na prática o funcionamento da **Camada de Enlace**, utilizando o **Cisco Packet Tracer**.

A atividade consistiu na criação e simulação de duas redes locais: uma utilizando **Hub** e outra utilizando **Switch**, permitindo comparar a forma como esses dispositivos encaminham os dados.

## Objetivos

Os principais objetivos da atividade foram:

- Familiarizar-se com a interface do Cisco Packet Tracer.
- Construir topologias de rede simples.
- Adicionar e conectar computadores utilizando cabos de rede.
- Configurar endereços IP estáticos.
- Comparar o funcionamento de Hub e Switch.
- Observar o comportamento dos endereços MAC.
- Utilizar o modo de simulação do Packet Tracer para acompanhar o fluxo dos pacotes na rede.

## Ferramentas utilizadas

- Cisco Packet Tracer
- PC-PT
- Hub-PT
- Switch Cisco 2960
- Cabos Copper Straight-Through
- CLI do Switch
- Modo Simulation do Packet Tracer

## Cenário 1 — Rede com Hub

No primeiro cenário foi criada uma rede contendo:

- 1 Hub-PT
- 4 computadores PC-PT
- 4 conexões utilizando cabo direto

Os computadores foram configurados da seguinte forma:

| Estação | Endereço IP | Máscara |
|---|---|---|
| PC0 | 192.168.1.1 | 255.255.255.0 |
| PC1 | 192.168.1.2 | 255.255.255.0 |
| PC2 | 192.168.1.3 | 255.255.255.0 |
| PC3 | 192.168.1.4 | 255.255.255.0 |

Após a configuração, foi utilizado o modo **Simulation** para enviar um pacote PDU do **PC0 para o PC2**.

Durante a simulação foi possível observar que o Hub replica o pacote recebido para todos os computadores conectados, mesmo quando apenas um deles é o destino da comunicação.

## Cenário 2 — Rede com Switch

No segundo cenário foi criada uma nova rede contendo:

- 1 Switch Cisco 2960
- 4 computadores PC-PT
- 4 conexões utilizando cabo direto

A configuração utilizada foi:

| Estação | Endereço IP | Máscara |
|---|---|---|
| PC4 | 192.168.10.1 | 255.255.255.0 |
| PC5 | 192.168.10.2 | 255.255.255.0 |
| PC6 | 192.168.10.3 | 255.255.255.0 |
| PC7 | 192.168.10.4 | 255.255.255.0 |

Foi realizada uma comunicação entre o **PC4 e o PC6** para observar o comportamento do Switch e sua tabela de endereços MAC.

## Tabela MAC

A CLI do Switch foi utilizada para visualizar sua tabela MAC.

O comando utilizado foi:

~~~bash
show mac-address-table
~~~

Esse comando permite visualizar os endereços MAC aprendidos pelo Switch e as portas associadas a eles.

Durante a atividade também foi utilizado o comando:

~~~bash
clear mac-address-table dynamic
~~~

O objetivo dessa etapa foi apagar as entradas dinâmicas da tabela MAC do Switch e observar novamente o comportamento do encaminhamento dos quadros.

Após novas comunicações entre os computadores, a tabela MAC foi consultada novamente para observar as entradas aprendidas pelo Switch.

## ARP e ICMP

Durante a primeira comunicação entre PC4 e PC6, foi observado o processo de resolução do endereço MAC utilizando **ARP**.

Como os computadores ainda não haviam se comunicado, o PC4 precisava descobrir o endereço MAC do PC6. Para isso, foi utilizado um **ARP Request em broadcast**.

Depois que o Switch aprendeu as portas relacionadas aos dispositivos, os pacotes ICMP puderam ser encaminhados diretamente para o destino.

## Hub x Switch

A principal diferença observada durante as simulações foi a forma como cada dispositivo encaminha os dados.

O **Hub** envia o pacote para todos os dispositivos conectados, mesmo quando apenas um computador é o destino.

O **Switch**, por outro lado, aprende os endereços MAC dos dispositivos conectados e identifica em qual porta cada equipamento está localizado. Dessa forma, após aprender essas informações, consegue encaminhar os dados diretamente para o dispositivo correto.

Além disso, no Hub todos os dispositivos compartilham o mesmo domínio de colisão, enquanto no Switch cada porta forma um domínio separado.

## Principais conceitos trabalhados

Durante a atividade foram trabalhados conceitos como:

- Camada de Enlace
- Endereço MAC
- Endereçamento IPv4
- Máscara de rede
- Hub
- Switch
- Domínio de colisão
- Tabela MAC
- ARP
- ICMP
- Broadcast
- Encaminhamento de quadros
- Simulação de tráfego de rede