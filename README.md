# CamCandy — How to Use

For firmware **3.1.62**. CamCandy controls your camera from the flight controller
and displays camera information in your goggles.

## 1. Initial setup

- Use Ultra FC version B57 and newer. 
- Enable **MSP Protocol** on the UART connected to CamCandy.
- Enable and position **Custom Text Messages 1–4** in the FC OSD editor menu.
- Open the flight controller's **CamCandy** menu to configure the device.

## 2. Pair your camera

1. Select **GO PRO** or **DJI OSMO** under **CAMERA**.
2. Turn on your camera and enable its Bluetooth/app pairing mode.
3. Disconnect other camera controllers or phone apps. Keep other cameras off
   during pairing to avoid selecting the wrong one.
4. Select **PAIR CAMERA**. Accept any confirmation shown on the camera.
5. Wait for **CAM READY** and check the displayed camera information.

The pairing is saved. CamCandy reconnects automatically on later starts;

**PAIR CAMERA** replaces the saved camera for the selected brand. If pairing
stalls, select it again to restart the search. 
**UNPAIR CAMERA** removes that brand's saved camera and clears its information from the OSD. 
DJI and GoPro pairings are saved separately.

## 3. Choose recording control

| Trigger | Operation |
| --- | --- |
| **ARM State** | Starts recording when armed; stops when disarmed. |
| **AUX Active / Follow** | Starts when the selected AUX position becomes active; stops when it becomes inactive. |
| **AUX Toggle** | Each move into the selected AUX position toggles recording. |
| **Manual** | Use the camera's record button; CamCandy displays its information. |

For AUX control, select the channel and its **LOW**, **MEDIUM** or **HIGH** position.
AUX Toggle waits for a switch transition; if already active at startup, move it
inactive, then active.

**Manual recording is also allowed in ARM and AUX Follow modes.** Start recording
on the camera while disarmed or AUX is off. It continues through takeoff and
stops on the next disarm or AUX-off transition. While ARM/AUX Follow remains
active, CamCandy keeps recording enabled, including after a reconnect.

Before takeoff, select a video-capable mode and confirm that the camera is
recording. Landing alone does not stop recording; disarm or switch AUX Follow off.

## 4. Read the OSD

CamCandy shows camera status, recording time, video format, battery and free
storage where supported. Unavailable data is omitted.

**Example:** `4K30 4:3 UW` means 4K, 30 fps, 4:3 aspect ratio and ultra-wide lens.

- **CAM READY:** camera ready for control.
- **REC:** camera recording.
- **NO SD!:** no SD card detected on supported cameras; the warning blinks.
- **RECORD REJECTED:** camera refused the recording command; check its mode and storage.
- **DISCONNECTED:** camera link was lost.

If no camera is connected when you arm, CamCandy hides its OSD. Once a camera
has been connected during that flight, later disconnects remain visible.

## 5. Optional settings and updates

- **AUTO WAKE:** wakes supported sleeping cameras. With it off, turn the camera
  on yourself. Support varies by camera; Action 2 Auto Wake is unavailable.
- **BAT WARNING / STORAGE WARNING:** choose warning thresholds, or OFF to disable.
- **Firmware updates:** use the FC updater with `CamCandy-version.bin`.
  The full USB image is for first installation on a new/erased device and must
  not be sent through MSP. Keep power connected until the update finishes.
  Normal MSP updates retain settings and pairings.

See [tested cameras and model-specific limits](CAMERA_COMPATIBILITY.md) and
[flashing instructions](FLASHING.md).
