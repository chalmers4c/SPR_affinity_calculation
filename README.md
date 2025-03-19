# SPR_affinity_calculation
The code aims to import an excel file, perform fit on the K_on region of the SPR data, find the maximum response unit from fitting across multiple concentration of analyte, then use Langmuir isotherm equation to find the maximum response, then extract affinity data from this fit.
# Requirement
- Use reference subtracted data, some python knowledge is needed, particularly the dataframe structure.
- Ready to use excel file, it should be organised such that Column A is Time (s) (x-axis), Column B is the response unit (RU) (y-axis), Column C is Category data (which concentration this data point belongs to)
- Some packages will be imported that may require you to install them
# Example
With an excel like below, it is ready to be imported into this code

![image](https://github.com/user-attachments/assets/26107181-08eb-4925-b9b5-e93c62443d9e)

The code will perform a combined function contains exponential decay and straight line, and each concentration is fitted. Sometimes fit will fail, probably due to the curve appears as a straight line between the observation window, i.e. it is lack of an exponetial decay plateau, this will require the user to either reaquire the data with longer K_on observation window or discard those data

![CRP_HD_Oligo_ready_after_stack_fitting_rawsignal](https://github.com/user-attachments/assets/81ee1448-0553-4aa9-bef8-d4a29a6c0bed)

The code will automatically export two excel file, one will contain all the exponential fitted XY value, the other is a summary of the data including the k constant for each curve and the maximum response unit within your K_on observation window (i.e. last row).
Next, the code will perform Langmuir isotherm fitting on the data, the x-axis is the concentration data, and the y axis is the corresponding maximum response RU from that concentration range. The fitting, e.g. here will take from 0.78 nM to 25 nM, this is because analyte started sticking onto the reference lane at 50 nM and above so the data is not useful at higher concentration range.

![CRP_HD_Oligo_ready_after_stack_fitting_langmuir](https://github.com/user-attachments/assets/5bb0bdf0-870c-477d-a0d9-2ed8953495a6)

The Langmuir isotherm fitting on the data will return two values: the plateau value (formerly known as maximum adsorption capacity) and the Langmuir constant (steepness). The understanding of SPR means that there is a finite amount of ligand immobilised on the surface, and the binding response will plateau once above a certain concentration of analyte being flushed across the ligand surface, this plateau region is the maximum response. By using the Langmuir isotherm equation, the plateau RU value of this curve can be found.
Affinity is defined as the concentration of an analyte that occupies 50% of the available ligand, which means half of the plateau value, having this y axis value, one can find the x axis value either by drawing a line or calcultion using the fitted Langmuir isotherm equation.
As can be seen from the figure, the plot automatically finds the half maximum response position and its corresponding x axis value which is the affinity value.
