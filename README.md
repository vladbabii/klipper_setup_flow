# Klipper Setup Flow

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
