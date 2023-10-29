# Demystifying the Math of Stereoscopy

The basics comes down to these three fundamental equations:

$$ \frac {z}{f}=\frac{x}{x_l} $$

$$ \frac {z}{f}=\frac{x-b}{x_r} $$

$$ \frac {z}{f}=\frac{y}{y_l}=\frac{y}{y_r} $$


Somehow these equations create the follow equations to get the X, Y, Z coordinates.
|            Z Coordinate           |          X Coordinate            |           Y Coordinate          |
| --------------------------------- | -------------------------------- | ------------------------------- |
$ \Large {z= \frac {fb}{x_l-x_r}} $ | $\Large {x=b+\frac {x_rz} {f}} $ | $ \Large {y=\frac {y_rz} {f}} $ |

For the purposes of these equations $ b $ is the distance between the two cameras (the baseline). $f$ is the focal length of the camera (ideally in millimeters). $x_l$ is the X coordinate in the left camera and $x_r$ is the X coordinate in the right camera. $y_l$ is the Y coordinate in the left camera and $y_r$ is the Y coordinate in the right camera. 


Below is a function in the Rust programming language to calculate based on the needed values.


```rust
fn getCoordinateVector(focal: f32, base: f32, px_l: f32, 
px_r: f32, py_l: f32, py_r: f32, pxtk: f32) {

    let x_l: f32 = px_l*pxtk;
    let x_r: f32 = px_r*pxtk;
    let y_l: f32 = py_l*pxtk;
    let y_r: f32 = py_r*pxtk;

    let z: f32 = (focal*base)/(x_1-x_r);
    let x: f32 = base + (x_r*z)/focal;
    let y: f32 = (y_r*z)/focal;

    let array: [f32; 3] = [x,y,z];

    return array;
}
```