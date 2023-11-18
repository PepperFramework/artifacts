# Setup Protocol V1

## Fabian Baitura Issue rundown

---

This is written by mind so it may be incorrect to a small degree (next time write it during install you little goof)

### Android Studio Versions used

* Electric Eel 2022.1.1 Patch 2
* Dolphin 2021.3.1 Patch 1
* Chipmunk 2021.2.1 Patch 2
* Bumblebee 2021.1.1 Patch 1
* Bumblebee 2021.1.1 Patch 2
* Bumblebee 2021.1.1 Patch 3

### Pepper SDK Setup Versions used

* 1.5.3
* 1.3.15

---

### Pepper API Versions used

* API 7
* API 5
* API 3

---

### Meetings with Ahif (And how they went)
* first meeting, introducing bugs we currently have, fixing sdk not recognized bug, trying to connect to pepper / failure
* secound meeting, trying to fix gradle bug without success. Trying to fix 95% Emulator loading bug without success (Emulator is apperently not being recognized).

---

### Other Issues

* Having trouble connecting to the real Pepper
* Router connetion extremly faulty. Apperently didn't work neither for us nor for the AHIF at the moment we attemted it.
* Deadlock on help (AHIF cannot help us any further with the issues we have)
* I've also had Issues with gradle. There seems to be an issue where it cannot accept the base package (not resolved yet)

---
#### Combinations we have tried out:

**Electric Eel 2022.1.1 Patch 2**

- [x] Pepper SDK 1.5.3
  - [x] API 7
    - [x] Tablet Emulator (never finishes loading, always crashes when trying to switch windows)
    - [x] Movement Emulator (works only 10% of the time)
  - [x] API 5
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [x] API 3
    - [ ] Tablet Emulator
    - [ ] Movement Emulator

- [x] Pepper SDK 1.3.15
  - [x] API 7
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [x] API 5
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [x] API 3
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
---
**Dolphin 2021.3.1 Patch 1**

- [x] Pepper SDK 1.5.3
  - [x] API 7
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [x] API 5
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 3
    - [ ] Tablet Emulator
    - [ ] Movement Emulator

- [x] Pepper SDK 1.3.15
  - [ ] API 7
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 5
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 3
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
---
**Chipmunk 2021.2.1 Patch 2**

- [x] Pepper SDK 1.5.3
  - [x] API 7
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [x] API 5
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 3
    - [ ] Tablet Emulator
    - [ ] Movement Emulator

- [ ] Pepper SDK 1.3.15
  - [ ] API 7
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 5
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 3
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
---
**Bumblebee 2021.1.1 Patch 1**

- [x] Pepper SDK 1.5.3
  - [x] API 7
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 5
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 3
    - [ ] Tablet Emulator
    - [ ] Movement Emulator

- [x] Pepper SDK 1.3.15
  - [x] API 7
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 5
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 3
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
---
**Bumblebee 2021.1.1 Patch 2**

- [x] Pepper SDK 1.5.3
  - [x] API 7
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 5
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 3
    - [ ] Tablet Emulator
    - [ ] Movement Emulator

- [ ] Pepper SDK 1.3.15
  - [x] API 7
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 5
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 3
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
---
**Bumblebee 2021.1.1 Patch 3**

- [x] Pepper SDK 1.5.3
  - [x] API 7
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [x] API 5
    - [x] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 3
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
- [x] Pepper SDK 1.3.15
  - [x] API 7
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [x] API 5
    - [ ] Tablet Emulator
    - [ ] Movement Emulator
  - [ ] API 3
    - [ ] Tablet Emulator
    - [ ] Movement Emulator

---

## Leon Leeb Issue rundown

### Meetings with Ahif (And How They Went)

* First meeting: Tried to setup the pepper development environment (failed)
* Pepper Presentaion: Complete mess, other class didn't have linux so we wasted the whole time for setting up dual boot.

---

### Other Issues

* Having trouble connecting to the real Pepper and emulation strait up hasn't worked yet
* Deadlock on help
* faulty Router connection
* Hard to find good turtorials for developing the pepper when searching the web