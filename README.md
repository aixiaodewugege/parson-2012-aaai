# parson-2012-aaai
MATLAB code used for the empirical experiments in my paper:

Oliver Parson, Siddhartha Ghosh, Mark Weal, Alex Rogers. Non-intrusive Load Monitoring using Prior Models of General Appliance Types. In: 26th AAAI Conference on Artificial Intelligence. Toronto, Canada. 2012.

The data file, 'aaai.mat' is a parsed version of the REDD data set, which I'm afraid I can't redistribute. I was hoping to release the script I used to create this data structure, but but I'm afraid I never got round to it before finishing my PhD. As far as I can see from my code, it looks like it creates a variable called 'loads', which is a cell array of houses, e.g. loads{1} contains a matrix for house 1. For each house, the first column of the matrix contains the household aggregate data, while the remaining columns contain the sub-metered data for various appliances, e.g. loads{1}(:,1) is an array containing the aggregate data for house 1, while loads{1}(:,2:) is a matrix containing the sub-metered data for house 1. I remember I also summed the two phases of aggregate power into a single feed, and also summed the two feeds where a single appliance is connected to both phases. I think I then resampled these feeds to a fixed sampling rate of 1 sample per minute.

`main.m` specifies the following parameters which general to all appliance instances of the same type:
- always_on - the baseload power which should be assumed while the appliance is off
- window_length - the duration of windows of aggregate data which are tested for similarity against the general model
- starting_point - data to skip at the start of data set (only for computational reasons)
- training_length - number of windows of aggregate data to search for appliance signature for tuning
- num_of_windows - number of windows to select which are most similar to general model to be used for tuning
- lik_thresh - likelihood threshold above which a window of aggregate data is considered to only contain state changes generated by the appliance of interest
