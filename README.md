This is a Python class to generate plots of the Mandelbrot set using Matplotlib

The class is defined as follows:
- Mandel(pixels=50, bounds=25, itermax=25)
  - pixels => the desired size of the resulting image ( pixels x pixels )
  - bounds => the value at which we assume the test point diverges
  - itermax => the number of iterations before we assume the test point converges

The class works as follows:
- A grayscale image of size ( pixels x pixels ) is defined, where each pixel is associated with a point on the complex plane
- For each pixel, we check if the quadratic map diverges when applied to the associated point
  - The check for divergence is done with an escape time algorithm, bounded by `bounds` and `itermax`
  - For each iteration `i`:
    - If the quadratic map exceeds `bounds`, we assume it diverges
    - If the check reaches `itermax`, we assume it converges
  - We define a "confidence of convergence", where `cvrg_conf = i / itermax`
  - We color the associated pixel using value `cvrg_conf * 255`, so that brighter pixels represent points which more likely converge, and are thus more likely members of the Mandelbrot set
