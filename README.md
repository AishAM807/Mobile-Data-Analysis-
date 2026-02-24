# Mobile Dataset Analysis 

### Dashboard Link : SharePoint from Microsoft365

## Problem Statement
The smartphone market includes numerous models with varying specifications and different launch prices across countries. Businesses often find it difficult to evaluate how features such as model type and camera specifications influence product value and market positioning in different regions.

This project analyzes a mobile dataset containing smartphone model names, back and front camera resolutions, and launch prices in India, Pakistan, Dubai, and the United States. The goal is to compare regional pricing and device features to understand product competitiveness and support better pricing and product selection decisions.


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : Identified 30 duplicate records using Keep Duplicates to review repeated entries in the dataset. Removed all duplicate values to ensure each smartphone record is unique, enhancing the accuracy and reliability of subsequent analysis.
- Step 5 : Observed that some entries in the Launch Price (Pakistan) column were marked as "NOT Available", indicating missing pricing information for certain smartphone models.
- Step 6 : Converted launch prices from USD to PKR using the conversion factor. For example, multiplying 2259 USD × 279.59 PKR resulted in 631,129.81 PKR, which was then used to fill the missing value in the Launch Price (Pakistan) column.
- Step 7 : Cleaned the RAM column by replacing the "GB" text with a blank using the Replace Values feature, converting the column into numeric values suitable for analysis.
- Step 8 : Changed the RAM column data type from Text to Whole Number to enable numerical analysis.
- Step 9 : Applied the Trim function to remove any leading or trailing spaces, ensuring clean and consistent data.
- Step 10 : Created the first report page named "Overview" to provide a high-level view of the mobile dataset.
- Step 11 : Added two slicers: Company Name and Launch Year to enable interactive filtering.
- Step 12 : Visuals added:

	- Bar Chart: Number of models by Company.

  - Bar Chart: Average RAM by Model Name.

  - Bar Chart: Processor count by Model Name.

  - Bar Chart: Number of models by Front Camera Resolution.

  - Bar Chart: Number of models by Back Camera Resolution.
 
 # Report Snapshot (Power BI DESKTOP)


- Step 13 : Created the second report page named "Camera Resolution Details" to provide detailed insights into smartphone camera specifications.
- Step 14 : Added a table view displaying Company Name, Model Name, Front Camera Resolution, and Back Camera Resolution.
- Step 15 : Included a navigation button to go back to the Overview page for smooth report interaction.
- Step 16 : A Drill Through function has been implemented on the Model Name. This allows users to click on a model in the Overview page and be taken directly to its detailed camera specifications. Additionally, a corresponding drill-through button has been automatically generated to ensure seamless functionality.

 
 # Report Snapshot (Power BI DESKTOP)


- Step 17 : Created a third report page named "Price Analysis" to examine smartphone launch prices across regions.
- Step 18 : Added two slicers: Company Name and Launch Year for interactive filtering.
- Step 19 : Cleaned all launch price columns by:
	    - Replace text values like PKR, INR, USD, and AED with blanks to retain only numeric values.
	    - Changing the data type from Text to Whole Number to enable numerical calculations and comparisons.
- Step 20 : Created a new "Conversion Factor Table" using Chat GPT to store currency conversion rates between USD, PKR, INR, AED, and CNY.

- Step 21 : Performed data transformation in Power Query by creating custom columns for multi-currency price conversion (PKR, INR, AED, CNY) using exchange-rate logic and a centralized conversion table.
	    - PKR TO USD:
			PKR * 0.00358
	    - INR TO USD:
			INR * 0.01101
	    - AED TO USD:
			AED * 0.2723
	    - CNY TO USD:
			CNY * 0.1447

- Step 22 : Converted all newly created currency columns (PKR, INR, AED, CNY) to Decimal Number data type to ensure numerical accuracy in calculations and aggregations. 
- Step 23 : Implemented analytical bar chart reports showing average launch price (AED) segmented by model and company. 
- Step 24 : Designed a multi-currency interactive dashboard using Power BI Bookmarks, allowing users to toggle pricing analysis across different countries while reusing the same visuals, improving report efficiency and user navigation.
- Step 25 : Used Selection Pane and visual layering to replicate standardized bar chart analyses for multiple countries, supporting bookmark-based multi-currency reporting.
- Step 26 : Created and organized bookmark groups for the Price Analysis report page, including AED PA, INR PA, PKR PA, USD PA, and CNY PA.
- Step 27 : Implemented bookmark-driven navigation buttons to allow users to switch between currency analysis views directly from the dashboard.

 
 # Report Snapshot (Power BI DESKTOP)


- Step 28 : Designed a dedicated report page titled “Feature vs Price Comparison” to analyze the relationship between device specifications and pricing across multiple countries.
- Step 29 : Integrated slicers for RAM and Launch Price to enable dynamic filtering based on product configuration and price range.
- Step 30 : Implemented bookmark-driven currency switching within the Launch Price slicer to allow seamless comparison across USD, PKR, INR, AED, and CNY.
- Step 31 : Created a feature table listing Company, Model, Processor, Screen Size, Battery, and RAM, integrated with slicers and bookmarks for multi-currency analysis.
- Step 32 : Created four bookmarks to capture different Launch Price selections, enabling users to quickly toggle between price ranges.
- Step 33 : Added and layered four slicers corresponding to the bookmarks for dynamic feature-to-price filtering across multiple countries.
- Step 34 : Grouped bookmarks into a “FP Page” (Feature vs Price) collection to streamline report navigation and maintain dashboard organization.
- Step 35 : Added four bookmark navigator buttons to allow users to switch the Launch Price slicer between different countries (AED, INR, PKR, USD, CNY).
 

 # Report Snapshot (Power BI DESKTOP)


- Step 36 : Created a calculated column using the CONCATENATE DAX function to combine Company Name and Model Name into a single identifier.

Following DAX expression was written to add column, 
		
			Concatinate Column = CONCATENATE('Mobile Data Set'[Company Name], 'Mobile Data Set'[Model Name])


- Step 37 : Created a calculated column to determine the length of the Mobile Weight field using DAX.

Following DAX expression was written to add column,

			length_mobile weight = LEN('Mobile Data Set'[Mobile Weight])

- Step 38 : Extracted numeric values from the Mobile Weight column using DAX IF logic for clean and accurate feature analysis.

 Following DAX expression was written to add column,

			Numerical_mobile _weight = IF('Mobile Data Set'[length_mobile weight] = 4, LEFT('Mobile Data Set'[Mobile Weight], 3), LEFT('Mobile Data Set'[Mobile Weight], 5))

- Step 39 : Created a “Summarize Table” using the SUMMARIZE DAX function to aggregate key product and pricing metrics.


 Following DAX expression was written to add new table, 

			SUMMERIZE Table = SUMMARIZE('Mobile Data Set', 'Mobile Data Set'[Company Name], 'Mobile Data Set'[Model Name], "Average RAM", AVERAGE('Mobile  Data Set'[RAM (GB)]), "Average USD", AVERAGE('Mobile Data Set'[Launched Price (USA)(USD)]), "Average Mobile Weight", 						  AVERAGE('Mobile Data Set'[Numerical_mobile _weight]))



- Step 40 : Created new report view page "DAX Function" to show matrix visual. 


Following DAX expression was written to add new table, 

