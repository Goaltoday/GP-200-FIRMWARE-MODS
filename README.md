# Custom_Firmware_0.1 — GP-200 README

> **Experimental modification. Use at your own risk.** No warranty or support claims are accepted for this modification.

## 1. What the HTML does

`Custom_Firmware_0.1.html` is a browser-based firmware configurator. Open it on a computer, select a GP-200 firmware BIN, choose and configure MODs, then generate a ZIP containing the modified firmware and any accompanying files. The HTML itself is not installed on the pedal; the BIN inside the ZIP is the firmware image to install.

- The generator supports GP-200 firmware versions **1.8.0 and 1.8.2**. Use a BIN that matches the firmware profile you intend to prepare.
- The generator may recognize and preserve certain existing MODs. If it reports an unrecognized, partial, or incompatible image, stop and check the BIN; do not force the operation.
- The CHAIN MOD changes the GP-200 firmware interface. **CHAIN can only be edited on the GP-200** and does not require official-editor file replacement.

## 2. Before you start

- Prepare source files in advance: mono WAV files for CAB IRs and compatible CLO/Sound Clone files for AMP replacements.
- Use a desktop browser and keep the downloaded ZIP intact until you have read its manifest and contents.
- Back up your presets.
- Back up the official editor files before replacing any of them.

## 3. Open the HTML and load a BIN

1. Make sure the generator file is named `Custom_Firmware_0.1.html`.
2. Open it in a desktop browser, by double-clicking the file or using the browser’s **Open File** command. Do not open it in a text editor to run it.
3. Under **Load your firmware BIN**, select the `.bin` for the profile you intend to use.
4. Wait for the compatibility check. MOD controls become available after a recognized image is loaded. If the page reports an incompatible or unrecognized BIN, stop and verify the file and profile.
5. Select only the MODs you want to include in this build, then configure their options.

The generator processes the selected firmware in the browser and checks the image and recognized MOD state before enabling generation.

## 4. Configure the MODs

### 4.1 Factory CAB → Custom IR

Open **Replace Factory CAB and AMP**, then **Configure CAB and AMP**. The list contains 70 Factory CAB destinations. For each CAB to replace:

- Select a mono WAV at **44.1 kHz**. The generator writes the IR as **1024 samples**.
- Optionally enter a display name, up to **12 ASCII characters**.
- Check that the file and name appear on the intended CAB row.

A replacement is associated with the Factory CAB slot, so presets using that slot will use the replacement IR.

### 4.2 Factory AMP → SnapTone/CLO

In the same section, select a Factory AMP destination, choose its compatible Sound Clone/CLO file, enter a display name if desired, then click **Add Sound Clone**. Any of the 71 Factory AMP destinations can be selected, up to a total of **18 replacements** in one build.

- AMP models not selected keep their original sound.
- Follow the character limit shown on the page for the display name.
- Model slots use PCM sample regions associated with Drum Machine banks that the firmware identifies as unused. The Drum Machine routine is retained, but pattern preservation still needs confirmation on the pedal.

### 4.3 Effects on the PRE block

Enable **Load effects on PRE Block** and open **Configure PRE effects**. The page offers 15 PRE assignments. For each slot, choose a compatible replacement from its list or keep the original effect.

- Each list is limited to effects supported by that slot.
- Delay and Reverb choices are marked experimental in the configurator.
- The MOD reuses existing PRE packages and does not reserve a new model bank.

### 4.4 DUAL CHAIN · parallel routing

Enable **DUAL CHAIN** to add two signal paths, A and B, with a BLEND control. All DUAL CHAIN operation and editing described here take place on the GP-200:

1. On the GP-200, open **FX Loop** and select **CHAIN** to use parallel routing.
2. To change the effect order, press and hold **PARAM** on an effect, then use the pedal’s native reorder workflow.
3. On the CHAIN screen, press **GLOBAL** to switch to the page containing **BLEND**, **ALIGN**, and **Ø B**. PARAM remains the parameter-edit control.
4. ALIGN ranges from **−32 to +32 samples** in one-sample steps. Positive values delay path A; negative values delay path B. Adjust it while listening.
5. Ø B inverts path B polarity. BLEND sets the balance between A and B.

> **CHAIN boundary:** Do not replace official-editor files for CHAIN. CHAIN routing and its BLEND, ALIGN, and polarity settings are edited on the GP-200 itself.

## 5. Replace official-editor files for CAB, AMP, and PRE

Some generated ZIPs include replacement resources for the official GP-200 editor for MODs other than CHAIN. These resources are separate from the firmware BIN and do not install a MOD on the pedal by themselves. Use them only for CAB/IR, AMP/SnapTone, or PRE, and only when the package identifies them as editor files.

1. Extract the generated ZIP to a new folder. Read the manifest and included instructions, then identify the files explicitly listed for the official editor.
2. Close the official editor. Back up every original file that will be replaced.
3. Copy only the listed replacement files into their corresponding locations, preserving the folder structure and filenames.
4. Do not copy CHAIN files into the official editor. Do not replace unrelated files or mix resources from different firmware builds.
5. Reopen the official editor and check the relevant CAB, AMP, or PRE names and options. If they do not match the generated firmware, restore the backup and verify the package and profile.

> **Important:** Follow the exact file list and paths in the generated package. If it contains no editor replacements or clear instructions, do not guess which installed files to overwrite. Keep the originals so you can restore them.

## 6. Generate and install the firmware

1. Click **Build and download firmware** and wait for completion. Keep the page open while the build runs.
2. Download the ZIP and extract all of it. Keep the BIN, manifest, and any editor resources together.
3. Record the input BIN, profile, selected MODs, HTML filename, and SHA-256 of the generated BIN. Use the manifest to identify the build.
4. Install the generated BIN using Valeton’s official GP-200 firmware update procedure for the matching firmware version.
5. Do not disconnect or interrupt the pedal during the firmware update. Afterward, confirm that it starts normally and test each selected MOD.

## 7. Basic post-install checks

| MOD | Check on the GP-200 |
|---|---|
| CAB / IR | Open a preset using the replaced CAB; check its name and listen. |
| AMP / CLO | Check the destination, name, and sound; then check Drum Machine operation and patterns. |
| PRE | Check the selected effect, its parameters, and bypass. |
| DUAL CHAIN | Check CHAIN, effect order, A/B paths, GLOBAL/PARAM, BLEND, ALIGN, Ø B, tap tempo, preset changes, and restart. |

