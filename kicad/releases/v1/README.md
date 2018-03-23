# basic-lm399 v1

This board was designed to be a basic "utility" board for working with the [LM399](http://cds.linear.com/docs/en/datasheet/199399fc.pdf).  Some features which support versatiliy:

- This board supports the use of either single or dual-package DIP-8 op amps (whatever you have on hand!)
- Multiple supply connection options (barrel jack, terminal blocks, or header pins)
- The LM399 footprint supports using a 2x2 header socket, so that LM399's can be quickly swapped and compared.
- For the single op amp footprint, input offset voltage trimming circuitry footprints are included (which could be used to make a temporary small adjustment to the final output voltage).

This board's dimensions are under 50mm x 50mm, which means it fits in the cheapest pricing tier of most board manufacturers (e.g., in case you'd like to spin a bunch of these boards for bulk LM399 ageging).


## The Circuit

Full schematic: [pdf](trivial-lm399.pdf)

This board uses the basic "bootstrapped zener" concept:

![](media/bootstrapped-zener.png)

Here's the actual implementation:

![](media/basic-circuit.png)


## Single op amp configuration

To use this board with a single op amp, populate the `U1` op amp and leave `U3` op amp unpopulated.

Because most single op amps are pin-compatible, this configuration can be used with a number of DIP-8 op amps, e.g.:
- OP07
- LT1001
- TL061, TL071, TL081
- uA741



## Dual op amp configuration


## Start-up issues

With an ideal op amp, this circuit actually has two stable configurations:
- Nominal (7V) output
- 0V output

That is, if the output pin were very slightly negative at start-up, and a rail-to-rail op amp was used, the output could "stick" at 0V and be stable there.

One way to solve this issue is to tie a very high value resistor from output to Vcc, so that some current always flows through the zener, keeping the output positive at all times.

The other way to solve this is to use an op amp which cannot go all the way to 0V output when used in a single-supply configuration (i.e., not a rail-to-rail op amp).  The OP07 fits this bill nicely, is fairly precision, and is cheap, so it fits this circuit well.  The LT1001 (which is used in the LM399 datasheet circuits) is essentially Linear Tech's upgraded version of the OP07.
