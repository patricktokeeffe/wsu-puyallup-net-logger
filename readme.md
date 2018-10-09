# NET Facility Logger: North Walls 7/8

## WSU Puyallup Research Extension

> Patrick O'Keeffe  
> Voiland College of Engineering and Architecture  
> Washington State University

### Work Requested

* Acquire data from recently installed sensors...
    * many point moisture measurements ([PMM Sensor; SMT Research](https://www.smtresearch.ca/product-page/point-moisture-measurement-sensor-pmm))
    * many embedded moisture sensors ([EMS Sensor; SMT Research](https://www.smtresearch.ca/product-page/embedded-moisture-sensor-ems))
    * a few rel. humidity & temperature sensors ([HTM2500; SMT Research](https://www.smtresearch.ca/product-page/relative-humidity-sensor))
* using existing datalogger infrastructure:
    * (2) microloggers ([CR10X; Campbell Scientific](https://www.campbellsci.com/cr10x))
    * (9) AM16/32A multiplexer ([AM16/32A; Campbell Scientific](https://www.campbellsci.com/am16-32a))
    * (1) datalogger ([CR1000; Campbell Scientific](https://www.campbellsci.com/cr1000))


### Current Status

* [x] Reviewed wiring diagram
    * Identifies possible typos
    * Suggests circuit revision for HTM2500 RH measurements (tie DF input low
      side to earth)
* [x] Wiring diagram reviewed by PI
    * Returned with some edits
* [x] On-site visit by PI
    * Review flagged cells... and update wiring diagram
    * Take photos of installation
    * Positively identify each MUX unit
* [ ] Fix-up sensor hardware integration
    * Per discussion with PI, most sensors are resistive (thermistors)
    * Thermistor-based sensors require additional integration circuity
      &rarr; construct resistor half-bridge
    * Multiplexers designed to read consecutive blocks of identical sensors 
      &rarr; reorganize sensor input locations

A workable approach to thermistor integration:

![Half-bridge (two-wire) thermistor integration](halfbridge_wiring.png)

Notes:
* precision resistor
    * resistive value: 10kOhm is commonly used, reduces impact of lead wire resistance
    * low tolerance: 0.02% (CSI recommended) or 0.1% (spec of Model 107 probe)
    * low temperature coefficient: no more than 5ppm/°C (CSI recommended)
* excitation voltage
    * CSI typ uses 2VAC
    * some examples used 0.5V
* temperature polynomial
    * datasheets specify Beta values.. do they also include Steinhart-Hart 
      coefficients?
    * still need to identify "*a, b species correction regression coefficients*"
      mentioned in datasheets


### Resources

* Wiring diagrams
    * [Version last updated by PI](Wiring%20Info%20for%20Yadama%20Walls.xlsx)
    * [Refactoring for thermistor inputs](Wiring%20Info%20for%20Yadama%20Walls%20(new%20MUX%20inputs).xlsx) **WIP**
* [Images of installation](images/)
* Multiplexer layout:  
  ![MUX layout](mux_layout.png)


### References

* Campbell Scientific Inc. *AM16/32A Relay Multiplexer Instruction Manual.*
  Revision Nov 2007. Online: <https://s.campbellsci.com/documents/us/manuals/am16-32a.pdf>
    * Section 6.3.1 - Half Bridge Measurement with Completion Resistor at Datalogger
* Campbell Scientific Inc. *CR10X Measurement and Control Module Operator's
  Manual.* Revision Feb 2003. Online: <https://s.campbellsci.com/documents/us/manuals/cr10x.pdf>
    * Section 7.15 - Nonelinear Thermistor in Half Bridge (Model 101 Probe)
* Campbell Scientific Inc. *Model 107 Temperature Probe Instruction Manual.*
  Revision Feb 2018. Online: <https://s.campbellsci.com/documents/us/manuals/107.pdf>
    * Section 8.1 - Sensor Schematic
    * Section 8.2 - Measurement and Output Linearization
* Campbell Scientific Inc. *Using Thermistor Temperature Sensors with Campbell
  Scientific Dataloggers.* Technical Note 15-95AS. Issued Nov 2005. Online:
  <https://s.campbellsci.com/documents/us/technical-papers/csl_thermistors.pdf>
* SMT Research Ltd. *Embedded Moisture Sensor (EMS) Datasheet.* Revision C.
  Online: <http://docs.smtresearch.ca/EMS_Datasheet.pdf>
* SMT Research Ltd. *Point Moisture Measurement (PMM) Sensor Datasheet.*
  Revision H. Online: <http://docs.smtresearch.ca/PMM_Datasheet.pdf>
* SMT Research Ltd. *Relative Humidity Sensor (HTM2500) Datasheet.* Revision B.
  Online: <http://docs.smtresearch.ca/HTM2500_Datasheet.pdf>
* Other bookmarks:
    * https://www.thermistor.com/sites/default/files/specsheets/Beta-vs-Steinhart-Hart-Equations.pdf
    * http://www.ni.com/white-paper/7112/en/
    * https://octopart.com/search?q=resistor%2010k&start=0&specs2.81.numbers=0.01&specs2.81.numbers=0.02&category_ids=6312&specs2.85.numbers=10000&specs2.495.numbers=5




