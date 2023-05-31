- Hardware is meant to be deterministic.
  Deterministic means that given the same inputs, there should be  the same outputs.

- **True Random and Pseudo-random number generators.**
  The most common of the two is pseudo-random number generators (PRNGs), which use software and a "seed" to generate random number. Seeds are fairly easy to predict.
  
  For nearly all applications, PRNGs are good enough, but for some higher stake applications, like cryptography, we don't want anyone to be able to predict out seed. These PRNGs are considered deterministic.
  
  For those higher stakes scenarios, sometimes a true random number generator is required.
  
  TRNGs use something like radioactivity, atmospheric noise, or a video of a bunch of lava lamps to create a truly random seed as input. These TRNGs are considered non deterministic.
  
  Another form of TRNGs is a computer chip known as a Hardware RNG, which, develops an input that is, based on known laws of physics, impossible to predict.

Next section -> [[Fetch, Decode, Execute]]


- PCI slot:
  PCI (Peripheral Component Interconnect) slot is a type of expansion slot found on the motherboard of a computer. It is used to connect various peripheral devices, such as network card, sound cards, graphics cards, and expansion cards, to the computer's motherboard.
  
  PCI slots provide a standardised interface and communication protocol for these devices to interact with the computer's central processing unit and memory.