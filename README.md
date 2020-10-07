# Klipper Setup Flow

*Important!*
1. don't forget to backup your config

## Initial config
1. copy config file or create a new one based on an existing one
2. fix any errors until klipper starts up
3. if temperature sensors are not set up, configure min_temp=-200 and max_temp=2000 temporarely

## Endstops
1. connect all endstops
2. run QUERY_ENDSTOPS
3. if any of the endstops shows reverse state then add or remove a "!" in front of pin definition like this
```
endstop_pin: ^!ar2
```
becomes
```
endstop_pin: ^ar2
```
or the reverse, of course
4. nce you changed all the pin definitions, restart klipper and go to #1 again, repeat until endstops show up right
5. now, manually trigger each endstop and run QUERY_ENDSTOPS - check the endstops is triggered
6. fix any issues then go to #1 again

now endstops should be running ok 

## Steppers
1. connect step sticks where needed
2. while board is POWERED off, connect all steppers
3. restart klipper
4. use STEPPER_BUZZ to check stepper is moving like this
```
STEPPER_BUZZ stepper=stepper_x
STEPPER_BUZZ stepper=stepper_b
...
```

If the stepper does not move at all and wiring looks ok, you can try changing the enable pin definition (add/remove a "!")
```
enable_pin: !ar38
enable_pin: ar38
```

5. if anything fails, fix the issue (bad wiring, connector, 12/24 v power issues) then go to #1 and repeat

## Stepper Directions - carthesian, delta
1. with the printer powered off, move each axis in the middle of it's travel so if you move it a couple of cm either way it won't hit anything
2. we're going to use the force move command to move a stepper a couple mm
```
FORCE_MOVE STEPPER=stepper_x DISTANCE=2
FORCE_MOVE STEPPER=stepper_a DISTANCE=2
```
3. watch the direction of the printhead / axis
4. if direction is not correct, find dir_pin and add/remove a ! in the pin definition
```
dir_pin: ar55
```
reverse direction
```
dir_pin: !ar55
```
5. if any steppers move in incorrect direction then make changes and go to #1 again

## Stepper Directions - corexy

...

## Confused about "correct" moving direction of the printhead ?

If you're facing the front of the printer:
```
-x is to the left
+x is to the right
-y is toward you
+y is away from you
+z is the printhead going up or bed going down (distance increases)
-z is the printhead going down or bed going up (disntance decreases)
```


