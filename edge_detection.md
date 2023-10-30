# Edge Detection Basics

## Canny Edge Detection

- Convert the image to grayscale
- Reduce noise  
  - As the edge detection that using derivatices is sensetive to noise, we reduce it


To do this we calculate total color difference at pixel differences. For this we will use R, G, and B
$$ L = (0.2126*R + 0.7152*G + 0.0722*B) $$

$$ a = R-G $$

$$ b = \frac{R+G}{2}-B $$

$$ \Delta E = \sqrt {\Delta L^2+\Delta a^2+\Delta b^2} $$

$ \Delta E $ is a numerical way of seeing change in color. Make a new array of the differences to spot high contrast zones.

Below is a function in the Rust programming language to calculate $ \Delta E $ with $R$, $G$, and $B$:

```rust
fn calculate_de(r_1: i8, g_1: i8, b_1: i8, r_2: i8, g_2: i8, b_2: i8) {
    
    let L_1: f32 = 0.2126*r_1 as f32 +0.7512*g_1 as f32 +0.0722*b_1 as f32;
    let L_2: f32 = 0.2126*r_2 as f32 +0.7512*g_2 as f32 +0.0722*b_2 as f32;
    let dL: f32 = L_2-L_1;

    let a_1: i8 = r_1-g_1;
    let a_2: i8 = r_2-g_2;
    let da: i8 = a_2-a_1;

    let B_1: i8 = (r_1+g_1)/2+b_1;
    let B_2: i8 = (r_2+g_2)/2+b_2;
    let dB: i8 = B_2-B_1;

    let dE: f32 = dL.powi(2)+da.powi(2)+dB.powi(2);
    dE = dE.sqrt();

    return dE;
}
```