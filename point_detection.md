# The Math of Point Detection

## Outline

1. Edge Detection
2. Edge Parsing
3. Edge Matching
4. Depth Calculation

## Edge Detection Basics

While there are many methods of edge detection that already exist, and this may correlate heavily with an existing algorithm, this is completely from scratch.

To do this we calculate total color difference at pixel differences. For this we will use R, G, and B

$$ L = 0.2126(R) + 0.7152(G) + 0.0722(B) $$

$$ a = R-G $$

$$ b = \frac{R+G}{2}-B $$

$$ \Delta E = \sqrt {\Delta L^2+\Delta a^2+\Delta b^2} $$

$\Delta E$ is a numerical way of seeing change in color. Make a new array of the differences to spot high contrast zones.

Below is a function in the Rust programming language to calculate $\Delta E$ with $R$, $G$, and $B$:

```rust
fn calculate_de(r_1: u8, g_1: u8, b_1: u8, r_2: u8, g_2: u8, b_2: u8) {
    
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

A new two-dimensional array would be created with a width of the width of the original picture minus one and a height of the height of the original pictue minus one. A cursor would be moved across the picture to the width of the original picture minus one and the height of the original picture minus one, iterating over each pixel. 

At each pixel value, you calculate the difference between the pixel directly below and the pixel directly to the right. The final value that would be placed into the new two-dimensional array of pixel values is the maximum of those two values, to ensure that if an edge is present, it is seen in the final map even if the edge only appears in one dimension.