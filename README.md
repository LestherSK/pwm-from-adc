PWM From ADC
============

This project can be used as a robot's joystick to generate PWM for motor DC from ADC values.
Many [ABU Robocon](http://en.wikipedia.org/wiki/ABU_Robocon) contestants from Indonesia use this kind
of joystick to drive their robots.

## Spec

* Schematic: adc_schematic.png
* Internal ADC from ATMega16 or ATMega8535
* ADC0 (PINA.0) and ADC1 (PINA.1) connected to potentiometer (10k or 50k is fine). Sliding contact from potentiometer is hooked into two
  meshing gears.
* R3, R4, R5, and R6 values are 220 or 330 Ohm.
* ADC values (1 - 255) is adjusted to set the Timer0 from MCU. For example, simple formula like below:

  ~~~text
  // Assuming center value (126-128) is for stop
  if ( adc < 126 ) {
		motor_direction = forward;
		pwm = ( adc - 128 ) * 2;
  } else {
		motor_direction = backward;
		pwm = 255 - ( adc * 2 );
  }

  ~~~

## License - MIT License

Copyright (c) 2006 Akeda Bagus <admin@gedex.web.id>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.