### How to have different sensitivity in Mouse and Touchpad.

Linux allow us to have different sensitivity in Mouse and TouchPad.
First of all we need to get a list of all the inputs we have available.

`xinput`

The result will be something like this:
```
⎡ Virtual core pointer                    	id=2	[master pointer  (3)]
⎜   ↳ Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
⎜   ↳ ETPS/2 Elantech Touchpad                	id=13	[slave  pointer  (2)]
⎜   ↳ USB Optical Mouse                       	id=16	[slave  pointer  (2)]
⎣ Virtual core keyboard                   	id=3	[master keyboard (2)]
    ↳ Virtual core XTEST keyboard             	id=5	[slave  keyboard (
```

So now we use the ID or the name and check all the properties:

`xinput list-props "USB Optical Mouse"`

```
Device 'USB Optical Mouse':
	Device Enabled (142):	1
	Coordinate Transformation Matrix (144):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (267):	0
	Device Accel Constant Deceleration (268):	1.000000
	Device Accel Adaptive Deceleration (269):	1.000000
	Device Accel Velocity Scaling (270):	10.000000
```

So in this case we need to change the Constant Deceleration (1 = current, 2 = twice as slow) so the higher the slower the mouse

So you can do using the Name between quotes or the number:

So in this case:
 
`xinput set-prop 16 268 1.2`

is equivalent to 

`xinput set-prop "USB Optical Mouse" "Device Accel Constant Deceleration" 1.2` 


