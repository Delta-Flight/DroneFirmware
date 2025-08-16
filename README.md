# ESP-FC Flight Controller
The mini, DIY, Low cost, ESP32 based, high performance flight controller for hobbyists.

## Features
* Espressif targets (ESP32, ESP8266, ESP32-S3, ESP32-S2, ESP32-C3)
* ESC protocols (PWM, Oneshot125/42, Multishot, Brushed, Dshot150/300/600 bidirectional)
* PPM, SBUS and CRSF Receivers
* Builtin ESP-NOW receiver and WiFi configuration [read more...](/docs/wireless.md)
* SPI and I2C gyro modules support (MPU6050, MPU9250, ICM20602, BMI160)
* Flight modes (ACRO, ANGLE, AIRMODE)
* Frames (Quad X)
* Betaflight configuration tool compatible (v10.8-v10.10)
* Configurable Gyro Filters (LPF, Notch, dTerm, RPM)
* Blackbox recording (OpenLog/OpenLager/Flash)
* Up to 4kHz gyro/loop on ESP32 with SPI gyro
* MSP protocol interface
* CLI Interface
* Resorce/Pin mapping
* In flight PID Tuning
* Buzzer
* Lipo voltage monitor
* Failsafe mode

## Requisitos
Hardware:
* ESP32 mini board  ESP8266 Wemos D1 mini or similar
* MPU9250 SPI or MPU6050 I2C gyro (GY-88, GY-91, GY-521 or similar)
* PDB with 5V BEC
* Buzzer and some electronic components (optional).

Software:
* [Betaflight Configurator](https://github.com/betaflight/betaflight-configurator/releases) (v10.8 to v10.10)
* [CH340 Driver](https://sparks.gogo.co.nz/ch340.html)

## Flashing
1. Download and unzip selected firmware from [Releases Page](https://github.com/rtlopez/esp-fc/releases)
2. Visit [ESP Tool Website](https://espressif.github.io/esptool-js/)
3. Clique em "Connect" e escolha a porta do dispositivo
4. Adicione o arquivo de firmware e escolha o "Flash Address" para `0x1000`
5. Clique em "Program"
6. Assim que concluir, reinicie o dispositivo

Note: only ESP32 and ESP8266 can be flashed in this way.

![ESP-FC Flashing](/docs/images/esptool-js-flash-connect.png)

## Setup
After flashing you need to configure few things first:
 1. Configure pinout according to your wiring, especially pin functions, you can find more information in [CLI Reference](/docs/cli.md)
 2. Connect to [Betaflight Configurator](https://github.com/betaflight/betaflight-configurator/releases) and setup to your preferences,
 3. Test motors without propellers
 4. Have fun ;)

> [!NOTE]
> Not all functions displayed in configurator are avalable in firmware. The rule of thumb is if you cannot change specific option in Betaflight Configurator, that means it is not supported. It usually rolls back to previous value after save.

Here are more details about [how to setup](/docs/setup.md).

## Wiring diagrams

[![ESP-FC example wiring diagrams](/docs/images/espfc_wiring_combined.png)](/docs/wiring.md)

## Chips Suportados

 - **ESP32** - recomendado
 - **ESP32-S2** - experimantal
 - **ESP32-S3** - experimantal
 - **ESP32-C3** - experimantal, queda de performance, sem FPU
 - **RP2040** - experimantal, queda de performance, sem FPU
 - **ESP8266** - obsoleto

## Interfaces Suportadas

| Interface       | ESP8266 | ESP32 | RP2040 |
|----------------:|--------:|------:|-------:|
| UART            | Sim     |   Sim |    Sim |
| I2C             | Sim     |   Sim |    Sim |
| SPI             | -       |   Sim |    Sim |

## Protocolos de Receptor Suportados

| Protocol        | ESP8266 | ESP32 | RP2040 |
|----------------:|--------:|------:|-------:|
| PPM             | Sim     |   Sim |    Sim |
| SBUS            | Sim     |   Sim |    Sim |
| CRSF (ELRS)     | Sim     |   Sim |    Sim |

## Protocolos de Motor Suportados

| Protocol        | ESP8266 | ESP32 | RP2040 |
|----------------:|--------:|------:|-------:|
| PWM             | Sim     |   Sim |    Sim |
| BRUSHED         | Sim     |   Sim |    Sim |
| ONESHOT125      | Sim     |   Sim |    Sim |
| ONESHOT42       | -       |   Sim |    Sim |
| MULTISHOT       | -       |   Sim |    Sim |
| DSHOT150        | Sim     |   Sim |    Sim |
| DSHOT300        | Sim     |   Sim |    Sim |
| DSHOT600        | -       |   Sim |    Sim |

# Outros Protocolos

| Protocolo       | ESP8266 | ESP32 | RP2040 |
|----------------:|--------:|------:|-------:|
| MSP             | Sim     |   Sim |    Sim |
| CLI             | Sim     |   Sim |    Sim |
| BLACKBOX        | Sim     |   Sim |    Sim |
| ESPNOW          | Sim     |   Sim |      - |

## Giroscópios Suportados

| Dispositivo | ESP8266 | ESP32 | RP2040 |
|------------:|--------:|------:|-------:|
| MPU6050     | Sim     |   Sim |    Sim |
| MPU6000     | -       |   Sim |    Sim |
| MPU6500     | Sim     |   Sim |    Sim |
| MPU9250     | Sim     |   Sim |    Sim |
| ICM20602    | Sim     |   Sim |    Sim |
| BMI160      | Sim     |   Sim |    Sim |

## Barômetros Suportados

| Dispositivo | ESP8266 | ESP32 | RP2040 |
|------------:|--------:|------:|-------:|
| BMP180      | Sim     |   Sim |    Sim |
| BMP280      | Sim     |   Sim |    Sim |
| SPL06       | Sim     |   Sim |    Sim |

## Bússolas Suportadas

| Dispositivo | ESP8266 | ESP32 | RP2040 |
|------------:|--------:|------:|-------:|
| HMC5883     | Sim     |   Sim |    Sim |
| QMC5883     | Sim     |   Sim |    Sim |
| AK8963      | Sim     |   Sim |    Sim |

## Licence
This project is distributed under MIT Licence. Bear in mind that:

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[Repositório oficial](https://github.com/rtlopez/esp-fc)