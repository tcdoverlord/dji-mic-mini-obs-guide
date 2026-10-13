# 🎙️ DJI Mic Mini + OBS Studio Audio Guide

<p align="center">
  <img src="https://raw.githubusercontent.com/tcdoverlord/dji-mic-mini-obs-guide/main/DJI%20Mic%20Mini%20OBS%20Audio%20Guide%20(1).png" alt="DJI Mic Mini OBS Studio Audio Guide — hero image" width="100%">
</p>

<p align="center">
  <strong>Clear voice. Less background noise. Better live shows.</strong><br>
  A visual setup guide for the DJI Mic Mini (1 transmitter + 1 receiver), OBS Studio, and Windows.
</p>

<p align="center">
  <img alt="Windows" src="https://img.shields.io/badge/Platform-Windows-0878D1?style=for-the-badge&logo=windows">
  <img alt="OBS Studio" src="https://img.shields.io/badge/OBS-Studio-302E31?style=for-the-badge&logo=obsstudio">
  <img alt="Noise suppression" src="https://img.shields.io/badge/Noise_Suppression-RNNoise-7C3AED?style=for-the-badge">
  <img alt="Visual guide" src="https://img.shields.io/badge/Guide-Visual%20Setup-00B8D9?style=for-the-badge">
</p>

---

## ⚡ Your setup at a glance

<table>
  <tr>
    <td align="center" width="33%">
      <h3>🎚️ RX output</h3>
      <strong>+12</strong><br>
      <sub>Set in the DJI Mic Mini phone app</sub>
    </td>
    <td align="center" width="33%">
      <h3>🔊 Live-show audio</h3>
      <strong>Stereo</strong><br>
      <sub>Switch from Mono in the phone app</sub>
    </td>
    <td align="center" width="33%">
      <h3>🟠 TX noise cancellation</h3>
      <strong>Orange light</strong><br>
      <sub>Press the transmitter button once</sub>
    </td>
  </tr>
</table>

> These are the settings used in this guide. Make a short test recording before going live because room acoustics, input level, microphone placement, and speaking volume affect the final sound.

## 🧭 Jump to a section

<table>
  <tr>
    <td width="50%">
      <a href="#1-connect-the-dji-mic-mini"><strong>01 · Connect your mic</strong></a><br>
      Pair TX/RX and choose the receiver in OBS.
    </td>
    <td width="50%">
      <a href="#2-prepare-the-phone-app-and-transmitter"><strong>02 · Prepare the hardware</strong></a><br>
      RX +12, Stereo output, orange noise-cancellation indicator.
    </td>
  </tr>
  <tr>
    <td width="50%">
      <a href="#3-set-up-obs-audio"><strong>03 · Configure OBS</strong></a><br>
      Set 48 kHz, Stereo, and the correct input.
    </td>
    <td width="50%">
      <a href="#4-add-microphone-filters"><strong>04 · Add filters</strong></a><br>
      Apply noise suppression and level shaping.
    </td>
  </tr>
  <tr>
    <td width="50%">
      <a href="#5-check-your-audio-level"><strong>05 · Monitor levels</strong></a><br>
      Keep audio clean and avoid clipping.
    </td>
    <td width="50%">
      <a href="#6-position-the-transmitter"><strong>06 · Position the mic</strong></a><br>
      Reduce clothing noise and keep your voice natural.
    </td>
  </tr>
</table>

---

## 1. Connect the DJI Mic Mini

1. Pair the DJI Mic Mini transmitter (**TX**) and receiver (**RX**).
2. Connect the receiver to your PC using a supported USB or audio connection.
3. In OBS, open **Settings → Audio**.
4. Set **Mic/Auxiliary Audio** to the DJI receiver. It may appear as `Microphone (Wireless Mic Rx)`.
5. Speak and confirm that the **Mic/Aux** meter moves.
6. Avoid capturing the same microphone twice through both a global device and a separate Audio Input Capture source.

## 2. Prepare the phone app and transmitter

<blockquote>
  <strong>🎛️ In the DJI Mic Mini phone app</strong>
  <ol>
    <li>Set the receiver (RX) level to <strong>+12</strong>.</li>
    <li>Change the live-show output mode from <strong>Mono</strong> to <strong>Stereo</strong>.</li>
  </ol>
  <strong>🟠 On the transmitter (TX)</strong>
  <ol>
    <li>Press the transmitter's power/noise-cancellation button <strong>once</strong> to enable noise cancellation.</li>
    <li>Confirm the indicator light turns <strong>orange</strong>.</li>
  </ol>
</blockquote>

App labels and button behavior can vary by version. Confirm the orange indicator and make a short listening test before going live.

## 3. Set up OBS audio

Open **Settings → Audio** and start with these values:

<table>
  <thead>
    <tr><th>OBS option</th><th>Recommended value</th></tr>
  </thead>
  <tbody>
    <tr><td>Sample Rate</td><td><code>48 kHz</code></td></tr>
    <tr><td>Channels</td><td><code>Stereo</code></td></tr>
    <tr><td>Mic/Auxiliary Audio</td><td>DJI Mic Mini receiver</td></tr>
    <tr><td>Desktop Audio</td><td>Disabled if you do not need it</td></tr>
    <tr><td>Disable Windows audio ducking</td><td>Enabled</td></tr>
  </tbody>
</table>

Click **Apply**, then **OK**.

## 4. Add microphone filters

In OBS **Audio Mixer**, open the menu next to **Mic/Aux** and select **Filters**.

<details open>
  <summary><strong>Recommended filter values</strong></summary>

  <table>
    <thead><tr><th>Filter</th><th>Control</th><th>Starting value</th></tr></thead>
    <tbody>
      <tr><td><strong>Noise Suppression</strong></td><td>Method</td><td><code>RNNoise</code></td></tr>
      <tr><td><strong>Expander</strong></td><td>Ratio / Threshold</td><td><code>3:1</code> / <code>-45 dB</code></td></tr>
      <tr><td></td><td>Attack / Release</td><td><code>5 ms</code> / <code>100 ms</code></td></tr>
      <tr><td></td><td>Output Gain / Detection</td><td><code>0 dB</code> / <code>RMS</code></td></tr>
      <tr><td><strong>3-Band Equalizer</strong></td><td>High / Mid / Low</td><td><code>+2 / -2 / +2 dB</code></td></tr>
      <tr><td><strong>Compressor</strong></td><td>Ratio / Threshold</td><td><code>3:1</code> / <code>-18 dB</code></td></tr>
      <tr><td></td><td>Attack / Release</td><td><code>5 ms</code> / <code>100 ms</code></td></tr>
      <tr><td></td><td>Output Gain</td><td><code>+4 dB</code></td></tr>
      <tr><td><strong>Gain</strong></td><td>Gain</td><td><code>+15 dB</code></td></tr>
      <tr><td><strong>Limiter</strong></td><td>Threshold / Release</td><td><code>-1 dB</code> / <code>60 ms</code></td></tr>
    </tbody>
  </table>
</details>

<p align="center">
  <strong>RNNoise → Expander → EQ → Compressor → Gain → Limiter</strong>
</p>

- **RNNoise** helps reduce background noise. If the voice sounds watery or artificial, reduce room noise and test with suppression disabled.
- **Expander** reduces quieter room noise when you are not speaking. If it cuts words off, make its threshold less aggressive.
- **EQ** values are starting points; tune them to your voice.
- **Compressor** balances quieter and louder speech. Reduce output gain if the voice sounds squashed or too loud.
- **Gain +15 dB** is the value shown in this guide, not a universal recommendation. Gain raises both voice and background noise.
- **Limiter last** provides final peak protection. Gain placed after the limiter can push audio beyond its ceiling.

Some OBS versions do not include a 3-band equalizer by default. If it is missing, skip it or use a reputable compatible OBS audio-filter plugin.

---

## 5. Check your audio level

<p align="center">
  <img src="assets/02-obs-audio-levels.png" alt="OBS Studio Mic/Aux meter and audio level guide" width="100%">
</p>

Use the Mic/Aux meter while speaking at your usual live-show volume.

<table>
  <tr><td>🟢 <strong>Normal speech</strong></td><td><code>-24 to -12 dBFS</code></td></tr>
  <tr><td>🟡 <strong>Louder speech peaks</strong></td><td><code>-12 to -6 dBFS</code></td></tr>
  <tr><td>🔴 <strong>Avoid clipping</strong></td><td>Do not hit <code>0 dBFS</code></td></tr>
</table>

The OBS mixer fader shown in your screenshot is **-3.0 dB (Global)**. This is the fader setting, not a guarantee that the voice meter peaks at -3 dB. Listen to a test recording and adjust the receiver level, filters, and fader as needed.

## 6. Position the transmitter

<p align="center">
  <img src="assets/03-mic-placement-guide.png" alt="DJI Mic Mini microphone placement and windscreen guide" width="100%">
</p>

- Clip TX near your collar or upper chest, roughly **6–12 inches (15–30 cm)** from your mouth when practical.
- Use the furry windscreen when wind or airflow is an issue.
- Keep clothing, jewelry, and hands from rubbing against or covering the microphone.
- Avoid placing the microphone directly in your breath stream.
- Speak at a consistent volume and make a short test recording before going live.

## ✅ Quick pre-show checklist

- [ ] TX and RX are paired.
- [ ] Receiver level is set to **+12** in the phone app.
- [ ] Live-show output is set to **Stereo**, not Mono.
- [ ] TX noise cancellation is enabled and the indicator is orange.
- [ ] OBS is using the DJI Mic Mini receiver.
- [ ] RNNoise and chosen filters are enabled.
- [ ] Mic/Aux meter moves while speaking.
- [ ] Test recording is clear, natural, and not clipping.

## 🛠️ Troubleshooting

<table>
  <thead><tr><th>Problem</th><th>Try this</th></tr></thead>
  <tbody>
    <tr><td>Voice too quiet</td><td>Check the selected input and RX level; increase OBS Gain carefully.</td></tr>
    <tr><td>Distorted or clipping</td><td>Lower receiver/input level or OBS Gain, and keep the Limiter last.</td></tr>
    <tr><td>Words get cut off</td><td>Make the Expander threshold less aggressive.</td></tr>
    <tr><td>Voice sounds artificial</td><td>Reduce noise suppression or EQ changes, then retest.</td></tr>
    <tr><td>Background noise remains</td><td>Move closer to the mic and reduce room noise.</td></tr>
    <tr><td>No OBS meter movement</td><td>Check pairing, connection, and Mic/Aux device selection.</td></tr>
  </tbody>
</table>

---

<p align="center">
  <strong>Made for streamers and creators by <a href="https://github.com/tcdoverlord">tcdoverlord</a> 💙</strong><br>
  <sub>Community guide; not affiliated with or endorsed by DJI or the OBS Project.</sub>
</p>
