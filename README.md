# E1.L-JBOF-Concept
Concept of a 1U/2U JBOF unit using E1.L enterprise SSD form factor

---------

**Disclaimer: I'm not an engineer in this field. This is just a concept.**

---------

Publishing date: 19/06/2026

Last edited: N/A

---------

Core idea:

The core idea is to enhance the storage density in smaller formats like 1 and 2U. This idea is based off of the fact no one has built something like this to this day.
JBOF units like the Supermicro petascale are example this can work, even if their models use U.3 and U.2 SSD form factors.

Front:

In the front there are hotswap bays to easily access the drives without pulling the whole rack out like a drawer, making serviceability fast and convenient even when the unit is powered. By putting the E1.L vertically there is a potential capacity of 44 slots, accounting for hotswap bay trays and seams to let air in. In the 2U model this works the same but since it's taller there is extra space to allow for extra holes to let even more air in.

Internals:

A singular E1.L is from 9.5mm to 15mm thick, 38.4mm wide and 318.75mm long. By using the 9.5mm variant we can achieve our 44 slots layout. For cooling in the 1U layout 40mm fans would be used, while for the 2U 80mm fans would be used. Liquid cooling could also be used, but for this specific form factor and configuration it's not worth doing. As of now at least.

The backplate will be the hardest thing to design since it has to accommodate 176 PCIe lanes (1 E1.L is PCIe x4 so 44*4=176) but not completely out the realm of possibilities.

To coordinate the PCIe lanes either PCIe switches or DPUs (Data Processing Unit), depending on the unit's intended purpose.

For power I'd use a 2+2 configuration (2 PSUs are on, 2 PSUs are on stand-by) and 1000w CRPS, to ensure stable and reliable power delivery. The use of multiple 1000w PSUs is due to the fact that an E1.L 9.5mm SSD can draw up to 25w, plus we have to account for other internal components like fans and various chips and switches.
To grant even more protection I'd also suggest the option to use 1-2 small batteries to use as UPS (Uninterrupted Power Supply) to have extra time to safely shut off the unit in case of an emergency, if a UPS isn't available or for small power outages that could damage the hardware if a UPS was absent.
The battery/batteries would be located at the back near the CRPS modules to allow serviceability and replace them in the event one was failing due to age, use or other factors.

Connection:

I'd reccomend using 2-6 QSFP-DD modules, so that the module inside can be changed depending on needs. This covers anywhere from 100GbE to 800GbE. Alternatively standard RJ45 and SFP+ can be used to ensure connectivity with other systems lacking QSFP ports.

Data density:

Thanks to SSDs like the Solidigm D5-P5336 a capacity of 5.4PB per unit can be reached (122.88TB per SSD), though it's only for Gen.4 PCIe. For more IOPS the D7-P5520 is the alternative, however it has a limit of 15.36TB per unit so the total comes out to 675.8TB per unit.

Conclusion:

The 1U variant is made for maximum density with minimal footprint, while the 2U variant is a versatile option with the added benefit of better airflow.

---------

Links:

Solidigm D5-P5336: https://www.solidigm.com/products/data-center/d5/p5336.html#form=E1.L%209.5mm&cap=122.88TB

Solidigm D7-P5520: https://www.solidigm.com/products/data-center/d7/p5520.html#form=E1.L%209.5mm&cap=15.36TB

Supermicro petascale: https://www.supermicro.com/en/products/jbof

My other repo: https://github.com/Monster-Head/High-density-JBOF-server-racks-concept-for-AI-and-Hyperscalers

---------

## License

This work is licensed under a [Creative Commons Attribution-NonCommercial 4.0 International License](https://creativecommons.org/licenses/by-nc/4.0/).

[![CC BY-NC 4.0](https://mirrors.creativecommons.org/presskit/buttons/88x31/png/by-nc.png)](https://creativecommons.org/licenses/by-nc/4.0/)
