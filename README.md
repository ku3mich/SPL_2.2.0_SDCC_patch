Patch for STM8 Standard Peripherals Library v2.2.0
--------------------------------------------------

with the great support by the SDCC community I provide here an initial patch for SDCC of the STM8 Standard Peripheral Library available by STM from http://www.st.com/web/en/catalog/tools/FM147/CL1794/SC1807/SS1754/PF258009

Technical status:
  - applied SDCC specific changes to some headers and sources (marked with "SDCC“)
  - changed all ISR headers in examples to skip ISR declaration (see open points)
  - added flash r/w for 24b addresses via inline assembly (thanks Philipp!)
  - created a SDCC "template project“ (i.e. Makefile). See $(SPL)/Project/STM8S_StdPeriph_Template/
  - created Win, Linux, and MacOSX batch scripts to compile and upload via https://github.com/gicking/STM8_serial_flasher 
  - added Doxygen input for creating manual from sources, since provided UM is in Windows proprietary .chm format —> run Doxy to create HTML docu
  - all SPL examples can be compiled but require editing of Makefile. Functionality tested partly (see open points)

Open points —> questions to you:
  - I only have access to a STM8 Discovery Board and a custom PCB, so I can't verify all functionality -> additional checking is required
  - since I am used to IDEs, the provided Makefile is far from perfect. For example it lacks automatic dependencies. Any help is appreciated!
  - in the same content: a template project for an IDE would be nice, but which one…?
  - acc. to UM flash block operations must be executed from RAM. How do I compile/link code for RAM execution?
  - SDCC requires the interrupt token AFTER the function name in ISR declaration. I have fixed all examples, but this requires a manual fix for other libs that rely on SPL (see STM homepage). However, according to Erik and Philipp this would require a change of the SDCC parser with associated risks --> not likely to be changed
  - the trap handler requires a recent nightly-build. To skip, set SKIP_TRAPS=1 in Makefile. Trap handling is planned for the next release (when?)

Legal status:
  - STM has indicated that they may approve of distribution of the modified sources. But nothing official, yet
  - I would still prefer STM to support SDCC officially to assert future consistency. But so far no news on this

For instructions on patching see e.g. http://jungels.net/articles/diff-patch-ten-minutes.html. Please let me know if the patch works.

My first impressions of the SPL are quite mixed. It seems much more complicated than e.g. Wiring for Arduino. However, as said before the STM8 SPL is very similar to the STM32 SPL. And for the latter with 100x registers, a HW-lib is almost mandatory. In addition STM provides a lot of ready-made software which is based on the SPL. So I guess it’s worth digging into… Let me know what you think!?

Any feedback and/or support on the above open points is highly welcome! 

Regards,
Georg Icking-Konert
