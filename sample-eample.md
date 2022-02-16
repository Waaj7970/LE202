# อธิบายโปรแกรม

# การทดลอง 1

#include <Arduino.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
}

void loop()
{
	cnt++;
	Serial.printf("PATTANI :%d\n",cnt);
	int s = cnt % 5 + 1;
	int d = s * 1000;
	delay(d);
}

เป็นการใช้ไมโครคอนโทรเลอร์สร้างคำสั่งการนับโดยแสดงตัวเลขที่ 1 วินาทีแล้วรันเลขไปเรื่อยๆจะนับใหม่เมื่อกดรีเซ็ต

# การทดลอง 2

#include <Arduino.h>
#include <ESP8266WiFi.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
	WiFi.mode(WIFI_STA);
	WiFi.disconnect();
	delay(100);
	Serial.println("\n\n\n");
}

void loop()
{
	Serial.println("========== เริ่มต้นแสกนหา Wifi ===========");
	int n = WiFi.scanNetworks();
	if(n == 0) {
		Serial.println("NO NETWORK FOUND");
	} else {
		for(int i=0; i<n; i++) {
			Serial.print(i + 1);
			Serial.print(": ");
			Serial.print(WiFi.SSID(i));
			Serial.print(" (");
			Serial.print(WiFi.RSSI(i));
			Serial.println(")");
			Serial.print(WiFi.channel(i));
			delay(10);
		}
	}
	Serial.println("\n\n");
	delay(10 * 1000);
}

เป็นการใช้ไมโครคอนโทรเลอร์แสกนหา wifi ในบริเวณใกล้เคียงเมืื่อกดรีเซ็ตก็จะทำการแสกนซ้ำอีกรอบ

# การทดลอง 3 

#include <Arduino.h>
#include <ESP8266WiFi.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
	pinMode(0, OUTPUT);
	Serial.println("\n\n\n");
}

void loop()
{
	cnt++;
	if(cnt % 2) {
		Serial.println("========== ON ===========");
		digitalWrite(0, HIGH);
	} else {
		Serial.println("========== OFF ===========");
		digitalWrite(0, LOW);
	}
	delay(500);
}

เป็นการใช้คำสั่งารนับแบบแลปแรกแต่เปลี่ยนจากการแสดงตัวเลขเป็นการสั่งเปิดปิดแทนโดยเลขคู่ทำให้ไฟจากไดโอตดับหรือคำสั่งปิด เลขคี่เป็นคำสั่งเปิด ดีเลย์ทุกๆ 0.5 วินาทีเป็นลูปซ้ำไปเรื่อยๆและยังงสามารถกดรีเซ็ตเพื่อให้โปรแกรมเริ่มนับใหม่ได้เหมือนการทดลองที่ 1

# การทดลอง 4

#include <Arduino.h>
#include <ESP8266WiFi.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
	pinMode(0, INPUT);
	pinMode(2, OUTPUT);
	Serial.println("\n\n\n");
}

void loop()
{
	int val = digitalRead(0);
	Serial.printf("======= read %d\n", val);
	if(val==1) {
		digitalWrite(2, LOW);
	} else {
		digitalWrite(2, HIGH);
	}
	delay(100);
}

เป็นการทดลองการเปิดปิดไฟของไดโอตมี input ผ่าน port 0  output ผ่าน port 2 ให้ 0 แสดงค่าเป็น 1 หรือก็คือสัญญาณ OFF แต่ถ้ากดปุ่มจะแสดงค่า ON แล้วนำไปต่อกับเซ็นตรวจจับแสงหากได้รับแสงจะแสดงค่าเป็น 0 คือ OFF หากได้รับแสงแสดงค่า 1 เป็น ON

# การทดลอง 5

#include <ESP8266WiFi.h>
//#include <WiFiClient.h>
#include <ESP8266WebServer.h>

const char* ssid = "HI_BMFWIFI_2.4G";
const char* password = "0819110933";

ESP8266WebServer server(80);

int cnt = 0;

void setup(void){
	Serial.begin(115200);

	WiFi.mode(WIFI_STA);
	WiFi.begin(ssid, password);
	while (WiFi.status() != WL_CONNECTED) {
		delay(500);
		Serial.print(".");
	}
	Serial.print("\n\nIP address: ");
	Serial.println(WiFi.localIP());

	server.onNotFound([]() {
		server.send(404, "text/plain", "Path Not Found");
	});

	/// http://192.0.0.1/ = Hello cnt: ???
	server.on("/", []() {
		cnt++;
		String msg = "Hello cnt: ";
		msg += cnt;
		server.send(200, "text/plain", msg);
	});
	/// http://192.0.0.1/on = Hello cnt: ???
	server.on("/on", []() {
		cnt++;
		String msg = "Switch on ";
		msg += cnt;
		server.send(200, "text/plain", msg);
	});
	/// http://192.0.0.1/off = Switch off: ???
	server.on("/off", []() {
		cnt++;
		String msg = "Hello cnt: ";
		msg += cnt;
		server.send(200, "text/plain", msg);
	});

	server.begin();
	Serial.println("HTTP server started");
}

void loop(void){
  server.handleClient();
}

เป็นการใช้ไมโครคอนโทรเลอร์สร้างเว็บบราวเซอร์ผ่าน wifi โดยต้องใส่ ชื่อ wifi แลละ password เป็นการsetup wifiที่เลือกไว้ และชื่อต่อเว็บเซอเวอร์ที่ได้เตรียมไว้ตัวโปรอกรมจะแสดงคำสั่งท่ได้เตรียมไว้

# การทดลอง  6

#include <ESP8266WiFi.h>
//#include <WiFiClient.h>
#include <ESP8266WebServer.h>

const char* ssid = "MY-ESP8266";
const char* password = "choompol";

IPAddress local_ip(192, 168, 1, 1);
IPAddress gateway(192, 168, 1, 1);
IPAddress subnet(255, 255, 255, 0);

ESP8266WebServer server(80);

int cnt = 0;

void setup(void){
	Serial.begin(115200);

	WiFi.softAP(ssid, password);
	WiFi.softAPConfig(local_ip, gateway, subnet);
	delay(100);

	server.onNotFound([]() {
		server.send(404, "text/plain", "Path Not Found");
	});

	server.on("/", []() {
		cnt++;
		String msg = "Hello cnt: ";
		msg += cnt;
		server.send(200, "text/plain", msg);
	});

	server.begin();
	Serial.println("HTTP server started");
}

void loop(void){
  server.handleClient();
}

เป็นการาสร้าง wifi จากไมโครคอนโทรเลอร์โดยต้องมีกำหนด IP Adressเพื่อให้อุปกรณ์อื่นๆสามารถเชื่อต่อกับไมโครคอนโทรเลอร์ได้
