# Arduino-DoorLock


O projeto apresentado no presente repositório se trata de um sistema de controle de acesso físico utilizando o microcontrolador Arduino. Dessa forma, o protótipo final simula o funcionamento de um mecanismo para abertura de portas de forma eletrônica, controlada via Cartão RFID e WiFi, movimentando um Servo Motor caso o acesso seja bem-sucedido.

Com o objetivo de analisar e evidenciar os riscos encontrados em implementações inseguras de redes e dispositivos IoT, demonstram-se, nesse projeto, testes de segurança no protótipo desenvolvido, simulando ataques reais de forma a exemplificar e
aproximar da realidade os ataques cibernéticos que ocorrem recorrentemente, baseando-os, principalmente, no relatório da “OWASP Top 10 IoT”, de 2018.


## Tabela de Conteúdos
* [Sobre](#arduino-doorlock)
* [Tabela de Conteúdos](#tabela-de-conteudos)
* [Pré-Requisitos](#pre-requisitos)
* [Modo de Uso](#modo-de-uso)
* [Testes de Invasão](#testes-de-invasao)
* [Autores](#autores)

## Pré-Requisitos

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
