# Modeling Just Noticeable Differences in Charts

Supplemental materials for our paper on _Modeling Just Noticeable Differences in Charts_

0. 'stimuli_data' folder //the bounds for conditions, meta data driven 7200 plots
	- *_bounds.csv // (epsilon_lower epsilon_upper) for each conditions in three charts
	- plot_data/*_test_*.json // data for the 7200 plots, i.e., heights of bars (in pixel) for bar chart, radius for bubbles in bubble chart, angles of fan in pie chart
	- plot_data/*_meta_*.json // meta data for the 7200 plots, i.e., the 'intensity of standard stimulus' (baseHeight/baseR/baseAngle) in each plot, 'difference' (delta*), and 'distance' (gap*)

1. "jnd" folder //the estimated jnds, sorted by chart type

	- jnd_bar.csv
	- jnd_bubble.csv
	- jnd_pie.csv
	
Data dict:
- userid: [String] unique user id
- intensity: [Int] intensity of standard stimulus (i.e., height in bar chart, radius in bubble chart, degree in pie chart)
- distance: [float] distance between standard stimulus and compared stimulus
- jnd: [float] estimated Just Noticeable Difference
- pse: [float] estimated Point of Subjective Equality


2. "rawdata" folder //the raw data collected for each trial, for each chart type, the raw data sorted by user, in file name formate of "userid.csv"

	- bar/*.csv  
	- bubble/*.csv
	- pie/*.csv

Data dict:
- yes-answer: [Boolean] 1 if answering the compared stimulus is larger/taller than standard stimulus; 0 if not
- time: [Float] time cost of answering this trial- intensity: [Int] intensity standard stimulus in this trial
- distance: [float] distance in this trial- difference: [float] the intensity difference between compared stimulus and standard stimulus, if negative, it means compared stimulus is smaller/shorter than standard stimulus.

3. "stat" folder //the yes-answer counting for each condition, for each chart type, the yes-answer is sorted by each user, each condition, in file name formate of "userid_distance_intensity.csv"
	
	- bar/*.csv
	- bubble/*.csv
	- pie/*.csv


4. "stat_dest” folder //computed JND for each user at each condition, in each chart type, in file name formate of "userid_distance_intensity.csv.txt”
	
	- dest_bar/*.txt
	- dest_bubble/*.txt
	- dest_pie/*.txt


Date dict:
- X: [Float] the intensity of compared stimulus
- Yes: [Int] the number of yes-answer in that 10 trials 
- Total: [Int] the number of trials in that comparison, we repeat 10 trials, so it is 10

5. “code” folder //the python / R script that we run to analysis the data
	
	-draw_jnd_distribution.ipynb // draw the box plot distribution in Fig. 4
	-compJND_2021_submitted.R // read data from stat and compute JNDs
	-jnd_*2021_submitted.R // JND modeling in three charts
