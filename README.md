# MDPI LoRaWAN Path Loss Dataset including Environmental Variables
This dataset includes a measurement campaign for LoRaWAN End Nodes measuring path loss and environmental variables. For this end, we have deployed a LoRaWAN network in Medellín, Colombia, for four months, as shown in Fig 1:

![alt text](https://github.com/magonzalezudem/MDPI_LoRaWAN_Dataset_With_Environmental_Variables/blob/main/Architecture.png)
### Fig 1. LoRaWAN Architecture

Four End Nodes (ENs) are deployed at different distances, from 2 to 8 km, and connected to a LoRaWAN Gateway (GW).The GW serves as a relay to resend the information to a Network Server (The Things Network). Subsequently, the Network Server exposes an MQTT broker (MQTT: Message Queue Telemetry Transport). Finally, we coded a database server which includes an MQTT consumer that captures the information sent by the ENs, and then, it stores the corresponding data into a MySQL database. Our database includes 990750 observations from October 2021 to March 2022. The sample rate is about 15 seconds.

The measurement campaign includes the following fields:

### Row identification
- **row_number**: A sequential number from 1 to 990750
- **timestamp**: The date and time field for the current measurement
- **device_id**: The name of the EN that corresponds to the current measurement
### Physical/geometric conditions
- **distance**: The distance between the EN and the GW in meters
- **ht**: Antenna height of the EN in meters
- **hr**: Antenna height of the GW in meters
### Link budget features
- **ptx**: Transmitter (EN) radio power in dBm
- **ltx**: Transmitter (EN) losses associated to cables and connectors in dB
- **gtx**: Transmitter (EN) antenna gain (characterized with a Vector Network Analyzer) in dBi
- **lrx**: Receiver (GW) losses associated to cables and connectors in dB
- **grx**: Receiver (GW) antenna gain (characterized with a Vector Network Analyzer) in dBi
- **frequency**: Carrier frequency in Hz
- **frame_length**: Number of bytes of the current transmission
### Environmental variables
- **temperature**: Environment temperature of the current measurement in °C
- **rh**: Relative humidity of the current measurement in %
- **bp**: Barometric pressure of the current measurement in hPa
- **pm2_5**: Particulate matter of the current measurement in ug/m3
### Received signal strength and channel signal to noise ratio
- **rssi**: Received signal strength indicator in the GW in dBm
- **snr**: Channel signal to noise ratio in dB
- **toa**: Time on air of the current transmission in seconds
### Calculated path loss and energy
- **experimental_pl**: Experimental path loss calculated by ptx+gtx-ltx+grx-lrx-rssi
- **energy**: Consumed energy in current transmission in Joules
- **mean_pl**: Mean path loss at each distance in dB
- **friis**: Path loss estimated using the Friis model in dB
- **trplm**: Path loss estimated using the Two-ray approach in dB
- **splm**: Simplified path loss model or log-distance empirical model estimation in dB
- **okumura-hata**: Path loss estimated using the Okumura-Hata approach in dB

This dataset can be used to estimate the impact of the weather changes in path loss for LoRaWAN deployments, and get more accurate tracking/positioning data or more efficient energy reduction strategies.
