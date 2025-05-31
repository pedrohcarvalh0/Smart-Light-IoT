# Smart Light IoT 🌟

## Automação de Iluminação Externa com Raspberry Pi Pico W e MQTT

---

## 📌 Sobre o Projeto

O projeto **Smart Light IoT** é uma solução para automação residencial, especialmente voltado ao controle inteligente de iluminação externa. Desenvolvido com uma placa BitDogLab (baseada no Raspberry Pi Pico W), sensor LDR (Light Dependent Resistor) e o protocolo MQTT, o sistema controla automaticamente uma lâmpada com base na luminosidade ambiente. Além disso, permite controle remoto manual via MQTT, oferecendo praticidade e conforto ao usuário.

---

## 🚀 Funcionalidades Principais

### 🔄 **Modo Automático**
- Mede continuamente a luminosidade ambiente usando o sensor LDR.
- Liga automaticamente o LED quando a luminosidade está baixa (escuro).
- Desliga automaticamente o LED quando há luz suficiente.

### 🎛️ **Modo Manual**
- Permite ligar ou desligar o LED remotamente, independente das condições de luminosidade.
- Comandos enviados através do protocolo MQTT.

---

## 🛠️ Tecnologias Utilizadas

- **Hardware:**
  - Raspberry Pi Pico W (BitDogLab - RP2040)
  - Sensor LDR com divisor de tensão
  - LED representando a lâmpada inteligente
  - Botão físico para reset (BOOTSEL)

- **Software:**
  - SDK C/C++ Raspberry Pi Pico
  - Protocolo MQTT (via Mosquitto)
  - IoT MQTT Panel (App Android)
  - Termux (para executar o Mosquitto em dispositivos Android)

---

## ⚙️ Configuração e Personalização

### 🖥️ Configurações Principais (Editar no código):

```c
#define WIFI_SSID "Sua rede Wi-Fi"
#define WIFI_PASSWORD "Sua senha Wi-Fi"
#define MQTT_SERVER "IP do Broker MQTT"
#define LED_PIN 11
#define LDR_ADC_PIN 28
#define ADC_INPUT_CHANNEL 2
#define VALOR_LIMIAR_LUZ_BAIXA 1000
#define LIGHT_WORKER_TIME_S 1
```

---

## 📡 Tópicos MQTT

| Tópico           | Direção     | Descrição                             | Valores                |
|------------------|-------------|---------------------------------------|------------------------|
| `/light`         | Publicação  | Valor bruto do LDR                    | 0-4095                 |
| `/light/status`  | Publicação  | Status do ambiente (luz)              | "Dark", "Bright"      |
| `/led`           | Assinatura  | Controle manual do LED                | "On", "Off" ou "1","0"|
| `/led/state`     | Publicação  | Estado atual do LED                   | "On", "Off"           |
| `/led/auto`      | Assinatura  | Retorno ao modo automático            | "On"                  |
| `/led/mode`      | Publicação  | Modo atual                            | "Auto", "Manual"      |
| `/online`        | Publicação  | Status da conexão                     | "1" online, "0" offline|
| `/print`         | Assinatura  | Mensagem impressa no console          | texto                  |
| `/exit`          | Assinatura  | Encerra o cliente MQTT                | qualquer mensagem      |

---

## 📱 Configuração do IoT MQTT Panel

Crie widgets no IoT MQTT Panel para:
- Visualizar nível de luminosidade
- Indicação visual do LED
- Controle manual do LED
- Botão de retorno ao modo automático
- Status detalhado dos dispositivos

---

---

## 📝 Como Executar o Projeto

1. Clone o repositório:
```bash
git clone https://github.com/seu-usuario/smart-light-iot.git
```

2. Compile e faça upload para a placa BitDogLab usando SDK do Raspberry Pi Pico.

3. Configure o broker MQTT (Mosquitto) no seu dispositivo móvel usando Termux ou em um computador.

4. Utilize o IoT MQTT Panel para monitoramento e controle.

---
