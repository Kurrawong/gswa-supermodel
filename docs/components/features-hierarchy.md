<a href="../../assets/features-hierarchy/Hierarchy.svg">
<figure id="figure-gfh" markdown style="width:70%">
  ![](../assets/features-hierarchy/Hierarchy.svg)
  <figcaption>Figure GFH: A Feature class hierarchy within which this Model's elements exists</figcaption>
</figure>
</a>

## Purpose 

This component model describes the overarching hierarchy of geospatial Features used by GSWA to position Mines, Sites, Cratons, Basins etc. This Component Model is the immediate parent model of the [Sites & Admin Features](sites-admin.md) and [Geological Features](geofeature) component models.

## Model logic

The logic of this component model is shown in the class hierarchy diagram above:

* all Features known to GSWA are either 'Man-made', 'Natural' or some specialised form of either 
* there is no prohibition on a Feature being _both_ natural and man-made or many other combinations of sub-classes of those two main classes
    * this top-level cannot set detailed rules for what combinations of Feature class are allowed

