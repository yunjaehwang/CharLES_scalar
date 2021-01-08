# Turbulent channel flow

**References**

1. [DNS data](https://turbulence.oden.utexas.edu/data/MKM/chan395/profiles/)
2. [Cascade webpage (using ideal gas solver)](https://support.cascadetechnologies.com/posts/1968-turbulent-channel)

---

### Comparison to other simulation results

- Velocity field

  <img src="images/mean_Ux.png" width=300>

  <img src="images/rms_Uxvw.png" width=1200>

  <center>Figure. comparison of velocity profiles</center>

- Scalar field





### Minor correction in source code 

- Varying trend of mean scalar profiles is the opposite to as it should be \
  -> Schmidt number should go denominator instead of numerator? 

- Modified codes

  1. **HelmholtzSolver.cpp & HelmholtzSolverBCs.cpp**
     Modify scalar transport equation part, \
     Schmidt number is divided instead of being multiplied     

  2. **FlowSolver.hpp**
     Initial value of Schmidt number is set to 1.0 (originally 0.0) to avoid errors due to zero division

     

- Results

<img src="images/orig_scalar_profile_mean.png" width=500>

<center> Figure: result using origial code </center>

<img src="images/update_scalar_profile_mean.png" width=500>

<center> Figure: result using updated code </center>
