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

Código Fonte: 

```C++
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2); // Pinos RS, E, D4, D5, D6, D7 do LCD

const int potentiometerPin = A0; // Pino do potenciômetro
const int redLEDPin = 8;        // Pino do LED RGB (vermelho)
const int greenLEDPin = 9;      // Pino do LED RGB (verde)
const int blueLEDPin = 10;      // Pino do LED RGB (azul)

void setup() {
  pinMode(redLEDPin, OUTPUT);
  pinMode(greenLEDPin, OUTPUT);
  pinMode(blueLEDPin, OUTPUT);
  
  lcd.begin(16, 2);
  lcd.setCursor(0, 0); // Define o cursor na primeira linha
  lcd.print("UV Intensity:");
  randomSeed(analogRead(0)); // Inicializa o gerador de números aleatórios
}

void loop() {
  int sensorValue = analogRead(potentiometerPin); // Leitura do potenciômetro
  int uvIntensity = map(sensorValue, 0, 1023, 0, 100); // Mapeia o valor para um intervalo de 0 a 100
  
  lcd.setCursor(0, 1); // Define o cursor na segunda linha
  if (uvIntensity == 0) {
    lcd.print("UV Desligado   ");
    setColor(0, 0, 0); // Desliga o LED RGB
  } else {
    lcd.print(uvIntensity);
    lcd.print("% UV     ");
  
    // Iniciar a análise
    lcd.setCursor(0, 0);
    lcd.print("Analisando...   ");
    delay(5000); // Espera 5 segundos para simular a análise
  
    // Gerar porcentagem aleatória de microplásticos
    int microplasticPercentage = random(5, 95); // Gera um número aleatório entre 5 e 95
  
    // Exibir o resultado da análise
    lcd.setCursor(0, 0);
    lcd.print("Microplastics: ");
    lcd.setCursor(0, 1);
    lcd.print(microplasticPercentage);
    lcd.print("%         ");
  
    // Definir cor do LED RGB baseado na porcentagem
    if (microplasticPercentage == 0) {
      setColor(0, 255, 0); // Verde sólido para 0%
    } else if (microplasticPercentage < 25) {
      setColor(0, 0, 255); // Azul sólido para 1% a 24%
    } else if (microplasticPercentage < 50) {
      setColor(255, 255, 0); // Amarelo sólido para 25% a 49%
    } else if (microplasticPercentage < 75) {
      setColor(255, 0, 0); // Vermelho sólido para 50% a 74%
    } else {
      blinkRed(); // Vermelho piscante para 75% a 95%
    }
  
    delay(5000); // Espera 5 segundos antes da próxima leitura
  }
}

void setColor(int red, int green, int blue) {
  analogWrite(redLEDPin, red);
  analogWrite(greenLEDPin, green);
  analogWrite(blueLEDPin, blue);
}

void blinkRed() {
  for (int i = 0; i < 5; i++) {
    setColor(255, 0, 0); // Vermelho
    delay(200);
    setColor(0, 0, 0); // Desliga
    delay(200);
  }
}
```

Link Tinkercad:

[https://www.tinkercad.com/things/8McWzDCkbBD-stunning-kup-elzing/editel?sharecode=fNOdlG9uXO9SzfSDZnuoSbg2tBs3gJOHCzY2ppiWaOw]

