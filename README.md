# ecmc_target_muts_logger
Logger for target MUTS tests.
Will be used to log:
1. dispalcements of rotor by 4 sensors
2. encoder signal
3. Phase error

## Hardware

```
$ ethercat slaves
0  0:0  PREOP  +  EK1100 EtherCAT-Koppler (2A E-Bus)
1  0:1  PREOP  +  EL5021 1Ch. Sin/Cos Encoder
2  0:2  PREOP  +  EL3174-0002 4K. Ana. Eingang  +/-10V, +/-20mA, 16 Bit, Galvanis
3  0:3  PREOP  +  EL9505 Netzteilklemme 5V
4  0:4  PREOP  +  EL1252-0050 2K. Fast Dig. Eingang 5V, 1�s, DC Latch
```

### Encoder
AMO encoder should be conneted to EL5021 (slave 1)

### Telemess sensors
Telemess sensors should be connected to EL3174-002 (slave 2)
Channel 1..3 is used for the three sensors with a range of 0..15mm.
Channel 4 is used for the sensor with a range of 0..20mm.

The values in the following records are scaled in mm
```
IOC_TEST:ec0-s2-EL3174_0to10V-AI1
IOC_TEST:ec0-s2-EL3174_0to10V-AI2
IOC_TEST:ec0-s2-EL3174_0to10V-AI3
IOC_TEST:ec0-s2-EL3174_0to10V-AI4
```

### Phase error measurement
The EL1252-0050 (timestamped 5V I/O) is used to measure phase error.
* Input1: Photocell (if 24V signal then it needs a resitor divider or a optcoupler)
* Input2: Timing system TTL output

WARNING: The EL1252-0050 is a 5V terminal and will break if a 24 V signal is connected.

The phase is calculated as the difference between the two timestamps by a ecmc plc. Phase errors bigger than 20mm will be filtered away by the plc.

## Start ioc

Note: Require version 3.4.0

Note: Use ecmccomgui_py36 to activate python env for ecmccomgui
```
$ cd iosch
$ iocsh.bash start_ioc.script
```
## Intresting PVs

Item | Prefix| Pv name | Description
--- | --- | --- | --- |
1 | IOC_TEST: | ec0-s1-EL5021-PosAct  | AMO SinCos encoder terminal Actual position (Amo encoder) [raw counts]
2 | IOC_TEST: | ec0-s2-EL3174_0to10V-AI1  | Telemess displacement sensor 1 0..15 [mm]
3 | IOC_TEST: | ec0-s2-EL3174_0to10V-AI2  | Telemess displacement sensor 2 0..15 [mm]
4 | IOC_TEST: | ec0-s2-EL3174_0to10V-AI3  | Telemess displacement sensor 3 0..15 [mm]
5 | IOC_TEST: | ec0-s2-EL3174_0to10V-AI4  | Telemess displacement sensor 4 0..20 [mm]
6 | IOC_TEST: | ec0-s4-EL1252-CH1-PosTime-Act  | Photecell timestamp positive edge [ns]
7 | IOC_TEST: | ec0-s4-EL1252-CH1-NegTime-Act  | Photecell timestamp negative edge [ns]
8 | IOC_TEST: | ec0-s4-EL1252-CH2-PosTime-Act  | Timing system timestamp positive edge [ns]
9 | IOC_TEST: | ec0-s4-EL1252-CH3-NegTime-Act  | Timing system timestamp negative edge [ns]

All accesible PVs are listed in: [PVs](./iocsh/pvs.log)

## FFTs
The analog displacement sensors are linked fft plugins:
https://github.com/anderssandstrom/e3-ecmc_plugin_fft

### Settings
The signales are scaled in the FFT plugin to [mm]. So the resulting spectra and rawdata is then also in [mm]. By default the system samples data in 1kHz for 10 revs at 36/14 Hz speed (25714 values). 

### GUI
The ecmccomgui can be used to view the FFT results: https://github.com/anderssandstrom/ecmccomgui

