const int powerPin = A0; // Broche du potentiomètre pour régler la puissance
const int speedPin = A1; // Broche pour capter la vitesse
const int temperaturePin = A2; // Broche pour capter la température

void setup() {
  Serial.begin(9600); // Initialisation de la communication série
}

void loop() {
  int powerValue = analogRead(powerPin); // Lecture de la valeur du potentiomètre
  int speedValue = analogRead(speedPin); // Lecture de la valeur de la vitesse
  int temperatureValue = analogRead(temperaturePin); // Lecture de la valeur de la température

  // Conversion des valeurs analogiques en valeurs réelles
  float power = map(powerValue, 0, 1023, 0, 100); // Conversion de 0-1023 à 0-100%
  float speed = map(speedValue, 0, 1023, 0, 255); // Conversion de 0-1023 à 0-255 (pour la vitesse)
  float temperature = map(temperatureValue, 0, 1023, 0, 100); // Conversion de 0-1023 à 0-100 degrés

  // Affichage des valeurs
  Serial.print("Puissance: ");
  Serial.print(power);
  Serial.println("%");
  
  Serial.print("Vitesse: ");
  Serial.println(speed);
  
  Serial.print("Température: ");
  Serial.print(temperature);
  Serial.println(" degrés");

  delay(1000); // Délai d'une seconde entre chaque lecture
}
