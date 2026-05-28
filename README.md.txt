#define BUZZER 25
#define CHANNEL 0

int melody[] = {

  659,659,0,659,
  0,523,659,0,
  784,0,0,0,
  392,0,0,0,

  523,0,0,392,
  0,0,330,0,
  0,440,0,494,
  0,466,440,0,

  392,659,784,
  880,0,698,784,
  0,659,0,523,
  587,494,0,0,

  523,0,0,392,
  0,0,330,0,
  0,440,0,494,
  0,466,440,0,

  392,659,784,
  880,0,698,784,
  0,659,0,523,
  587,494,0,0
};

int noteDurations[] = {

  150,150,150,150,
  150,150,150,150,
  300,150,150,300,
  300,150,150,300,

  300,150,150,300,
  300,150,300,150,
  150,300,150,300,
  150,150,300,150,

  200,200,200,
  300,150,200,200,
  150,200,150,200,
  200,300,150,300,

  300,150,150,300,
  300,150,300,150,
  150,300,150,300,
  150,150,300,150,

  200,200,200,
  300,150,200,200,
  150,200,150,200,
  200,300,150,300
};

int sizeMelody = sizeof(melody) / sizeof(int);

void setup() {

  ledcSetup(CHANNEL, 2000, 8);

  ledcAttachPin(BUZZER, CHANNEL);
}

void loop() {

  for (int thisNote = 0; thisNote < sizeMelody; thisNote++) {

    int noteDuration = noteDurations[thisNote];

    ledcWriteTone(CHANNEL, melody[thisNote]);

    delay(noteDuration);

    ledcWriteTone(CHANNEL, 0);

    delay(50);
  }

  delay(5000);
}
