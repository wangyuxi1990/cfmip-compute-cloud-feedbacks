# Overview #

Cloud radiative kernels [Zelinka et al. (2012)](http://www.atmos.washington.edu/~mzelinka/Zelinka_etal12a.pdf) quantify the sensitivity of top-of-atmosphere (TOA) radiative fluxes to cloud fraction perturbations within seven cloud top pressure categories and seven optical depth categories.  Multiplying the cloud radiative kernels, which are a function of latitude, month, and surface albedo, by changes in cloud fraction (segregated on the same cloud top pressure-optical depth grid) between two climate states yields a quantitative estimate of cloud-induced TOA radiation anomalies.  Normalizing these by the change in global mean surface temperature between the two climate states provides a measure of cloud feedback.

Because the kernels are computed using a single radiative transfer code (Fu-Liou), differences in cloud feedbacks among climate models can be unambiguously attributable to inter-model differences in the responses of clouds.  Furthermore, because the cloud feedback is computed directly from changes in cloud fields rather than inferred from TOA fluxes, no adjustments are necessary to account for non-cloud-induced radiative flux anomalies. The tremendous advantage of this technique over previous techniques is its ability to quantify the contribution of 49 different cloud types to the cloud feedback. For more details, see our papers documenting these results (below). Please let me know if you make use of these kernels, and feel free to email me with any questions.

# Details #

The code takes in a single model's monthly-resolution ISCCP simulator cloud fraction histogram (clisccp) from both a control (amip) and perturbed (amipFuture) climate, and differences their annual cycles.  This difference is then multiplied by the monthly-resolved cloud radiative kernels to compute the cloud-induced radiation anomalies.  Normalizing these by the change in global mean surface air temperature (tas) between these two runs provides an estimate of the cloud feedback.

The kernels are computed for three values of clear-sky surface albedo rather than for a pre-determined longitudinal distribution of surface albedos.  In order to map the kernels to physical space applicable for a given model, the calculation therefore requires the model's monthly-resolved clear-sky upwelling and downwelling shortwave radiation at the surface (rsuscs and rsdscs).

We have provided the following netcdf files:
  * clisccp, rsuscs, rsdscs, and tas fields from the MPI-ESM-LR model (as an example)
  * LW and SW cloud radiative kernels

The user must update the directory paths to these files within the matlab script. These are indicated in the script by the comments :% USER: MODIFY THIS LINE"

# References & Acknowledgements #

  * Zelinka, Mark D., Stephen A. Klein, Dennis L. Hartmann, 2012: Computing and Partitioning Cloud Feedbacks Using Cloud Property Histograms. Part I: Cloud Radiative Kernels. J. Climate, 25, 3715–3735. doi:10.1175/JCLI-D-11-00248.1.
  * We acknowledge the World Climate Research Program’s Working Group on Coupled Modeling, which is responsible for CMIP. For CMIP, the U. S. Department of Energy’s Program for Climate Model Diagnosis and Intercomparison provides coordinating support and led development of software infrastructure in partnership with the Global Organization for Earth System Science Portals.