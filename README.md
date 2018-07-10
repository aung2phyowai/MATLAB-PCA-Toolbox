# PCA-Toolbox
Tools for spatial PCA, temporal PCA, temporal spatial PCA, and spatial temporal PCA analysis.

You MUSE have Joe Dien's PCA toolkit in your MATLAB path (https://sourceforge.net/projects/erppcatoolkit/) for these tools to word. Credit to Joe Dien for all the work done on the PCA toolkit, all we have written are shell files to run spatial, temporal, spatial temporal, and temporal spatial PCA easily. The key inputs are ERP data in a 4D matrix (channels x time x conditions x participants), and EEGLAB channel locations file, and a time vector for plotting purposes. If you load the sample data, 'samplePCAData.mat' you can see the structure formats. A final note, you will also have EEGLAB installed and in your MATLAB path.

Here is some sample code to run a spatial PCA with IMAX rotation and create some virtual ERPs. Only components that explain at least 5% of the variance are kept.

load('samplePCAData');

% run spatial PCA

[PCAResults] = spatialPCA(ERP.data,ERP.chanlocs,'IMAX',5);

% select a factor

whichFactor = 1;

% get virtual conditional and DW average and grand average waveforms

virtualERPs = squeeze(PCAResults.virtualERPs(whichFactor,:,:,:));

meanvirtualERPs = mean(virtualERPs,3);


Here is some sample code to run a temporal spatial PCA with PMAX rotation (temporal) and IMAX rotation (spatial). Only components that explain at least 5% of the variance are kept.

[PCAResults TSPCAResults] = temporalSpatialPCA(ERP.data,ERP.chanlocs,ERP.time,'PMAX','IMAX',5);
