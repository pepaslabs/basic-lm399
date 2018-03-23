# basic-lm399 v1

This board was designed to be a basic "utility" board for working with the [LM399](http://cds.linear.com/docs/en/datasheet/199399fc.pdf).  Some features which support versatiliy:

- This board supports the use of either single or dual-package 8-DIP op amps (whatever you have on hand!)
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


## Single-package op amp configuration



## Dual-package op amp configuration
