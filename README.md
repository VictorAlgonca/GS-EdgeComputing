# GS-EdgeComputing

Pedro Henrique Martins Alves dos Santos RM: 558107

Victor de Almeida Gonçalves RM: 558799

Felipe Cerboncini Cordeiro RM: 554909

Projeto: Detecção de Microplásticos na Água com Luz UV

Descrição:

Este projeto utiliza um Arduino Uno, um potenciômetro, um display LCD 16x2 e um LED RGB para simular um sistema de detecção de microplásticos na água. A intensidade
da luz UV é controlada por um potenciômetro, e o display LCD mostra a intensidade da luz UV utilizada e uma porcentagem aleatória de microplásticos detectados. O 
LED RGB muda de cor com base na porcentagem de microplásticos detectados.

Funcionalidades:

- Controle da intensidade da luz UV via potenciômetro;
- Exibição da intensidade da luz UV no display LCD;
- Geração e exibição de uma porcentagem aleatória de microplásticos detectados;
- Indicação visual da quantidade de microplásticos detectados através de um LED RGB.

Itens Utilizados:

- Arduino Uno;
- Potenciômetro;
- Display LCD 16x2;
- LED RGB;
- Resistores;
- Jumpers;
- Protoboard.

Biblioteca: 

- LiquidCrystal.

Montagem:

1. Arduino Uno: Conecte o Arduino Uno à protoboard.

2. Potenciômetro:

- Conecte uma extremidade ao 5V do Arduino;
- Conecte a outra extremidade ao GND do Arduino;
- Conecte o pino central ao pino A0 do Arduino.

3. Display LCD 16x2:
  
- Conecte os pinos VSS e RW ao GND do Arduino;
- Conecte os pinos VDD e A ao 5V do Arduino;
- Conecte o pino VO ao pino central de um potenciômetro;
- Conecte os pinos RS, E, D4, D5, D6 e D7 aos pinos digitais 12, 11, 5, 4, 3 e 2 do Arduino.

4. LED RGB:

- Conecte o cátodo comum ao GND do Arduino;
- Conecte os pinos R, G e B aos pinos digitais 8, 9 e 10 do Arduino, através de resistores de 220 ohms.

Instruções de Uso:

1. Monte o circuito conforme descrito na seção Montagem do Circuito.

2. Faça o upload do código fornecido para o Arduino Uno usando a IDE do Arduino.

3. Gire o potenciômetro para ajustar a intensidade da luz UV. O display LCD exibirá a intensidade em porcentagem.

4. Após 5 segundos, o LCD mostrará uma porcentagem aleatória de microplásticos detectados.

5. O LED RGB mudará de cor de acordo com a porcentagem de microplásticos:

- Verde: 0%;
- Azul: 1% a 24%;
- Amarelo: 25% a 49%;
- Vermelho: 50% a 74%;
- Vermelho Piscante: 75% a 95%.

Código Fonte: C++ 
