# Kwid-FC Firmware
Neste repositório está o código fonte do firmware usado na controladora de voo ESP32 para o projeto KWID da DeltaV Drones


> [!NOTE]
> Nem todas as funções que aparecem no Betaflight Configurator estão realmente disponíveis no firmware. se você não consegue alterar uma determinada opção no Configurator, isso significa que ela não é suportada. Normalmente, o valor volta para o anterior depois de salvar.
Aqui está mais detalhes sobre [Como configurar o Betaflight Configurator](/docs/setup.md).


## Alterações feitas para o KWID
* Calibração de desvio (bias) do giroscópio por eixo, substituindo a correção bruta anterior. O algoritmo agora aplica a calibração individualmente a cada eixo, corrigindo de forma eficaz o drift persistente no eixo Z.

## Funcionalidades
* Placas Espressif (ESP32, ESP8266, ESP32-S3, ESP32-S2, ESP32-C3)
* Protocolos de ESC (PWM, Oneshot125/42, Multishot, Brushed, Dshot150/300/600 bidirectional)
* Receptores PPM, SBUS e CRSF
* Receptor ESP-NOW e Configuração WiFi integradas [Leia Mais...](/docs/wireless.md)
* Módulo giroscópio SPI e I2C suportados (MPU6050, MPU9250, ICM20602, BMI160)
* Modos de voo (ACRO, ANGLE, AIRMODE)
* Frames (Quad X)
* Compatibilidade com Betaflight configuration (v10.8-v10.10)
* Filtros de giroscópio personalizados (LPF, Notch, dTerm, RPM)
* Gravação Blackbox (OpenLog/OpenLager/Flash)
* gyro/loop de até 4kHz no ESP32 com giroscópio SPI
* Protocolo de interface MSP
* Protocolo de interface CLI
* Mapeamento de Recursos/Pinos
* Ajuste de PID em voo
* Buzzer
* Monitor de tensão em baterias Lipo
* Failsafe

## Requisitos
Hardware:
* ESP32 mini board, ESP8266 Wemos D1 mini ou similar
* MPU9250 SPI ou MPU6050 I2C gyro (GY-88, GY-91, GY-521 ou similar)
* PDB com 5V BEC
* Buzzer e alguns componentes eletrônicos (opcional).

Software:
* [Betaflight Configurator](https://github.com/betaflight/betaflight-configurator/releases) (v10.8 to v10.10)
* [CH340 Driver](https://sparks.gogo.co.nz/ch340.html)

## Gravar Firmware
1. Download o firmware desejado na [Página de Lançamento](https://github.com/rtlopez/esp-fc/releases)
2. Vá para [Site ESP Tool](https://espressif.github.io/esptool-js/)
3. Selecione a baudrate de 115200, clique em "Connect" e escolha a porta do dispositivo
4. Adicione o arquivo de firmware e escolha o "Flash Address" para `0x1000`
5. Clique em "Program"
6. Assim que concluir, reinicie o dispositivo

OBS: Apenas ESP32 e ESP8266 podem ter o firmware gravado dessa forma.

## Chips Suportados

 - **ESP32** - recomendado
 - **ESP32-S2** - experimantal
 - **ESP32-S3** - experimantal
 - **ESP32-C3** - experimantal, queda de performance, sem FPU
 - **RP2040** - experimantal, queda de performance, sem FPU
 - **ESP8266** - obsoleto

## Interfaces Suportadas

| Interface | ESP8266 | ESP32 | RP2040 |
|---:|---:|---:|---:|
| UART | Sim | Sim | Sim |
| I2C | Sim | Sim | Sim |
| SPI | - | Sim | Sim |

## Protocolos de Receptor Suportados

| Protocol | ESP8266 | ESP32 | RP2040 |
|---:|---:|---:|---:|
| PPM | Sim | Sim | Sim |
| SBUS | Sim | Sim | Sim |
| CRSF (ELRS) | Sim | Sim | Sim |

## Protocolos de Motor Suportados

| Protocol | ESP8266 | ESP32 | RP2040 |
|---:|---:|---:|---:|
| PWM | Sim | Sim | Sim |
| BRUSHED | Sim | Sim | Sim |
| ONESHOT125 | Sim | Sim | Sim |
| ONESHOT42 | - | Sim | Sim |
| MULTISHOT | - | Sim | Sim |
| DSHOT150 | Sim | Sim | Sim |
| DSHOT300 | Sim | Sim | Sim |
| DSHOT600 | - | Sim | Sim |

# Outros Protocolos

| Protocolo | ESP8266 | ESP32 | RP2040 |
|---:|---:|---:|---:|
| MSP | Sim | Sim | Sim |
| CLI | Sim | Sim | Sim |
| BLACKBOX | Sim | Sim | Sim |
| ESPNOW | Sim | Sim | - |

## Giroscópios Suportados

| Dispositivo | ESP8266 | ESP32 | RP2040 |
|---:|---:|---:|---:|
| MPU6050 | Sim | Sim | Sim |
| MPU6000 | - | Sim | Sim |
| MPU6500 | Sim | Sim | Sim |
| MPU9250 | Sim | Sim | Sim |
| ICM20602 | Sim | Sim | Sim |
| BMI160 | Sim | Sim | Sim |

## Barômetros Suportados

| Dispositivo | ESP8266 | ESP32 | RP2040 |
|---:|---:|---:|---:|
| BMP180 | Sim | Sim | Sim |
| BMP280 | Sim | Sim | Sim |
| SPL06 | Sim | Sim | Sim |

## Bússolas Suportadas

| Dispositivo | ESP8266 | ESP32 | RP2040 |
|---:|---:|---:|---:|
| HMC5883 | Sim | Sim | Sim |
| QMC5883 | Sim | Sim | Sim |
| AK8963 | Sim | Sim | Sim |

## Licence
This project is distributed under MIT Licence. Bear in mind that:

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

Este firmware foi baseado neste [Repositório](https://github.com/rtlopez/esp-fc)