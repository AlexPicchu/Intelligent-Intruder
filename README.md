# Intelligent-Intruder
MEng Project - Reinforcement Learning for an Intelligent Intruder


## Sudo Code for Algorithm


### functions:
- f1(batch size, window of timesteps, node, features) = confidence level
	- model prediction function that returns sigmoid confidence output for potential attack on each node at current timestep
	- model trains on batch size 32 of randomly sampled windows in replay buffer that is updated with the correct vulnerabilities as time passes
- f2(time, predictions, threshold) = probability of confidence level being above the threshold in remaining attack time
	- probaility calculated as: $insert final probability equation$
	- uses a 2nd replay buffer, same structure as the first but with only the prediction values from f1 for associated timesteps
- f3(f1, f2, threshold) = final attack
	- uses numerically calculated threshold and the product of f1 and f2 to determine when adversary attacks in the remaining timeframe

### structure:


## Data_summary:

$timestamp_idleness.csv
	Generated by simulator. Logs every visit to nodes made by agents, including the time, which robot, which node, idleness of the visited node at time of visit, and cumulative inter-agent interference count (not relevant)
	
$timestamp_info.csv
	Generated by simulator. Contains info on simulation parameters and overall performance. Not really relevant.

$timestamp_results.txt
	Generated by simulator. Logs information after every complete patrol cycle (ie. every node visited at least once), including mean and standard deviations of vertex idlenesses, number of visits to nodes, and some global idleness values (the simulator calculates these in a weird way, so don't trust these values by default)

$timestamp_timeresults.txt
	Generated by simulator. Logs some global idleness metrics every 15 minutes. Caveat about reported idleness values from results files applies here as well.

distance_metrics.csv
	Derived data. Logs distance metric (1/shortest distance (in pixels) between node and agent summed over all agents) for each node. First column is timestamps, subsequent columns are node 0-n. 

distances/distances_n.csv
	Derived data. Logs shortest distance (in pixels) from node n to all agents over time. No timestamp column present, timestamps are however the same as observed in position_log.csv or any other derived data file. Columns refer to agents.

idleness.csv
	Derived data. Logs idleness (time since last visit) of every node over time. First column is timestamps, subsequent columns are nodes 0-n. Negative values are present when idleness is unknown (ie. node has not yet been visited), inf values are present after node has been visited for the last time. Cropping of dataset necessary to remove negative or infinite values.

position_log.csv
	Generated by simulator. Logs cartesian coordinates (in metres) of all agents over time. First column is timestamp, subsequent columns are ordered agent 0 x, agent 0 y, agent 1 x, agent 1 y, ...
	 
velocity_metrics.csv
	Derived data. Logs velocity metric (velocity (in pixels/s) of agent towards node/shortest distance (in pixels) between node and agent summed over all agents) for each node. First column is timestamps, subsequent columns are node 0-n. 

vulnerabilities.csv
	Derived data. Logs vulnerability (time until next visit) of every node over time. First column is timestamps, subsequent columns are nodes 0-n. Inf values are present after node has been visited for the last time. Cropping of dataset necessary to remove infinite values.

