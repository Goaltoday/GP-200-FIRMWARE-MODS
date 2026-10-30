# Custom Firmware 0.6 — Valeton GP-200

<img width="480" height="272" alt="custom6-startup" src="https://github.com/user-attachments/assets/0df64b3c-71ad-4ace-9ee1-f1697bec883b" />


> **⚠️ Experimental firmware modification**
>
> This project is experimental and currently in beta. Although the modifications are not expected to damage your GP-200, they have not been tested in every possible configuration.
>
> **Use at your own risk.** Always back up your presets before installing modified firmware.

## Acknowledgements

Special thanks to [Thomas (tntexplosivesltd)](https://github.com/tntexplosivesltd) for his discoveries and the invaluable help he has provided throughout this project.

---

## 1. What's New — Changelog

### Version 0.6.1

- Corrected bug to activate drums.

### Version 0.6

- Load up to **32 NAM A2 models** using the HTML loader.
- **NAM BLOCK** added.
- **Choose which effect family to use in each block**, allowing more flexible effect assignments.
- Simplified HTML firmware patcher.
- Updated **Trails in Patch Mode**:
  - The block order must remain unchanged.
  - You can change the effect family assigned to each block.
  - The Delay and Reverb blocks whose trails you want to preserve must retain the same settings.

### Version 0.5

- Added a **DSP Load (%) indicator**, displayed at the top center of the screen when selecting an effect.
- Improved Trails in Patch Mode:> ⚠️ Obsolete with 0.6
  - Effect order and assignments can be changed, except for the Delay and Reverb blocks whose trails must be preserved.
  - Their parameter values must remain unchanged.
  - Their ON/OFF states can differ between presets.
- Improved Scenes Mode:
  - The original preset acts as the base state.
  - Four additional Scenes (A–D) can be activated or deactivated.
  - This effectively provides five sound states per preset.

### Version 0.4

- Added **native NAM A2 Lite support**. Please read the instructions carefully.
- Added Trails in Patch Mode.

### Version 0.3

- Scenes Mode no longer automatically returns to Stomp Mode.
- Flexible footswitch assignments for Scenes A–D and Capture.
- Expanded effect combinations, including COMP and OCTA.⚠️ Obsolete with 0.6

---

## 2. What the HTML Firmware Patcher Does

The `Custom_Firmware` HTML tool is a browser-based firmware configurator.

It allows you to load a compatible GP-200 firmware BIN, select the NAM A2 to upload and generate a ZIP package containing the modified firmware.

**The HTML file is not installed on the pedal.** The generated BIN is the firmware image that must be installed.

### Firmware compatibility

- Supports GP-200 firmware versions **1.8.0 and 1.8.2**, including certain previously modified firmware images.
- The generator may recognize and preserve existing MODs.
- If an image is reported as unrecognized, incomplete, or incompatible, stop and verify the BIN before continuing.
- ⚠️ **All editing is performed directly on the GP-200. The official editor does not support the custom functionality**
-  ℹ️  A new editor with support for the modified features is under development.

---

## 3. Before You Start

Before generating a custom firmware:

1. **Back up your presets.**
2. Back up any official GP-200 editor files you intend to replace.
3. Download the compatible GP-200 firmware BIN.
4. Prepare any additional files you plan to use:
      - Compatible NAM A2 files for native NAM loading.
5. Use a desktop web browser to open the HTML configurator.
6. Keep the generated ZIP and its manifest together for future reference.

---

## 4. Open the HTML and Load a Firmware BIN

1. Locate the `Custom_Firmware` HTML file included in the release.
2. Open it in a desktop browser by double-clicking the file or using the browser's **Open File** command.
3. Under **Load your firmware BIN**, select the firmware image you want to modify.
4. Wait for the compatibility check to complete.
5. Select the NAM A2 you want to include.
6. Click **Build and download firmware**
7. Install the generated BIN using Valeton's official GP-200 firmware update procedure for the corresponding firmware version.
8. Do not disconnect or power off the pedal during the update.
9. Once the GP-200 restarts, check that it operates normally and test each selected modification.

> **Recommendation:** Test your modified firmware and presets before using them in rehearsals or live performances.

---

## 5. Using the MODs

### 5.1. Universal BLOCK

<img width="1672" height="941" alt="BLOCKS" src="https://github.com/user-attachments/assets/5f252510-881a-4a0d-bbe5-5970833687d7" />


It is possible to use any block to load a family of effects.

Select a BLOCK an rotate the knob to choose the desired family.

You can choose as many of each block as the DSP limits allows for each patch.

**Video demonstration:** https://youtu.be/Xp4BGLzOvZw

⚠️ The buttons of the GP200 will represent the first 10 blocks


### 5.2. Dual Chain — Parallel Signal Routing

**Video demonstration:** [Dual Chain on the GP-200](https://youtu.be/goAHSmzvuvo)

DUAL CHAIN introduces two signal paths, **A and B**, with controls for blending, sample alignment, and polarity.

All CHAIN operations and editing are performed directly on the GP-200.

#### Enable and configure Dual Chain

1. Enable **DUAL CHAIN** in the firmware configurator.
2. On the GP-200, open the **FX Loop** menu.
3. Select **CHAIN** to access the routing configuration, using the knob below SERIES/PARALLEL.

![Dual Chain interface](https://github.com/user-attachments/assets/8c149a10-41b5-4bb0-94ab-26479baccfb0)

4. To change the effect order, press and hold **PARAM** on an effect, then use the pedal's native effect-reordering controls.
5. On the CHAIN screen, press **GLOBAL** to access the page containing the **BLEND**, **ALIGN**, and **Ø B** controls.

#### Dual Chain controls

| Control | Function |
|---|---|
| **BLEND** | Adjusts the balance between signal paths A and B. |
| **ALIGN** | Adjusts the timing alignment between the two paths. |
| **Ø B** | Inverts the polarity of path B. |

**ALIGN** ranges from **−32 to +32 samples**, in single-sample increments.

- Positive values delay path A.
- Negative values delay path B.
- Adjust the value while listening to the combined signal.

The **PARAM** control remains available for normal parameter editing.

### 5.3. Scenes

**Video demonstration:** [Scenes on the GP-200](https://youtu.be/Mxq6-KZChpg)

Scenes allows you to store four additional sound states, **A–D**, within the current preset.

The original preset remains available as the base state.

#### Enable Scenes Mode

1. Open the **Footswitch** menu on the GP-200.
2. Rotate the **PARAM** knob to navigate through the available modes.
3. Select **SCENE**, which appears after USER Mode.

![Scenes mode interface](https://github.com/user-attachments/assets/a83fe754-1e95-4862-ad4d-2ab92e75261d)

#### Configure the footswitches

You can customize **FS1–FS8** as usual.

- Assign **Scene A**, **Scene B**, **Scene C**, and **Scene D** to your preferred footswitches.
- Assign **Capture** to a footswitch's **Hold** function.

#### Capture a Scene

1. Select and configure the desired preset.
2. Adjust the effect parameters, ON/OFF states, and effect chain to create the sound you want to capture.
3. Hold the **Capture** footswitch for at least **2 seconds**.
4. While holding it, press the footswitch assigned to the destination Scene (A–D).
5. The four Scene LEDs will flash for approximately **500 ms** to confirm that the capture has completed.

The LEDs then return to indicating the active Scene.

#### Save your Scenes

1. Deselect any active Scene to return to the base preset.
2. Press **SAVE** on the GP-200.
3. The first row of LEDs will flash yellow to indicate that the save operation has completed.

#### Scene behavior

- You can change an effect or the effect chain from any Scene.
- When storing a preset, parameters for replaced blocks are applied across Scenes A–D.
- Unchanged blocks are preserved.
- Each Scene retains its individual effect ON/OFF states.

#### Example

| Action | Result |
|---|---|
| Enter Scenes Mode | The base preset is active; no Scene is selected. |
| Press Scene A | Scene A becomes active. |
| Press Scene A again | Returns to the original preset state. |
| Press Scene B while Scene A is active | Switches directly from Scene A to Scene B. |

### 5.5. Native NAM A2 Lite

The custom firmware supports native execution of compatible **NAM A2 Lite** models.

Use GP200_Load_NAM_EN.html html for live loading of up to **32 NAM A2 models** 

**Only NAM A2 models are supported.**

The GP-200 runs the Lite implementation of the NAM A2 engine natively, without converting the model into a CLO/SnapTone.

#### DSP usage

NAM A2 Lite uses approximately **55% of the available DSP budget**, leaving enough processing capacity for many conventional effect chains.

However, some effects consume DSP resources even when switched off.

**Avoid including the following effects in presets that use NAM:**

| Block | Effects |
|---|---|
| **DIST** | SnapTone, Empire OD, Revolt, Bass Hammer, Flagman Dist |
| **DLY** | Broken Delay, Ice Delay |
| **RVB** | Tube Spring, Amp Spring |

These effects can reduce the available DSP headroom even when bypassed.

#### Recommended Input/Output settings

Until a complete calibration is available, the suggested starting values are:

| Parameter | Value |
|---|---:|
| **INPUT** | 36 |
| **OUTPUT** | 65 |

These values are recommended as a starting point for reproducing the raw sound of the NAM VST plugin. They are not a guarantee of level-matched results across all models.

---

## 8. Feedback, Bugs, and Suggestions

This is an ongoing experimental project, and feedback is always welcome.

If you encounter a bug, unexpected behavior, or an incompatible effect combination, please report it with as much detail as possible.

Useful information includes the firmware version, the MODs enabled, the affected preset, and the steps needed to reproduce the issue.

**Have fun, and please share your bugs, experiences, and ideas!**

[Project video and community feedback](https://www.facebook.com/share/v/1FkMth8dxY/)
