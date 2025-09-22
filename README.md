# this readme is not complete. [Instead read BACKEND - LYRA README.md](github.com/akshay-abraham/Lyra)

````
# **ZIA - The Smart Student Companion** 🚀

![GitHub Repo Size](https://img.shields.io/github/repo-size/akshay-abraham/zia?style=flat-square)
![License](https://img.shields.io/github/license/akshay-abraham/zia?style=flat-square)
![Open Issues](https://img.shields.io/github/issues/akshay-abraham/zia?style=flat-square)
![GitHub Stars](https://img.shields.io/github/stars/akshay-abraham/zia?style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/akshay-abraham/zia?style=flat-square)

---

## 🌟 **Project Overview**

**ZIA** is a **wearable AI-powered student companion band** that integrates **education assistance, health monitoring, social support**, and **parent-teacher engagement**.
It is **designed for day-to-day student use**, promoting **learning, wellbeing, and safety**, without replacing teachers.

> **Purpose:**
> - Provide AI-guided learning tailored to student style
> - Track daily health habits (hydration, menstrual cycles, posture)
> - Facilitate anonymous/named social reporting
> - Notify teachers of important student queries

---

## 🎯 **Key Features**

### 1️⃣ Education Assistant
- Voice/text guidance for homework & studies
- Adaptive learning based on student curiosity
- Personalized hints & learning style insights
- Escalation of complex doubts to teacher notifications

### 2️⃣ Health & Habit Monitoring
- Water intake reminders optimized per student
- Menstruation support & cycle reminders
- Posture/activity tracking with accelerometer

### 3️⃣ Social Support
- Anonymous/named reporting system for bullying
- AI-guided emotional support & habit nudges
- Teacher alerts for immediate interventions

### 4️⃣ Parent App Integration
- Daily monitoring of study habits and health
- Notifications for irregular trends or flagged events

---

## 🛠 **Implementation Plan**

### Hardware
| Component | Model / Tech | Purpose |
|----------|----------------|---------|
| Microcontroller | ESP32-S3 | Wi-Fi, I2S audio streaming |
| Microphone | MEMS I2S Mic | Voice input |
| Sensors | Accelerometer | Activity / posture tracking |
| Sensors | Capacitive water sensor | Hydration tracking |
| Sensors | Temperature / Humidity | Environmental context |
| Output | Speaker / Piezo | Audio guidance |
| Output | OLED Display 0.96–1.3" | Private text output |
| Output | Vibration Motor | Discreet notifications |

### Software
| Layer | Tech / Library | Notes |
|-------|----------------|-------|
| Cloud AI | OpenAI ChatGPT, Whisper, TTS API | Guides students, STT, TTS |
| Edge Logic | ESP32 Firmware | Audio capture, sensor processing, cloud communication |
| Mobile Apps | Flutter / React Native | Parent & Teacher dashboards |
| Backend | Firebase / AWS Lambda / Node.js | Notifications, database integration |
| Database | Firestore / SQLite | Activity, health, and query logs |

---

## 💡 **System Architecture**

```mermaid
graph TD
    A[Student Band] --> B[Voice Input / Sensors]
    B --> C[ESP32 Firmware]
    C --> D[Cloud AI: STT, GPT, TTS]
    D --> E[Band Output: Audio / Display / Vibration]
    D --> F[Teacher / Parent Notifications]
    B --> G[Health & Activity Logs]
    G --> H[Parent / School Dashboard]
````

---

## 🧩 **Code Structure**

```text
/zia
├── firmware
│   ├── main.cpp           # Entry point for ESP32
│   ├── audio_handler.cpp  # Microphone capture & streaming
│   ├── sensor_handler.cpp # Sensor readings & preprocessing
│   ├── wifi_manager.cpp   # API connectivity & cloud communication
│   └── output_handler.cpp # Speaker, OLED display, vibration control
├── cloud
│   ├── ai_gateway.py      # STT, GPT, TTS logic
│   └── notification.py    # Parent & teacher notifications
├── mobile_app
│   ├── student_app/
│   ├── parent_app/
│   └── teacher_app/
├── docs/
└── README.md
```

````
### Example ESP32 Audio Capture Snippet

```cpp
#include <I2S.h>

void setup() {
  I2S.begin(I2S_PHILIPS_MODE, 16000, I2S_BITS_PER_SAMPLE_16BIT);
}

void loop() {
  int16_t buffer[256];
  int bytesRead = I2S.read(buffer, sizeof(buffer));
  if (bytesRead > 0) {
      // Stream audio to cloud AI
  }
}
````

````
### Cloud AI Call Example (Python)

```python
import openai

openai.api_key = "YOUR_API_KEY"

def get_ai_response(student_text):
    response = openai.ChatCompletion.create(
        model="gpt-4o-mini",
        messages=[{"role":"user", "content": student_text}]
    )
    return response.choices[0].message.content
````

---

```
## 🔧 **Design Considerations**

* Privacy-first: All queries encrypted, anonymous optional
* Budget-friendly: Individual parent API key per band
* Display vs Audio:

  * Display → Private / sensitive messages
  * Audio → Hands-free casual guidance
* Minimal & lightweight: Comfortable for daily wear

---

## 🎨 **Future Expansion**

* Adaptive AI learning styles
* Gamified habit & study rewards
* Integration with school LMS
* Peer collaboration & social features

---

```
