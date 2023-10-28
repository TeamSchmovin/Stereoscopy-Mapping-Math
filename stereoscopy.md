# Demystifying the Math of Stereoscopy

The basics comes down to these three fundamental equations:

$$ \frac {z}{f}=\frac{x}{x_l} $$

$$ \frac {z}{f}=\frac{x-b}{x_r} $$

$$ \frac {z}{f}=\frac{y}{y_l}=\frac{y}{y_r} $$


Somehow these equations create the follow equations to get the X, Y, Z coordinates.
|           Z Coordinate          |         X Coordinate           |          Y Coordinate         |
| ------------------------------- | ------------------------------ | ----------------------------- |
$ z= \LARGE \frac {fb}{x_l-x_r} $ | $\LARGE x=b+\frac {x_rz} {f} $ | $ \LARGE y=\frac {y_rz} {f} $ |

For the purposes of these equations $ b $ is the distance between the two cameras (the baseline). $f$ is the focal length of the camera (ideally in millimeters). $x_l$ is the X coordinate in the left camera and $x_r$ is the X coordinate in the right camera. $y_l$ is the Y coordinate in the left camera and $y_r$ is the Y coordinate in the right camera. 