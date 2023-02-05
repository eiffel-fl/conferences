Pulse-Width-Modulation (PWM) is easy, isn't it?
===============================================

PWM is a piece of hardware which outputs a periodic square wave signal.
You can use it to blink or dim LED but also to drive display backlights.

From one rising edge to another, it is the period.
And the length of the rising edge is the duty cycle:

     ________    ________
\___/        \__/        \__
    |-----------| period
    |--------|    duty cycle

If the duty cycle equals the period, then it is always high.
Sadly, the Linux kernel API has different accuracy then the actual hardware which can lead to problem withn, *e.g.*, motors.
When you want to get the number of period steps, you should divide by the number of nanoseconds per second at the last step to not loose precision.

Sometime, your delta can be bad for latency but good for frequency.

Transitions between lenght of duty cycle and period are also a problem.
For example, if you change the configuration during a duty cycle, it would only be used for next period.
You can also get immediate start of a new period, but you wll have a lower edge at one small moment.
There are several limitations in terms of hardware, *e.g.*, it can be possible for some hardware to not have a 0 length duty cycle or this duty cycle to equal the period.
It is asked for new drivers to document there limitations as comments in the code.

To improve the life of everyone a new callback called ``round_state`` could be implemented, it would determine the actual state impledted for a given request (by being always rounded down).
To help debugging your driver, you can enable ``PWM_DEBUG``.
You should also compare the hardware state before and after a call to ``apply()``.
