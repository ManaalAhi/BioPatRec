# Feature extraction #

![https://biopatrec.googlecode.com/svn/wiki/img/Biopatrec_paper/Biopatrec_signalfeatures_featurevectors.png](https://biopatrec.googlecode.com/svn/wiki/img/Biopatrec_paper/Biopatrec_signalfeatures_featurevectors.png)
_Feature vectors constructed from myoelectric signals.  [Fig. 4 from BioPatRec paper](http://www.scfbm.org/content/8/1/11)_

Although there are few PatRec algorithms that can be feed directly with time series, such as myoelectric signals, the vast majority require discrete values. In our case, these signal features are extracted from fixed time windows, or signal segmentation, handle by SigTreatment.

See BioPatRec\_StartupGuide for quick user instructions and BioPatRec\_Roadmap for an overview of the functions involved.

## Features ##

These are some of the available signal features

| **ID**    | **Feature**           | **Domain** |
|:----------|:----------------------|:-----------|
| tmn       | Mean                  | Time       |
| tmabs     | Mean absolute value   | Time       |
| tmd       | Median                | Time       |
| tstd      | Standard deviation    | Time       |
| tvar      | Variance              | Time       |
| twl       | Waveform length       | Time       |
| trms      | RMS                   | Time       |
| tzc       | Zero-crossing         | Time       |
| tpks      | Peaks (over RMS)      | Time       |
| tmpks     | Peaks mean            | Time       |
| tmvel     | Mean  velocity        | Time       |
| tslpch1   | Slope changes (peaks) | Time       |
| tslpch2   | Slope changes (diff)  | Time       |
| tpwr      | Power                 | Time       |
| tdam      | Difference abs. mean  | Time       |
| tmfl      | Max fractal length    | Time       |
| tfd       | Fractal dimension     | Time       |
| tfdh      | Fractal dim. Higuchi  | Time       |
| tren      | Rough entropy         | Time       |
| tcr       | Correlation           | Time       |
| tcv       | Co-variance           | Time       |
| fwl       | Waveform length       | Frequency  |
| fmn       | Mean                  | Frequency  |
| fmd       | Median                | Frequency  |
| fpmn      | Peaks mean (Top 5)    | Frequency  |
| fpmd      | Peaks median (Top 5)  | Frequency  |
| fpstd     | Peaks std (Top 5)     | Frequency  |

The [GUI\_PatRec](GUI_PatRec.md) includes sets of the top features, or more commonly used, for their easy selection before PatRec.

## Implementation ##

  * The GetAllSigFeatures function is the base of [sigFeatures](sigFeatures.md) and populates the [xFeatures](xFeatures.md) by calling GetSigFeatures
    * Input:
      * handles (from the GUI)
      * [sigTreated](sigTreated.md)
    * Output:
      * [sigFeatures](sigFeatures.md)

  * GetSigFeatures computes all the requested features in fID.
    * Input:
      * data(Samples x Channels)
      * sF (sampling frequency)
      * fID (Vector of cells with the features ID)
    * Output:
      * xFeatures
    * This function call the specific functions to compute each feature using :
      * pF (structure received by each function to compute a feature)
        * pF.ch (channels)
        * pF.sp (samples)
        * pF.sF (sampling frequency)
        * pF.data (Samples x Channels)
        * pF.absdata (Samples x Channels)
        * pF.f ([xFeatures](xFeatures.md), a structure with all the computed features)

# Adding a new feature #

Adding new signal features is very simple, you only need to:

  1. Add the ID (_t/fXXX_) in the features.def file
  1. Create a function call "_GetSigFeatures\_t/fXXX_" that receives pF, and returns _pF.f.t/fXXX = your feature values_. Most of the "_GetSigFeatures\_tXXX_" routines are inside the GetSigFeatures function.

t/f corresponds to time/frequency.

NOTE: If you consider that part of your computation would be useful for another feature, you can add it in pF. (e.g. `GetSigFeatures_tpks`)