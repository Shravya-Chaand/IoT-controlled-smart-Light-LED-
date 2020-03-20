Components used :
1. LED
2. NodeMCU ESP8266
3. Jumper wires
Adiitional components that can be used to prevent circuit breakage:
1. resisitors
2. relay
 
 DESIGN:::
Hardware :
The only connection required is the LED to your NodeMCU.Connect the positive of LED to a digital pin ,say D3, and negative of LED to GND pin of NodeMCU.
 
Software:
 Create a ThinkSpeak account. Now create a channel and fill a field for LED(in my case BLUE_LED).Within the channel choose API Keys and copy the "Write API keys " and "Read API keys" data and declare them in code as follows:
 unsigned long myChannelNumber = 1021488;//copy the channel number too
const char * myWriteAPIKey = "M633XTNE4JETL9QE";
const char * myReadAPIKey = "YP64HEP8OL9LGRZ6";


 Create an account in IFTTT and then create two applets in it one for turning on LED and the other for turning off the LED.The trigger service used is google assistant and the action is set up by webhooks. While seeting up action we need to give the URL copied from "Write a channel feed" under the API keys section of the ThingSpeak channel created (in my case BLUE_LED field from iot project channel that i created).Give different field values for turning on and turning off LED by editing the field1 value in URL copied as follows.
 https://api.thingspeak.com/update?api_key=M633XTNE4JETL9QE&field1=0   /// field1 = 0 is for turning off LED.
 https://api.thingspeak.com/update?api_key=M633XTNE4JETL9QE&field1=1   /// field1 = 1 is for turning oN LED.
 
 Arduino IDE :
   Install NodeMCU board, Also install ESP8266 and ThingSpeak library in arduino IDE.
  inorder to read the updated data from thingspeak and to control the LED connected to NodeMCU use the following code :
  
 int LED = ThingSpeak.readIntField(myChannelNumber, 1, myReadAPIKey);// to read data from cloud and assign it to variable
  
  after reading and write dtat from cloud to declared variable use the following code to control the LED connected: 
  if(LED==1)
  {
    digitalWrite(BLUE_LED,HIGH);
  }
  else if(LED==0)
  {
    digitalWri
  
