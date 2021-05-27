# ecmc_target_muts_logger
Logger for target tests at ESS MUTS and FAT at ESS Bilbao (Galicia).

The crate can be used to accuire the following data:
1. Dispalcements of rotor by 4 sensors
2. Encoder signal
3. Phase error

## Hardware

### Electrical connections

IMPORTANT: Make sure the measurement box and the measurement object are grounded.

### Ethercat hardware

```
$ ethercat slaves
0  0:0  PREOP  +  EK1100 EtherCAT-Koppler (2A E-Bus)
1  0:1  PREOP  +  EL5021 1Ch. Sin/Cos Encoder
2  0:2  PREOP  +  EL3174-0002 4K. Ana. Eingang  +/-10V, +/-20mA, 16 Bit, Galvanis
3  0:3  PREOP  +  EL9505 Netzteilklemme 5V
4  0:4  PREOP  +  EL1252-0050 2K. Fast Dig. Eingang 5V, 1�s, DC Latch
```

### Encoder

AMO encoder should be conneted to the black cable with heidenhain connector. This is interbally conencted to EL5021 (slave 1). 

### Telemess sensors

In total 4 Telemess distance sensors should be connected to the box:

Item | Serial No. | Position [deg] | Range [mm] | Description
---  | ---        | ---            | ---        | --- |
1    | 33020      | 0              | 0..15      | Telemess displacement sensor 1
2    | 33021      | 120            | 0..15      | Telemess displacement sensor 2
3    | 33018      | 240            | 0..15      | Telemess displacement sensor 3
4    | 32900      | vertical       | 0..20      | Telemess displacement sensor 4

Note: It's important that the sensor are connected to the correct cable of the box since the amplifiers are calibrated to the sensors.

The telemess sensors are connected internally to an EL3174-002 (slave 2).

Values are then accessed in the follwoing records (scaled in mm):
```
IOC_TEST:ec0-s2-EL3174_0to10V-AI1
IOC_TEST:ec0-s2-EL3174_0to10V-AI2
IOC_TEST:ec0-s2-EL3174_0to10V-AI3
IOC_TEST:ec0-s2-EL3174_0to10V-AI4
```

### Phase error measurement

NOTE: Phase error measurement is only possible if access to the ESS timing system. Therefore this functionality will only be used at ESS MUTS tests and not at Galicia.

The EL1252-0050 (timestamped 5V I/O) is used to measure phase error.
* Input1: Photocell (if 24V signal then it needs a resitor divider or a optcoupler), the crate is currentlly equipped with resistor divider.
* Input2: Timing system TTL output

WARNING: The EL1252-0050 is a 5V terminal and will break if a 24 V signal is connected.

The phase is calculated as the difference between the two timestamps by a ecmc plc. Phase errors bigger than 20mm will be filtered away by the plc.

## Start IOC

Note: Require version 3.4.0

First step is to source of E3 environment:

```
$ . ~/epics/base-7.0.5/require/3.4.0/bin/setE3Env.bash 
Set the ESS EPICS Environment as follows:
THIS Source NAME    : setE3Env.bash
THIS Source PATH    : /home/dev/epics/base-7.0.5/require/3.4.0/bin
EPICS_BASE          : /home/dev/epics/base-7.0.5
EPICS_HOST_ARCH     : linux-x86_64
E3_REQUIRE_LOCATION : /home/dev/epics/base-7.0.5/require/3.4.0
PATH                : /home/dev/epics/base-7.0.5/require/3.4.0/bin:/home/dev/epics/base-7.0.5/bin/linux-x86_64:/opt/conda/condabin:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin:/home/dev/.local/bin:/home/dev/bin
LD_LIBRARY_PATH     : /home/dev/epics/base-7.0.5/lib/linux-x86_64:/home/dev/epics/base-7.0.5/require/3.4.0/lib/linux-x86_64

Enjoy E3!
```

Start IOC:
```
$ cd iosch
$ iocsh.bash start_ioc.script
```

## Intresting PVs

Item | Prefix   | Pv name                        | Description
--- | ---       | ---                            | --- |
1   | IOC_TEST: | ec0-s1-EL5021-PosAct           | AMO SinCos encoder terminal Actual position (Amo encoder) [raw counts]
2   | IOC_TEST: | ec0-s2-EL3174_0to10V-AI1       | Telemess displacement sensor 1 (0deg)  0..15 [mm]
3   | IOC_TEST: | ec0-s2-EL3174_0to10V-AI2       | Telemess displacement sensor 2 (120deg) 0..15 [mm]
4   | IOC_TEST: | ec0-s2-EL3174_0to10V-AI3       | Telemess displacement sensor 3 (240deg) 0..15 [mm]
5   | IOC_TEST: | ec0-s2-EL3174_0to10V-AI4       | Telemess displacement sensor 4 (vertical) 0..20 [mm]
6   | IOC_TEST: | ec0-s4-EL1252-CH1-PosTime-Act  | Photecell timestamp positive edge [ns]
7   | IOC_TEST: | ec0-s4-EL1252-CH1-NegTime-Act  | Photecell timestamp negative edge [ns]
8   | IOC_TEST: | ec0-s4-EL1252-CH2-PosTime-Act  | Timing system timestamp positive edge [ns]
9   | IOC_TEST: | ec0-s4-EL1252-CH3-NegTime-Act  | Timing system timestamp negative edge [ns]
10  | IOC_TEST: | FFT-0                          | FFT for rotational encoder (AMO)
11  | IOC_TEST: | FFT-1                          | FFT for Telemess displacement sensor 1 (0deg)
12  | IOC_TEST: | FFT-2                          | FFT for Telemess displacement sensor 2 (120deg)
13  | IOC_TEST: | FFT-3                          | FFT for Telemess displacement sensor 3 (240deg)
14  | IOC_TEST: | FFT-4                          | FFT for Telemess displacement sensor 4 (vertical)

All accessible PVs are listed in: [PVs](./iocsh/pvs.log)

## FFTs

The analog displacement sensors are linked fft plugins:
https://github.com/anderssandstrom/e3-ecmc_plugin_fft

The spectras can be viewed with a dedicated GUI through ecmccomgui by entering the below prefix and pv name: 

Item | Prefix    | Pv name                        | Description
---  | ---       | ---                            | --- |
1    | IOC_TEST: | FFT-0                          | FFT for rotational encoder (AMO)
2    | IOC_TEST: | FFT-1                          | FFT for Telemess displacement sensor 1 (0deg)
3    | IOC_TEST: | FFT-2                          | FFT for Telemess displacement sensor 2 (120deg)
4    | IOC_TEST: | FFT-3                          | FFT for Telemess displacement sensor 3 (240deg)
5    | IOC_TEST: | FFT-4                          | FFT for Telemess displacement sensor 4 (vertical)


### Settings
The signales are scaled in the FFT plugin to [mm]. So the resulting spectra and rawdata is then also in [mm]. By default the system samples data in 1kHz for 10 revs at 36/14 Hz speed (25714 values). 

### GUI

Note: Use ecmccomgui_py36 to activate python env for ecmccomgui

The ecmccomgui can be used to view the FFT results: https://github.com/anderssandstrom/ecmccomgui
