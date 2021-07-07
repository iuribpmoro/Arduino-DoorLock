# Arduino-DoorLock


O projeto apresentado no presente repositório se trata de um sistema de controle de acesso físico utilizando o microcontrolador Arduino. O protótipo final simula o funcionamento de um mecanismo para trancar e destrancar portas de forma eletrônica, controlado via Cartão RFID e WiFi, onde, caso o acesso seja bem-sucedido, um Servo Motor é movimentado liberando a abertura da porta.

A premissa ao simular - o que poderia ser o controle de acesso físico de um ambiente real - é evidenciar, analisar e explorar as possíveis vulnerabilidades que podem ser encontradas em implementações inseguras de redes e dispositivos IoT. Para tanto, neste projeto, são executados testes de segurança que exemplificam de forma semelhante a realidade os ataques cibernéticos mais recorrentes, conforme aponta o relatório da [“OWASP Top 10 IoT”](https://owasp.org/www-pdf-archive/OWASP-IoT-Top-10-2018-final.pdf), de 2018.


## Tabela de Conteúdos
* [Sobre](#arduino-doorlock)
* [Tabela de Conteúdos](#tabela-de-conteúdos)
* [Pré-Requisitos](#pré-requisitos)
* [Modo de Uso](#modo-de-uso)
* [Testes de Invasão](#testes-de-invasão)
* [Autores](#autores)

## Pré-Requisitos
Nesta seção são apresentados todos os pré requisitos necessários para reproduzir o protótipo do [DoorLock](https://github.com/iuribpmoro/Arduino-DoorLock)

### Materiais
Para montagem desse projeto serão necessários os seguintes componentes:
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
A montagem desde projeto segue o sketch de demonstração. Lembrando que o Ethernet Shield deve ser conectado sobre o Arduino.
<details>
  <summary>Clique para visualizar o sketch</summary>
  <img alt="DoorLock Sketch" src="https://github.com/iuribpmoro/Arduino-DoorLock/blob/main/Sketch/door_lock_sketch.png" height="700px">
</details>

### Softwares
Os pré requisitos a nível de software reproduzir a aplicação:
* [Arduino IDE](https://www.arduino.cc/en/software)
* [Biblioteca](https://www.arduino.cc/reference/en/libraries/mfrc522/) (Passo a passo: [Adicionar bibliotecas na IDE do arduino](https://www.robocore.net/tutoriais/adicionando-bibliotecas-na-ide-arduino))
* [Código-fonte do DoorLock](https://github.com/iuribpmoro/Arduino-DoorLock/blob/main/DoorLock/DoorLock.ino)

Por fim, o arduino deve ser conectado via USB com o computador, o código deve ser carregado na placa e o ambiente estará pronto.
Caso desejar, o mesmo poderá ser anexado a uma maquete.

## Modo de Uso

## Testes de Invasão

Primeiramente, demonstra-se o funcionamento de um ataque físico de cópia de conteúdos em tags RFID, por meio da utilização de um
segundo arduino configurado para atingir esse objetivo. Em segundo lugar, exemplifica-se um ataque de força bruta para a quebra
da senha da rede WiFi na qual o dispositivo está conectado, descrevendo os riscos de utilizar senhas fracas e previsíveis.

Por meio da utilização do script [Automap](https://github.com/iuribpmoro/Automap) que realizam o reconhecimento, scanning e enumeração da rede, descobre-se, por fim, como operar a fechadura por meio de requisições web, finalizando o processo de ataque.

### Roteiro dos Ataques


## Autores
### Gabrieli Silva
[![Gmail Badge](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white
)](mailto:iuribpmoro@gmail.com)[![Linkedin Badge](https://img.shields.io/badge/linkedin%20-%230077B5.svg?&style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gabrieli-silva-435627164/)
### Iuri Moro
[![Gmail Badge](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white
)](mailto:iuribpmoro@gmail.com)[![Linkedin Badge](https://img.shields.io/badge/linkedin%20-%230077B5.svg?&style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/iuribpmoro/)
