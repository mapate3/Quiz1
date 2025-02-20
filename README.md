# Quiz1
Button corresponds to a color. and if you press multiple buttons it will show the color. 
const int GreenLED = 8;
const int BlueLED  = 9;
const int RedLED   = 10;

// Define button pins
const int GreenButton = 4;
const int BlueButton  = 3;
const int RedButton   = 2;

void setup() {
  // Initialize LED pins as outputs
  pinMode(GreenLED, OUTPUT);
  pinMode(BlueLED , OUTPUT);
  pinMode(RedLED  , OUTPUT);  
  
  // Initialize button pins as inputs with internal pull-up resistors
  pinMode(RedButton, INPUT_PULLUP);  
  pinMode(BlueButton, INPUT_PULLUP); 
  pinMode(GreenButton, INPUT_PULLUP);   
}

void loop() {
  boolean GreenIs = !digitalRead(GreenButton); // Button pressed = LOW, so invert logic
  boolean BlueIs  = !digitalRead(BlueButton);
  boolean RedIs   = !digitalRead(RedButton); 
  
  delay(50);
  
  if (GreenIs && BlueIs && RedIs) {
    // All buttons pressed: White (all LEDs on)
    digitalWrite(GreenLED, HIGH);
    digitalWrite(BlueLED, HIGH);
    digitalWrite(RedLED, HIGH);
  } 
  else if (GreenIs && BlueIs) {
    // Green + Blue: Cyan
    digitalWrite(GreenLED, HIGH);
    digitalWrite(BlueLED, HIGH);
    digitalWrite(RedLED, LOW);
  } 
  else if (GreenIs && RedIs) {
    // Green + Red: Yellow
    digitalWrite(GreenLED, HIGH);
    digitalWrite(BlueLED, LOW);
    digitalWrite(RedLED, HIGH);
  } 
  else if (BlueIs && RedIs) {
    // Blue + Red: Magenta
    digitalWrite(GreenLED, LOW);
    digitalWrite(BlueLED, HIGH);
    digitalWrite(RedLED, HIGH);
  } 
  else if (GreenIs) {
    // Only Green
    digitalWrite(GreenLED, HIGH);
    digitalWrite(BlueLED, LOW);
    digitalWrite(RedLED, LOW);
  } 
  else if (BlueIs) {
    // Only Blue
    digitalWrite(GreenLED, LOW);
    digitalWrite(BlueLED, HIGH);
    digitalWrite(RedLED, LOW);
  } 
  else if (RedIs) {
    // Only Red
    digitalWrite(GreenLED, LOW);
    digitalWrite(BlueLED, LOW);
    digitalWrite(RedLED, HIGH);
  } 
  else {
    // No buttons pressed: Turn all LEDs off
    digitalWrite(GreenLED, LOW);
    digitalWrite(BlueLED, LOW);
    digitalWrite(RedLED, LOW);
  }
}
