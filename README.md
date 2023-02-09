# Energy monitoring (with Iammeters) setup with Home Assistant

Full details of my energy management in Home Assistant, with Iammeter meters.

## Local energy provider setup

My provider has three time of use tariffs - off-peak, shoulder and peak. Off-peak runs from 10pm to 8am, shoulder (am) from 7am to 4pm, peak from 4pm to 8pm, shoulder (pm) from 8pm to 10pm. I get a small 'feed-in tariff' (AU$0.08/kWh) for energy returned to the grid (this is capped by my energy provider at a rate of 5kW, set and controlled by my inverter, which has its own smart meter on the grid feed line).

I have a WEM3080T and a WEM3080, setup as follows:

WEM3080T:
- A: CT clamp on hot water circuit
- B: CT clamp on inverter feed
- C: CT clamp on air conditioning circuit
WEM3080:
- CT clamp on main grid feed

Make sure clamps are correctly aligned. Inverter feed should result in +ve power flow when panels are producing power; and grid feed should be +ve when drawing from the grid (i.e. power inbound to your home is +ve).

I have 13.3kW of solar panels, connected to a GE 10kW hybrid inverter (GoodWe device, sold under GE brand)
No battery at the moment, so 'solar energy' = 'inverter in energy', but I am altering sensors to allow for accurate tracking of battery energy charging (potentially from grid or solar) and discharging, in which case 'energy from inverter' + 'solar energy to battery' = 'solar energy', so the sensor definitions are changing to reflect that.

## Helpers

- input_text.utility_current_electricity_tou_band
- input_datetime.utility_electricity_tou_am_shoulder_on
- input_datetime.utility_electricity_tou_pm_offpeak_on
- input_datetime.utility_electricity_tou_pm_peak_on
- input_datetime.utility_electricity_tou_pm_shoulder_on
- input_number.utility_electricity_fit_rate
- input_number.utility_electricity_supply_fee
- input_number.electricity_offpeak_rate
- input_number.electricity_peak_rate
- input_number.electricity_shoulder_rate
- input_number.supply_charge

## Sensors

- A set of sensors from the Iammeters, e.g. ```sensor.iammeter_1_modbus_importenergy```
- A set of filtered power sensors for when the above are unavailable, unknown or none, e.g. ```sensor.inverter_power```
- 

## Energy Dashboard

Extract of dashboard, noting that several of the views are incomplete or work in progress.

The dashboard uses conditional cards and apexcharts. The conditional cards drive the colours for the different time of use rates/tariffs.

![image](https://user-images.githubusercontent.com/8214128/217789249-0c899624-baef-44b6-8d44-9b9f574c7bac.png)
