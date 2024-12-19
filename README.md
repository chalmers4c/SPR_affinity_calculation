# SPR_affinity_calculation
The code aims to import an excel file, perform fit on the K_on region of the SPR data, find the maximum response unit from fitting across multiple concentration of analyte, then use Langmuir isotherm equation to find the maximum response, then extract affinity data from this fit.
# Requirement
- Use reference subtracted data, some python knowledge is needed, particularly the dataframe structure.
- Ready to use excel file, it should be organised such that Column A is Time (s) (x-axis), Column B is the response unit (RU) (y-axis), Column C is Category data (which concentration this data point belongs to)
- Some packages will be imported that may require you to install them
# Example
With an excel like below, it is ready to be imported into this code

![image](https://github.com/user-attachments/assets/26107181-08eb-4925-b9b5-e93c62443d9e)

The code will perform a combined function contains exponential decay and straight line, and each concentration is fitted.
