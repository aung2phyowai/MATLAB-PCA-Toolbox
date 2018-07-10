# PCA-Toolbox
Tools for spatial PCA, temporal PCA, temporal spatial PCA, and spatial temporal PCA analysis.

You MUSE have Joe Dien's PCA toolkit in your MATLAB path for these tools to word. Credit to Joe Dien for all the work done on the PCA toolkit, all we have written are shell files to run spatial, temporal, spatial temporal, and temporal spatial PCA easily.

Here is some sample code to run a spatial PCA with IMAX rotation and create some virtual ERPs.

load('samplePCAData');
% run spatial PCA
[PCAResults] = spatialPCA(ERP.data,ERP.chanlocs,'PMAX',5);
% select a factor
whichFactor = 1;
% get virtual conditional and DW average and grand average waveforms
virtualERPs = squeeze(PCAResults.virtualERPs(whichFactor,:,:,:));
meanvirtualERPs = mean(virtualERPs,3);
