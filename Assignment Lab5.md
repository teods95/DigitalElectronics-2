# Lab 5: DOS SANTOS TEO

Link to this file in your GitHub repository:

https://github.com/teods95/DigitalElectronics-2


### 7-segment library

1. In your words, describe the difference between Common Cathode and Common Anode 7-segment display.
The difference between the two displays is the common cathode has all the cathodes of the 7-segments connected directly together and the common anode has all the anodes of the 7-segments connected together.

2. Code listing of two interrupt service routines (`TIMER1_OVF_vect`, `TIMER0_OVF_vect`) from counter application with at least two digits, ie. values from 00 to 59. Always use syntax highlighting and meaningful comments:

```c
/**********************************************************************
 * Function: Timer/Counter1 overflow interrupt
 * Purpose:  Increment counter value from 00 to 59.
 **********************************************************************/
ISR(TIMER1_OVF_vect)
{
    // WRITE YOUR CODE HERE
    cnt0++;
	if(cnt0 > 9){
	  cnt0 = 0;
    	  cnt1++;
	      if (cnt1 > 5){
		  cnt1 = 0;				
	      }
	}

}
```

```c
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
```

3. Flowchart figure for function `SEG_clk_2us()` which generates one clock period on `SEG_CLK` pin with a duration of 2&nbsp;us. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.

 ![unnamed (1)](https://user-images.githubusercontent.com/60385716/146598954-fe9a3766-de7d-4d4b-afb8-cab1895d460d.jpg)



### Kitchen alarm

Consider a kitchen alarm with a 7-segment display, one LED and three push buttons: start, +1 minute, -1 minute. Use the +1/-1 minute buttons to increment/decrement the timer value. After pressing the Start button, the countdown starts. The countdown value is shown on the display in the form of mm.ss (minutes.seconds). At the end of the countdown, the LED will start blinking.

1. Scheme of kitchen alarm; do not forget the supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values.

 ![unnamed (2)](https://user-images.githubusercontent.com/60385716/146598985-0da4fd04-5597-4ca4-b137-391b4a32a47a.jpg)

