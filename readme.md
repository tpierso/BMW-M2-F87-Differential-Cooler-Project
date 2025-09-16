# 2018 BMW M2 Differential Cooler Build

> [!NOTE]
> **DISCLAIMER**
> 
> This Sample is provided for the purpose of illustration only and is
not intended to be used in a production environment.  
THIS SAMPLE AND ANY RELATED INFORMATION ARE PROVIDED AS IS WITHOUT
WARRANTY OF ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT
LIMITED TO THE IMPLIED WARRANTIES OF MERCHANTABILITY ANDOR FITNESS
FOR A PARTICULAR PURPOSE.
>
> We grant You a nonexclusive, royalty-free
right to use and modify the Sample and to reproduce and distribute
the object form of the Sample, provided that You agree
(i) to not use Our name, logo, or trademarks to market Your software
product in which the Sample Code is embedded; (ii) to include a valid
copyright notice on Your software product in which the Sample is
embedded; and (iii) to indemnify, hold harmless, and defend Us and
Our suppliers from and against any claims or lawsuits, including
attorneys' fees, that arise or result from the use or distribution
of the Sample.

> [!WARNING]
> This project is still a work in progress. I will be actively updating this as time goes on. 
## Summary
This is a differential cooler build for the BMW M2 F87. The idea was to create a more cost effective and usable solution for F8x road cars looking to implement a cooling configuration similar to the BMW M4 GT4 and BMW M2 CS Racing respectively. 

## Why not just use the M4 GT4 and M2 CS Racing off the shelf products?
While the M2 CSR and M4 GT4 give a good template to start from, there are a few issues with this in particular for the F87 road cars: 
  1. The CSR uses a side window vent to flow air into the inlet box for the radiator, which would mean moving away from the stock safetyglass window, increasing NVH, and also would require cutting and welding of the trunk area. 
  2. The M4 GT4 and CSR trigger the oil pump using the differential temperature probe in the bottom of the sump. This sends a signal that then goes to the FEM to power on the oil pump. The FEM on both cars are actually off the shelf units; however, those units are reprogrammed using MiDiS (BMW Motorsports Diagnostics) and thus this wasn't viable in my opinion.
  3. The BMW parts are natually more expensive than going your own way (although, over time this has proven not to be the case).

### Goals
  - Create a differential cooler that integrates more cleanly without cutting up too much of the car or increasing complexity massive lengths.
  - Trigger pump on after gear oil has reached temperature to increase pump life
  - Implement a quick connect fitting to ease maintenance and gear oil changes.
  - Integrate a long lasting solution that fits nicely under the car.

### Decided strategy
> [!NOTE]
> I am running a Drexler LSD and no longer have the OEM electronic differential or servo motor. 
  1. Use the M2 CSR to mount the oil cooler.
  2. Use a small oil cooler puller fan to augment the fact that we won't be using direct, efficient air cooling from the side window like the CSR.
  3. Integrate a thermal switch in the loop to ensure the pump and fan only power on as needed and when oil is at the desired operating temperature
     > The CSR activates its pump via the FEM at 170F; however, there aren't commercially available thermal switch that is useful here. I decided on a 180F Setrab M12x1.5 unit that fits into the factory temp sensor location on the oil sump and also have provisions for another temp location via a fitting after my oil pump via a AN6 female to male adapter with a 1/8 NPT that will test as well.
  4. Use a quick disconnect for ease of maintenance.
  5. Don't cheap out on components (especially in electrical).
  6. Reduce complexity, but err on the side of reliability and performance.

## Architecture
### Simplifed Cooling Loop
  1. An M22x1.5 banjo bolt fits directly into the stock differential oil sump outlet.
  2. From the M22-AN6 banjo fitting, the gear oil flows to a female AN6 to female AN6 hose.
  3. From the AN6 hose, the gear oil flows to quick disconnect fitting (optional).
  4. From the quick disconnect, the gear oil flows to a 150 micron AN6 male to AN6 male in-line filter.
  5. From the in-line filter, the gear oil then flows through the oil pump.
  6. From the oil pump, the gear oil flows to the inlet of the oil cooler.
  7. From the outlet of the oil cooler, the oil then flows back into the differential inlet.

Per BMW, the Mocal oil pump will come under serious load and reduce the longevity of the pump if cold gear oil is pumped through the s

## Parts order

| **Part Name** | **Quantity** | **Notes** |
|---|---|---|
| Mocal 25-Row, 235 Matrix Cooler | 1 | Setrab 6 235 Row alternatively works|
| Mocal EOP2 Oil Pump | 1 | Other brands may work, but just validate they work with thicker gear oil |
| Improved Racing 25 Row Oil Cooler Fan Bracket | 1 | |
| SPAL 6.5" Cooling Fan (pull)| 1 | Not neccessary, but adds additional cooling efficiency |
| Bosch 30A ISO 280 Micro Relays | 2 | Not neccessary, but adds additional protection |
| Eaton 15305-4-0-4 | 1 | Not neccessary, but makes for a cleaner install and can be mounted externally | 
| Setrab sūsa In-Line Pump Pre-Filter, AN6 Male-AN6 Male, 150µ | 1 | The Setrab inline 3/8 BSP to AN6 male pump collides with the pump housing |
| Setrab sūsa ProLine Banjo Fitting M22 to AN6 Male | 1 | This unit requires disassemble the fitting to fit the socket. Also requires a 27mm socket |
| Setrab sūsa ProLine Adapter Fittings - M22 to AN6 - 45 Degree | 1 | | 
| Mocal BSP 3/8 male to AN6 male | 2 | I would recommend going with the Mocal brand here to ensure the nut end doesn't collide with the pump housing |
| Vibrant Dry Break Quick Release Adapter Fitting AN6 | 1 | This is optional, but it makes maintenance easy if you have another dry break | 
| Setrab sūsa AN Union - 90 degree AN6 female to AN6 female | 1 | |  
| Setrab ūsa AN Union - straight AN6 female to AN6 female | 1 | | 
| Raceflux Custom -6AN PTFE SS hoses | 3 | Details below of construction; I didn't feel like making the hoses myself |
| KSV Looms/Prowire USA M22759/32-12 Wiring | 5 | 5 corresponds to the number of wire colors selected. Specific wiring lengths to come with harnessing docs. | 
| Deutsch DTP04 Full Kit 12-14 AWG gold plated terminals | 1 | Prowire USA sells these as a kit. Totally overkill, but buy once, cry once. | 
| Deutsch DTP02 Full Kit 12-14 AWG gold plated terminals | 2 | Prowire USA sells these qas a kit. Totally overkill, but buy once, cry once. | 

## Wiring and hose dimensions

| **Part name** | **Size** | **Length (seat-to-seat)** | **Quantity** | **Fitting/Terminal 1** | **Fitting/Terminal 2**| Install Location | **Notes** |
|---|---|---|---|---|---|---|---|
| Raceflux SS braided PTFE AN Custom Hose | AN6 | 15" | 1 | 45 degree AN6 female fitting | 45 degree AN6 female fitting | Oil Pump to Radiator In | 1/2 Silicone Fiberglass fire sleeve for whole line length |
| Raceflux SS braided PTFE AN Custom Hose | AN6 | 12" | 1 | Straight AN6 female fitting | Straight AN6 female fitting | Diff outlet to Dry Break | 1/2 Silicone Fiberglass fire sleeve for whole line length |
| Raceflux SS braided PTFE AN Custom Hose | AN6 | 46" | 1 | Straight AN6 female fitting | Straight AN6 female fitting | Radiator Out to diff in| 1/2 Silicone Fiberglass fire sleeve for whole line length | 
