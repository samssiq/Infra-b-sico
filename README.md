# Infraestrutura

*Conceitos básicos*

## Máquina Virtual (VM)

O que é uma máquina virtual?

É um ambiente virtual que possui componentes próprios (CPU, memória, interface de rede). Este sistema é criado a partir de um hardware físico - o host - possui seus recursos separados (e organizados) da máquina física por um hipervisor. A máquina virtual hospedada num host é chamada de guest. 

Exemplos de VMs: Softwares que permitem o uso de diferentes SOs numa única máquina.

Como elas funcionam?

Através da tecnologia de virtualização, que possibilita o gerenciamento dos recursos de hardware para cada ambiente virtual por meio do hipervisor.

Tipos de hipervisores

- **Tipo 1:**  Chamado de bare-metal, é um servidor físico dedicado a um único guest e o sistema operacional utilizado é instalado diretamente no servidor, sem necessidade de hipervisores ou softwares intermediários - eliminando a camada de sotftware entre o hardware e o SO.
- ****************Tipo 2:**************** Chamado de host. Um exemplo de host bastante conhecido é o Oracle VirtualBox.

Benefícios das máquinas virtuais

As máquinas virtuais permitem o uso de diversos servidores virtuais numa única máquina física, o que possibilita a otimização do uso do hardware. Com menor necessidade de utilização de recursos físicos, economiza-se energia, manutenção, espaço e afins.

As VMs são isolodas do restante do sistema e não inteferem no host. Além disso, dispões de mais opções de recuperações de desastres e, pelo seu isolamento característico, são bons espaços de testes. 

## **Virtualização**

O que é virtualização?

Tecnologia que permite, a partir de um uma única máquina (hardware), a criação de vários ambientes simulados, criando as chamadas máquinas virtuais (VMs).

*Hipervisor:* Software que possibilita a criação de outros ambientes simulados.

*Host:* Hardware físico no qual o hipervisor está instalado.

*Guest:* Máquina Virtual que utliza os recursos físicos do host.

Benefícios da virtualização

Redução de custos - diminuição do uso de hardwares utilizados, logo há economia de energia e manutenção;

Melhor gerenciamento de recursos;

Interoperabilidade entre fabricantes - com máquinas virtuais, é possível configurar todo o ambiente p/ atender às necessidades do fabricante, eliminando a necessidade de comprar um servidor físico para cada atividade distinta.

## **Máquina Virtual baseada em Kernel (KVM)**

O que é uma KVM?

É uma tecnologia de virtualização open source com base no Linux, que permite a transformação deste SO num hipervisor e faz com que o hardware host seja capaz de executar diversos ambientes virtuais isolados (VMs).

A KVM já faz parte do código do Linux, pois é parte dele. Assim, há um aproveitamento de todas as funcionalidades existentes.

Como a KVM funciona?

Ela funciona a partir da conversão do Linux em hipervisor tipo 1 (bare-metal ou nativo) . 

**Dúvida: Hipervisores de tipo 1 trabalham bastante com o hardware dedicado àquelas funcionalidades. Dessa forma, se eu fizer um boot de Linux num computador que possuía outro SO previamente instalado, a KVM irá funcionar?*

Como implementar a KVM?

O linux a ser executado deve ser uma versão pós 2007 e deve ser intalada num hardware X86 que tenha recursos de virtualização.

Vantagens da infraestrutura virtual da KVM

- Acesso ao código fonte do hipervisor, permitindo modificações, atualizações e aprimoramento do código;
- Segurança: as VMs são isoladas uma das outras, além da KVM contar com o Security-Enhanced Linus (SELinux) e virtualizção segura (sVirt), aprimorando a proteção das VMs
- Gerenciamento de Memória: Permite a troca da memória da VM, aprimorada e compartilhada/aprimorada por um arquivo de disco. Todas estas funcionalidades são herança do gerenciamento de memória do próprio Linux. Dúvida: o que significa isso? “*****acesso não uniforme à memória e a mesclagem da mesma página do kernel.”*****
- Migração ao vivo: permite mover uma guest em execução de uma host para a outra sem interromper os precessos que estão sendo realizados.
- Desempenho e escalabilidade: permite a flexibilização do desempenho para atender demandas aumentadas caso seja necessário.
- Agendamento e controle de recursos: Não entendi o que este tópico quis dizer
- Gerenciamento: Permite o gerenciamento das VMs manualmente ou através de softwares de gerenciamento de virtualização.

## Containers

O que é um container?

“[…] são pacotes de software leves que contêm todas as dependências necessárias para executar o aplicativo de software contido. Essas dependências incluem coisas como bibliotecas de sistema, pacotes de código externos de terceiros e outros aplicativos de nível de sistema operacional.’’

Vantagens

Velocidade: Devido ao seu tamanho reduzido e sua leveza, containers podem ser modificados de maneira mais rápida.

Robustez: Devido à quantidade de containers pré-fabricados, é possível localizar o que se quer usar na hora da execução sem a necessidade de desenvolver antes.

Desvantagens

Os containers não são tão isolados quanto as máquinas virtuais, assim, uma aplicação em um container X pode afetar outros containers ou o restante do hardware. Além disso, alguns containers pré-fabricados podem ter imagens com um nível de segurança fraco.

## Diferença entre containers e VMs

Uma das principais diferenças entre VMs e containers é o tamanho. Containers são mais leves que VMs, pois possuem apenas as bibliotecas necessárias para rodar uma aplicação enquanto VMs possuem toda a estrutura de outro sistema operacional. Assim, devido à leveza dos containers, entende-se que estes necessitam de menos recursos para funcionar.

Além disso, a virtualização dos recursos de uma VM é diferente da virtualização dos conteiners. As VMs virtualizam todas as camadas de uma máquina, incluindo seu hardware. Enquanto isso, “[…] containers virtualizam apenas camadas de software acima do nivel do sistema operacional.”

[Contêineres vs. máquinas virtuais | Atlassian](https://www.atlassian.com/br/microservices/cloud-computing/containers-vs-vms)