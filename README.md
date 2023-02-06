# Iammeter setup with Home Assistant

Full dump of my energy management in Home Assistant, with Iammeter meters.

I have a WEM3080T and a WEM3080, setup as follows:

WEM3080T:
- A: CT clamp on hot water circuit
- B: CT clamp on inverter feed
- C: CT clamp on air conditioning circuit

WEM3080:
- CT clamp on main grid feed

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
