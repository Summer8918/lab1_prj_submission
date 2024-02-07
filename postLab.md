Postlab Questions <br>
Postlab 1. Please answer the following questions and hand in as your postlab for Lab 1 <br>
1. What are the GPIO control registers that the lab mentions? Briefly describe each of their functions. <br>
(1) MODER register, used to select the I/O mode (00: input mode, 01: general purpose output mode, 10: Alternate function mode, 11: analog mode) <br>
(2) OTYPER register, used to choose the port output type (0: Output push-pull, 1: Output open-drain). <br>
(3) PUPDR register, used to choose pull-up or pull-down resistors (01: no pull-up, pull-down, 01: pull-up, 10: pull-down). <br>
(4) OSPEEDR register, used to config the port out speed (x0: low speed, 01: medium speed, 11: high speed). <br>
(5) IDR register, used to read input of entire 16 pins of port. <br>
(6) BSRR register, used to set or reset the I/O pins. (Bits 31: 16 is used to reset the corresponding bits, 15: 0 is used to set the corresponding bits).<br>
(7) ODR register, used to write output to entire 16 pins of port. <br>
(8) RCC (Reset and Clock Control), used to control clocks for various parts of the microcontroller such as processor,  different peripherals, buses, memories etc. RCC AHB peripheral clock register, used to enable and disabling GPIO peripheral clock. <br>
<br>
2. What values would you want to write to the bits controlling a pin in the GPIOx_MODER register in order to set it to analog mode? <br>
Write 11. <br>
<br>
3. Examine the bit descriptions in GPIOx_BSRR register: which bit would you want to set to clear the fourth bit in the ODR?
Bit 20. <br>
<br>
4. Perform the following bitwise operations: <br>
• 0xAD | 0xC7 = 0xEF <br>
• 0xAD & 0xC7 = 0x85 <br>
• 0xAD & ~(0xC7) = 0x28 <br>
• 0xAD ^0xC7 = 0x6A <br>
 <br>
5. How would you clear the 5th and 6th bits in a register while leaving the other’s alone? <br>
register &= ~((0x1 << 5) & (0x1 << 6)) <br>
<br>
6 What is the maximum speed the STM32F072R8 GPIO pins can handle in the lowest speed setting? <br>
• Use the chip datasheet: lab section 1.4.1 gives a hint to the location. You’ll want to search the I/O AC characteristics table. You will also need to view the OSPEEDR settings to find the bit pattern indicating the slowest speed. <br>
When CL = 50pF and VDDIOx >= 2 V, the max speed is 2 MHz. <br>
When CL = 50pF and VDDIOx < 2 V, the max speed is 1 MHz. <br>
"VDDIOx" typically refers to the power supply voltage for input/output (I/O) pins in a digital integrated circuit or microcontroller. <br>
<br>
7. What RCC register would you manipulate to enable the following peripherals: (use the comments next to the bit defines for better peripheral descriptions) <br>
• TIM1 (TIMER1) <br>
• DMA1 <br>
• I2C1  <br>
RCC->APB2ENR |= RCC_APB2ENR_TIM1EN;  // Enable the peripheral clock of Timer 1 <br>
<br>
RCC->AHBENR \|= RCC_AHBENR_DMA1EN;  // Enable the peripheral clock on DMA1 <br>
<br>
RCC->APB1ENR |= RCC_APB1ENR_I2C1EN; // Enable the peripheral clock on I2C <br>

