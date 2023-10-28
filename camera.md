# Camera Calculations
To convert the camera FOV to the focal length that is required by most equations for the remainder of this is 

$$ FOV = 2 \arctan {(\frac {x}{2f})} $$

Alternatively to calculate the the focal length from the FOV then the equation would be:

$$ f=\frac {x} {2\tan{(\frac {FOV}{2})}} $$

In this equation, x is the size of the dimension of the CMOS (ideally in millimeters). This dimension of the CMOS would be the diagonal distance across the sensor. For example for our calculations on the [Arducam OV2640](https://www.uctronics.com/download/OV2640_DS.pdf) this would be $ \sqrt {3.52 \text { mm}^2+2.64 \text { mm}^2} = 4.4 \text { mm} $.