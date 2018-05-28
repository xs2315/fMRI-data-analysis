# fMRI-data-analysis

Data can be found from http://www.fil.ion.ucl.ac.uk/spm/download/data/MoAEpilot/

Work flow:

      1. Spatial Preprocessing:
      
             1)realignment:  
                     Estimate the six parameters of spatial transformation and then apply 
                     the spatial transformation on each brain data
                      
               Purpose: 
                     By doing this step, we reduce the influence of head movement on my 
                     data to improve accuracy
                   

             2)coregistration: 
                     Coregister between the anatomical image (T-1 weighted) and mean 
                     function image
               
               Purpose: 
                     By doing this step, we reduce the influence of anatomical scans and 
                     functional scans and maximize mutual information
               
             3)segmentation: 
                     Segment the structural image into different tissue types such like 
                     grey matter, white matter, cerebral spinal fluid (CSF), and skull 
                     using the tissue probability maps as prior. Also, estimates a 
                     spatial transformation that used for normalzing images.    
               
               Purpose:
                     Segment different tissue and estimates a spatial transformation that 
                     used for normalzing images

             4)normalization:
                      Warp all images so that they can fit a standard template brain, then 
                      superimpose their functional activations on their own anatomy
              
               Purpose: 
                     (1) Standardize result so that results from different studies can be 
                         comparable
                     (2) Allow us to conduct group-level analysis and improve statistical 
                         power
                     (3) Helpful to generalize findings to the population level
                     (4) Helpful to find the difference and commonalities between some 
                         groups such like patient and healthy people

             5)smoothing: 
                     convolutionin the spatial domain with a 3D Gaussian kernel
               
               Purpose: 
                     (1) Reduce noise
                     (2) Makes data more close to normal distribution
                     (3) Deal with functional anatomical variability that cannot be 
                         reduced by spatial normalization
                     (4) Using Inter-subject averaging as spatial normalization cannot   
                         perfectly align all structures
                     (5) Makes data more satisfy validity of statistical testing and easy  
                         to be analyzed
                              


Limitation: 

              Since the time used to acquire every slice for fMRI sequence may not be 
              same , We should use slice timing method such like linear interpolation 
              method and cubic spline interpolation method to correct time difference 
              among the slices

Experiment result:

              Here we performed one-sided T test
              
              If T>threshold (5.255065 in this case), we can conclude that the 
              corresponding voxel is activated
 
              For the Figure 30.13, the half above is mamaximum intensity projection  
              (MIP) and the half below is a list of activated voxels, which have the 
              observed T scores larger than threshold.

              For the Figure 30.15, this table shows that there are 3 local maxima that 
              are more than 8.0mm apart. Also, the expected voxels per cluster is 0.755   
              and expected number of clusters is 0.07. In addition, there are two major 
              clusters with cluster size 476 and 613. Their corresponding peak p value are 
              zeros, which also indicates that they are activated.          

              For the Figure 30.19, marked parts in Figure 30.19 represents activated 
              voxels of brain 
