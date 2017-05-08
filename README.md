# Smart Storage Box library for ESP8266 WiFi chips

## Installation
1. Download as zip
2. Unzip
3. Copy the folder "SmartStorageBox" into arduino-x.x.x/libraries/ (x..x.x stands for version number)
4. restart the Arduino IDE

## Example usage
```
#include <Arduino.h>
#include <ESP8266WiFi.h>
#include <ESP8266WiFiMulti.h>
#include <SmartStorageBox.h>

ESP8266WiFiMulti WiFiMulti;

SmartStorageBox box("Box1", "http://example.com/api/");

void setup() {
    WiFiMulti.addAP("SSID", "password");
}

void loop() {
    if((WiFiMulti.run() == WL_CONNECTED)) {
        box.postWeight(10);
        box.postRFID("E2 46 4B A0");
        box.postActivity();
    }
    delay(1000);
}
```

## Documentation

### SmartStorageBox
Constructor

#### Arguments

type | name | description
 -- | -- | -- | --
String|name|Name of the box you want to send data about
String|host|Host of the Smart Storage API

#### Use
`SmartStorageBox box(String name, String host);`


### postWeight
Method for posting weight to the API

#### Arguments
type | name | description
 -- | -- | -- | --
int|weight|Weight of the content in the box

#### Returns
type | description 
  -- | -- 
bool | If the post to the API server succeeds 

#### Use
`box.postWeight(weight);`


### postRFID
Method for posting RFID to the API

#### Arguments
type | name | description
 -- | -- | -- | --
int|rfid|RFID value as int as scanned by RFID reader

#### Returns
type | description 
  -- | -- 
bool | If the post to the API server succeeds 

#### Use
`box.postRFID(rfid);`


### postActivity
Method for posting activity to the API

#### Arguments
type | name | description
 -- | -- | -- | --

#### Returns
type | description 
  -- | -- 
bool | If the post to the API server succeeds 

#### Use
`box.postActivity();`

