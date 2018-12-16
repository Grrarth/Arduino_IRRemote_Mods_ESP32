# Arduino_IRRemote_Mods_ESP32
Quick and dirty patch to get standard Arduino (1.8.5) IRRemote running on your ESP32

The section is here:

#elif defined(ESP32)
        // No system LED on ESP32, disable blinking by NOT defining BLINKLED

        // avr/interrupt.h is not present
#       undef HAS_AVR_INTERRUPT_H

	// BEGIN - Grrarth@GitHub - 20181213
	// Arduino 1.8.5 (ESP32 Selected) will not compile because it needs 
	// a send pin even though not used due to no support
	const int SEND_PIN = 0;
	// END - Grrarth@GitHub - 20181213

        // Sending not implemented
#       undef SENDING_SUPPORTED#

        // Supply own enbleIRIn
#       undef USE_DEFAULT_ENABLE_IR_IN
