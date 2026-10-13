# 🎙️ DJI Mic Mini + OBS Studio Audio Guide

<p align="center">
  <img src="https://raw.githubusercontent.com/tcdoverlord/dji-mic-mini-obs-guide/main/DJIMicMiniOBSAudioGuide.jpg" alt="DJI Mic Mini OBS Studio Audio Guide" width="100%">
</p>

<p align="center">
  <strong>Clear voice. Less background noise. A compact setup for desktop and mobile streaming.</strong><br>
  A practical visual guide to using the DJI Mic Mini with OBS Studio, including receiver/transmitter settings and example audio filters.
</p>

<p align="center">
  <img alt="Windows" src="https://img.shields.io/badge/Platform-Windows-0878D1?style=for-the-badge&logo=windows">
  <img alt="OBS Studio" src="https://img.shields.io/badge/OBS-Studio-302E31?style=for-the-badge&logo=obsstudio">
  <img alt="Noise suppression" src="https://img.shields.io/badge/Noise_Suppression-RNNoise-7C3AED?style=for-the-badge">
  <img alt="Visual guide" src="https://img.shields.io/badge/Guide-Visual%20Setup-00B8D9?style=for-the-badge">
</p>

---

## ⚡ Setup at a glance

<table>
  <tr>
    <td align="center" width="33%">
      <h3>🎚️ RX receiver</h3>
      <strong>+12</strong><br>
      <sub>Receiver audio level in the DJI app</sub>
    </td>
    <td align="center" width="33%">
      <h3>🔊 Output mode</h3>
      <strong>Stereo</strong><br>
      <sub>Choose Stereo in the app</sub>
    </td>
    <td align="center" width="33%">
      <h3>🟠 TX transmitter</h3>
      <strong>Noise cancellation</strong><br>
      <sub>Orange TX indicator when enabled</sub>
    </td>
  </tr>
</table>

> **Device settings used in this guide:** TX transmitter noise cancellation is **ON**; RX receiver output mode is **Stereo**. These are the settings used in this guide, not universal settings for every voice or room. Make a short test recording before going live and adjust levels to avoid clipping.

## 🎙️ My DJI Mic Mini Setup & Upgrade Plan

Here's how I'm building my setup based on my own testing:

**1. DJI Mic Mini Transmitter — Initial Test**

- Tested Bluetooth connectivity.
- Discovered that noise cancellation wasn't available in my initial transmitter-only setup.
- Lost connection in OBS, sometimes requiring a computer restart or signing out and back in to restore it.

**2. Added the DJI Receiver + Mic Mini**

- Added the receiver to access Stereo Mode and receiver audio-level adjustments.
- **Transmitter (TX) device setting: Noise Cancellation ON.** The TX indicator lights orange when noise cancellation is enabled.
- **Receiver (RX) device setting: Stereo Mode ON.** Select `Stereo` in the DJI device/app settings for the receiver's output mode.
- Now planning to use two microphones for podcasting and conversations.

**3. Authentic DJI Lightning Phone Adapter**

- Added the genuine DJI adapter for connecting my setup to my compatible iPhone.
- Makes switching to mobile livestreaming more convenient.

**4. Magnetic Neckband**

- Added a magnetic neckband with a mounting plate that works with the microphone's included magnet.
- Great for comfortable placement under a shirt or keeping the microphone out of the camera's view.

**5. Why My Next Purchase Is a Dedicated Receiver Setup**

The goal is to keep my PC streaming setup and iPhone livestreaming setup ready to go without constantly swapping adapters. I want the right receiver already connected to each device, with the mobile setup kept together and ready when I need it.

- **Dedicated iPhone/Lightning receiver:** Find a second-hand genuine DJI Mic Mini receiver (RX) and leave my authentic DJI Lightning phone adapter attached to it. This receiver will stay with my compatible iPhone livestreaming gear.
- **Dedicated PC/USB receiver:** Keep my current RX connected to the PC for OBS, so I don't have to disconnect it and move adapters every time I switch devices.
- **What to shop for:** Compare the price of a used receiver-only unit against **one complete additional DJI Mic Mini kit** with a transmitter and charging case. If the receiver-only price is close to the complete-kit price, the kit may be the better value because it also gives me another transmitter and charging case. I'm planning for one additional complete kit—not two.
- **Why I want the extra transmitter:** It gives me the option to use two microphones for podcasting, interviews, and conversations.
- **Keep the setups ready:** Leave the Lightning adapter attached to the mobile receiver and keep the PC receiver connected by USB when practical. Verify the charging/power arrangement for each connection before relying on it during a live show.

**Connection note:** The OBS connection losses described above occurred during the initial transmitter-only Bluetooth setup. Since adding the RX receiver, the connection issue has stopped.

---

## 🧭 Quick navigation

- [1. Connect the DJI Mic Mini](#1-connect-the-dji-mic-mini)
- [2. Configure the receiver and transmitter](#2-configure-the-receiver-and-transmitter)
- [3. Set up OBS audio](#3-set-up-obs-audio)
- [4. Add OBS filters](#4-add-obs-filters)
- [5. Monitor audio levels](#5-monitor-audio-levels)
- [6. Microphone placement](#6-microphone-placement)
- [7. Troubleshooting](#7-troubleshooting)

---

## 1. Connect the DJI Mic Mini

1. Pair the DJI Mic Mini transmitter (**TX**) with the receiver (**RX**).
2. Connect the receiver to your PC using a supported USB or audio connection.
3. In OBS Studio, open **Settings → Audio**.
4. Set **Mic/Auxiliary Audio** to the DJI receiver. It may appear as `Microphone (Wireless Mic Rx)`.
5. Speak and confirm that the **Mic/Aux** meter moves.
6. Avoid capturing the same microphone twice through both a global audio device and a separate Audio Input Capture source.

## 2. Configure the receiver and transmitter

### Receiver (RX)

- **Receiver audio level:** `+12`
- **Live-show output mode:** `Stereo`

Set these values in the DJI Mic Mini app if your model, firmware, and connection support the settings.

### Transmitter (TX)

- **Noise Cancellation:** Enabled
- **Indicator:** Orange when transmitter noise cancellation is enabled

The TX orange indicator is the noise-cancellation cue. Do not confuse light reflected from a blue background with an illuminated receiver status LED. Confirm your receiver mode in the app and test the sound before going live.

---

## 3. Set up OBS audio

Open **Settings → Audio** and start with these values:

| OBS option | Value |
|---|---|
| Sample Rate | `48 kHz` |
| Channels | `Stereo` |
| Mic/Auxiliary Audio | DJI Mic Mini receiver |
| Desktop Audio | Disable if you do not need it |
| Disable Windows audio ducking | Enable |

Click **Apply**, then **OK**.

## 4. Add OBS filters

In the OBS **Audio Mixer**, open the menu next to **Mic/Aux** and choose **Filters**.

### My example filter settings

| Filter | Controls | Starting value |
|---|---|---|
| **Expander** | Ratio / Threshold | `3:1` / `-45 dB` |
|  | Attack / Release | `5 ms` / `100 ms` |
|  | Output Gain / Detection | `0 dB` / `RMS` |
| **Noise Suppression** | Method | `RNNoise` |
| **3-Band Equalizer** | High / Mid / Low | `+2 / -2 / +2 dB` |
| **Compressor** | Ratio / Threshold | `3:1` / `-18 dB` |
|  | Attack / Release | `5 ms` / `100 ms` |
|  | Output Gain | `+4 dB` |
| **Gain** | Gain | `+15 dB` |
| **Limiter** | Threshold / Release | `-1 dB` / `60 ms` |

**Suggested filter order:**

`RNNoise → Expander → 3-Band EQ → Compressor → Gain → Limiter`

- **RNNoise** can reduce steady background noise. If your voice sounds watery or artificial, try reducing suppression or improving the room noise first.
- **Expander** reduces quieter room noise between phrases. If it cuts off words, make the threshold less aggressive.
- **EQ** settings are starting points; adjust them to your voice.
- **Compressor** helps even out speaking volume. Reduce output gain if the signal gets too loud.
- **Gain +15 dB** is the value used in this setup, not a universal recommendation. Gain raises background noise along with your voice.
- **Limiter last** gives the signal a final peak-control stage after gain is applied.

Some OBS installations do not include a 3-band equalizer by default. If it is missing, skip that filter or use a reputable OBS-compatible audio-filter plugin.

---

## 5. Monitor audio levels

Speak at your normal livestreaming volume while watching the OBS Mic/Aux meter.

| Voice level | Practical guide |
|---|---|
| Normal speech | Around `-24 to -12 dBFS` |
| Louder speech peaks | Around `-12 to -6 dBFS` |
| Clipping | Avoid reaching `0 dBFS` |

Treat these as practical targets rather than strict rules. The OBS mixer fader value is not the same as the actual audio peak. Make a short recording, listen back, and adjust the receiver level, filters, and fader as needed.

## 6. Microphone placement

- Clip the transmitter near the collar or upper chest, roughly **6–12 inches (15–30 cm)** from your mouth when practical.
- Use the furry windscreen when airflow or wind is an issue.
- Keep clothing, jewelry, and hands from rubbing against or covering the microphone.
- Avoid positioning the microphone directly in your breath stream.
- Speak consistently and make a short test recording before going live.

### Optional accessory tip

A compatible magnetic neckband can help keep the Mic Mini comfortably positioned and less visible under a shirt. Check that the mounting plate and magnet fit your specific transmitter/accessory arrangement.

---

## ✅ Quick pre-show checklist

- [ ] TX and RX are paired.
- [ ] Receiver audio level is set to **+12**, if supported by the current connection.
- [ ] Output mode is set to **Stereo**.
- [ ] TX noise cancellation is enabled; the TX indicator is orange.
- [ ] OBS is using the DJI receiver as the microphone input.
- [ ] OBS filters are enabled and levels are not clipping.
- [ ] Mic/Aux meter moves while speaking.
- [ ] A short test recording sounds clear and natural.

## 7. Troubleshooting

| Problem | Try this |
|---|---|
| OBS meter does not move | Check pairing, connection, and Mic/Aux device selection. |
| Voice is too quiet | Check the selected input and RX level; raise OBS gain carefully. |
| Audio distorts or clips | Lower receiver/input level or OBS gain; keep Limiter last. |
| Words get cut off | Make the Expander threshold less aggressive. |
| Voice sounds artificial | Reduce noise suppression or EQ changes, then test again. |
| Background noise remains | Move the mic closer and reduce room noise. |
| OBS loses the mic connection | Recheck the USB/audio connection and selected device; test whether the issue also happens outside OBS before assuming the cause. |

---

<p align="center">
  <strong>Made for streamers and creators by <a href="https://github.com/tcdoverlord">tcdoverlord</a> 💙</strong><br>
  <sub>Community guide; not affiliated with or endorsed by DJI or the OBS Project.</sub>
</p>
