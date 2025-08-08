# OpenVR OSC Unreal
> Easily track pose data from OpenVR devices via OSC, especially to Unreal Engine projects.

OpenVR OSC is a compact Python utility for tracking OpenVR devices (HMDs, controllers, trackers) and getting their position and rotation values over OSC. It can be used in VR as well as AR and any other position-based project and fed to any OSC-capable client. This fork contains adjustments to accommodate the differences between the coordinate systems of SteamVR and Unreal Engine.

This project is inspired by and used Triad's [Python OpenVR wrapper](https://github.com/TriadSemi/triad_openvr).

## Setup

### Requirements

This project requires Python `3` to run as dependencies are incompatible with Python `2.7`.
It also required an existing OpenVR installation (SteamVR etc.) and compatible hardware (HTC Vive etc.).

### Installation

To install the project dependencies run `pip install -r requirements.txt`.

## How to use

To run OpenVR-OSC Unreal enter the following in your terminal:
  `python3 openvr-osc-unreal.py`

### Tracked devices

The following devices are tracked and sent via OSC:
- headsets (HMDs, excluding the SteamVR null driver for 'headless VR')
- controllers
- tracker units
The OSC messages sent are formated in as follows:
 `\{DEVICE_ID} - [f,f,f,f,f,f]`

### OSC message format

Each message contains multiple float values in an order set by the `pose mode`:

In `Euler` mode:
- x position
- y position
- z position
- yaw
- pitch
- roll

In `Quaternion` mode:
- x position
- y position
- z position
- qx
- qy
- qz
- qw

Each tracking cycle is sent as a bundle of individual messages, per device, that are time synced.

### Configuration options
There are several configuration options to customize the OSC feed and the tracking

<details>
  <summary>OSC server ip</summary>
  
  Set the ip of the OSC server - `--ip 169.78.65.21`
  Defaults to `127.0.0.1 (localhost)`.
</details>

<details>
  <summary>OSC server port</summary>
  
  Set the port of the OSC server - `--port 5000`
  Defaults to `7000`.
</details>

<details>
  <summary>tracked device type</summary>
 
  By default all device types are tracked but that can lead to unnecesary OSC traffic.
  If you know which device type you'd like to track (HMD, controllers, trackers), you can limit the tracking:
  
  `--track=[hmd|controller|tracker]`
</details>

<details>
  <summary>tracking frequency (in ms)</summary>
 
  `--track=[hmd|controller|tracker]`
</details>

<details>
  <summary>pose mode</summary>
 
    `--mode [euler|quaternion]`
  </details>

## Using SteamVR without a headset

To use the trackers and controllers without the need for a headset follow in the instructions in [this tutorial](http://help.triadsemi.com/steamvr-tracking/steamvr-tracking-without-an-hmd).

## Roadmap

- [ ] period check for device state and new tracked devices


> Made at ITP NYU


