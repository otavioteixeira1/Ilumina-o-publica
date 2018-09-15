# Ilumina-o-publica
acender led com ldr
/* 
 * PROTÓTIPO: SENSOR DE LUZ (LDR) PARA ACIONAMENTO DE LED 
*/
 
// Pode ser necessário alterar o "valor limite de disparo" para encontrar um valor adequado
// para ligar e desligar o LED quando "mover a mão" sobre o fotoresistor (LDR)
int limiteDisparo = 965;
 
// Ligue o LED ao pino digital D4
int led = D4;
/*int led1 = D5;
int led2 = D2;
int led3 = D1;
int led4 = D6;*/

 
// O fotoresistor (LDR) é conectado ao pino analógico A0
int sensor = A0;
 
// Armazena o valor de leitura analógica
int sensorValue = 0;
 
void setup() {
  
  // Define o LED como uma saída
  pinMode(led, OUTPUT);
  /*pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
  pinMode(led4, OUTPUT);*/
  
  // Define o fotoresistor como uma entrada
  pinMode(sensor, INPUT);
  
  // Inicia a comunicação serial com uma taxa de transmissão de 9600 boud rate
  Serial.begin(9600);
}
 
void loop(){
  
  // Lê o valor atual do fotoresistor
  sensorValue = analogRead(sensor);
  
  // Se o valor estiver abaixo de um determinado "limite de disparo", então o LED liga, caso contrário o LED permanece desligado
  
  if (sensorValue < limiteDisparo) {
      digitalWrite(led, LOW);
      delay(50);
      /*digitalWrite(led1,HIGH);
      delay(50);
      digitalWrite(led2,HIGH);
      delay(50);
      digitalWrite(led3,HIGH);
      delay(50);
      digitalWrite(led4,HIGH);
      delay(50);*/
      
  }
  else {
      digitalWrite(led,HIGH);
      delay(50);
      /*digitalWrite(led1, LOW);
      delay(50);
      digitalWrite(led2, LOW);
      delay(50);
      digitalWrite(led3, LOW);
      delay(50);
      digitalWrite(led4, LOW);
      delay(50);*/
  }
  
  // Imprime as leituras atuais no monitor serial da IDE do Arduino
  Serial.print ("Leitura atual do sensor: ");
  Serial.println(sensorValue);
  delay(130);
}
