Lab 5: DOS SANTOS TEO
Link to my Digital-electronics-2 GitHub repository:

7-segment library
In your words, describe the difference between Common Cathode and Common Anode 7-segment display.

The difference between the two displays is the common cathode has all the cathodes of the 7-segments connected directly together and the common anode has all the anodes of the 7-segments connected together.

Code listing with syntax highlighting of two interrupt service routines (TIMER1_OVF_vect, TIMER0_OVF_vect) from counter application with at least two digits, ie. values from 00 to 59:

/**********************************************************************
 * Function: Timer/Counter1 overflow interrupt
 * Purpose:  Increment counter value from 00 to 59.
 **********************************************************************/
ISR(TIMER1_OVF_vect)
{
    // WRITE YOUR CODE HERE
    cnt0++;
	if(cnt0 > 9){
          ct0 = 0;
	  ct1++;
	  if (ct1 > 5){			
	      ct1 = 0;				
	  }
	}

}
/**********************************************************************
 * Function: Timer/Counter0 overflow interrupt
 * Purpose:  Display tens and units of a counter at SSD.
 **********************************************************************/
ISR(TIMER0_OVF_vect)
{
    static uint8_t pos = 0;

    // WRITE YOUR CODE HERE
    if (pos == 0){
	SEG_update_shift_regs(cnt0, 0);
    }
    else if (pos == 1){
		SEG_update_shift_regs(cnt1, 1);
    }
    pos++;
    if(pos > 1){
	pos = 0;

    }

}
Flowchart figure for function SEG_clk_2us() which generates one clock period on SEG_CLK pin with a duration of 2 us. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.
Kitchen alarm
Consider a kitchen alarm with a 7-segment display, one LED and three push buttons: start, +1 minute, -1 minute. Use the +1/-1 minute buttons to increment/decrement the timer value. After pressing the Start button, the countdown starts. The countdown value is shown on the display in the form of mm.ss (minutes.seconds). At the end of the countdown, the LED will start blinking.

Scheme of kitchen alarm; do not forget the supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values.
