# Mobile Dataset Analysis 

### Dashboard Link : 

### Data Source: SharePoint from Microsoft365

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

 
<img width="867" height="488" alt="Image" src="https://github.com/user-attachments/assets/3786eb11-60f2-46dd-bc9e-6e1abd03b66b" />


- Step 13 : Created the second report page named "Camera Resolution Details" to provide detailed insights into smartphone camera specifications.
- Step 14 : Added a table view displaying Company Name, Model Name, Front Camera Resolution, and Back Camera Resolution.
- Step 15 : Included a navigation button to go back to the Overview page for smooth report interaction.
- Step 16 : A Drill Through function has been implemented on the Model Name. This allows users to click on a model in the Overview page and be taken directly to its detailed camera specifications. Additionally, a corresponding drill-through button has been automatically generated to ensure seamless functionality.

 
 # Report Snapshot (Power BI DESKTOP)


<img width="872" height="482" alt="Image" src="https://github.com/user-attachments/assets/a962deb4-7c5c-4ff4-905c-30660d5794ce" />

- Step 17 : Created a third report page named "Price Analysis" to examine smartphone launch prices across regions.
- Step 18 : Added two slicers: Company Name and Launch Year for interactive filtering.
- Step 19 : Cleaned all launch price columns by:
	    - Replace text values like PKR, INR, USD, and AED with blanks to retain only numeric values.
	    - Changing the data type from Text to Whole Number to enable numerical calculations and comparisons.
- Step 20 : Created a new "Conversion Factor Table" using Chat GPT to store currency conversion rates between USD, PKR, INR, AED, and CNY.

<img width="249" height="107" alt="Image" src="https://github.com/user-attachments/assets/7e2a5ab5-191e-419c-8b68-467f36883702" />

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


<img width="873" height="482" alt="Image" src="https://github.com/user-attachments/assets/bf76e9b7-e72c-41e5-af2f-96af881e5223" />


- Step 28 : Designed a dedicated report page titled “Feature vs Price Comparison” to analyze the relationship between device specifications and pricing across multiple countries.
- Step 29 : Integrated slicers for RAM and Launch Price to enable dynamic filtering based on product configuration and price range.
- Step 30 : Implemented bookmark-driven currency switching within the Launch Price slicer to allow seamless comparison across USD, PKR, INR, AED, and CNY.
- Step 31 : Created a feature table listing Company, Model, Processor, Screen Size, Battery, and RAM, integrated with slicers and bookmarks for multi-currency analysis.
- Step 32 : Created four bookmarks to capture different Launch Price selections, enabling users to quickly toggle between price ranges.
- Step 33 : Added and layered four slicers corresponding to the bookmarks for dynamic feature-to-price filtering across multiple countries.
- Step 34 : Grouped bookmarks into a “FP Page” (Feature vs Price) collection to streamline report navigation and maintain dashboard organization.
- Step 35 : Added four bookmark navigator buttons to allow users to switch the Launch Price slicer between different countries (AED, INR, PKR, USD, CNY).
 

 # Report Snapshot (Power BI DESKTOP)

 <img width="880" height="489" alt="Image" src="https://github.com/user-attachments/assets/8b3e6e09-f1f0-4919-a645-efc424e380d9" />


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


<img width="665" height="463" alt="Image" src="https://github.com/user-attachments/assets/7ddae726-ff98-4aaf-814d-cabbac02a0bb" />


- Step 40 : Created new report view page "DAX Function" to show matrix visual. 


<img width="875" height="488" alt="Image" src="https://github.com/user-attachments/assets/bd302d26-75b3-4e8e-850d-79074163cae8" />


- Step 41 : The report was then published to Power BI Service.

# Insights:
A five pages report was created on Power BI Desktop & it was then published to Power BI Service.

### [1] Overview:
- Oppo has the most models (115) → Huawei the least (40).

- All top models feature 16 GB RAM.

- Highest processor variation is 3 (Pad 2 256GB).

- Most common front camera resolutions: 32MP (204) and 16MP (201).

- Most common back camera resolution: 50MP (180), with high-end 108MP only in 35 models.

### [2] Camera Resolution :

Total Records: 16 mobile/tablet models.

Front Camera:

- Highest: 12MP (Apple iPad 10.2-inch models)

- Lowest: 5MP (Honor Pad X series, Infinix models)

- Most common: 8MP (7 models, mostly Oppo, Nokia, POCO)

Back Camera:

- Highest: 8MP + 2MP (Oppo A3x 128GB/4G 128GB and 256GB)

- Standard: 8MP (majority of devices, 11 models)

Brand Insights:

- Oppo: 4 models, all 8MP front, back 8MP + 2MP for 3 models

- Apple: 4 models, front 7–12MP, back 8MP

- Honor: 2 models, front 5MP, back 8MP

- Infinix: 2 models, front 5MP, back 8MP

- Nokia: 1 model, front & back 8MP

- POCO: 2 models, front & back 8MP

Notable Patterns:

- Tablets tend to have slightly lower front cameras (5–7MP) compared to smartphones (8–12MP).

- Oppo models include dual back cameras for higher variants.

- Apple maintains high front camera consistency for higher-end models.

- The most expensive model is Mate XT 512GB at 10.1K ADE, followed by Mate XT 256GB at 10.5K ADE.

- Models like Mate X2, X3, X6 all have the same average launch price of 10K ADE, showing a premium range for Huawei Mate X series.

- The Galaxy Z Fold6 and Fold5 series range from 7K–8.7K ADE, indicating Samsung’s foldable devices are priced slightly lower than Huawei’s top-tier Mate series.

- Other notable models like Magic V series and Pixel 9 Pro Fold hover around 6.2K–7K ADE, placing them mid-tier in this analysis.

### [2] Price Analysis : 
Launch Price ADE:

- The Mate XT 512GB leads significantly at 11.10K ADE, followed closely by Mate XT 256GB at 10.50K. Huawei's Mate series dominates the top spots, suggesting a premium flagship lineup strategy.
  
Huawei — 4.15K leads the entire market. This is driven by the Mate XT series (10.5K–11.1K) and multiple Mate X variants, showing a bold bet on ultra-premium foldables and flagship devices.

Sony — 4.03K is remarkably close to Huawei despite having fewer visible models in the model chart, suggesting Sony maintains a tight, consistently high-priced portfolio with little budget dilution.

Apple — 3.68K comes in third. Given Apple's global dominance in brand value, this ranking suggests the ADE currency or market region may skew toward models where Apple is slightly undercut by Sony/Huawei flagships.

Launch Price INR:

- In INR, Apple leads at 103.00K, overtaking Huawei (102.44K) and Sony (91.67K). This is a notable flip from the ADE view, where Huawei ranked #1 — suggesting Apple's India pricing strategy or currency conversion rates position it slightly higher in the Indian market.
  
- Samsung (63.61K), Xiaomi (57.26K), Honor (48.85K), Oppo (46.49K), OnePlus (45.73K), and iQOO (44.00K) are all crammed within a ~20K range — the most fiercely competitive pricing band in the Indian market. For consumers, these brands offer near-identical price points, making specs and brand perception the deciding factor.

### [3] Feature v/s Price comparision : 
- It lets you filter devices by RAM (1–16 GB) and Launch Price in PKR (15,999–631,130) to compare specs side by side — a powerful tool for value analysis across models.
  
- iPhone X 64GB and 256GB share identical specs — same weight (174g), screen (5.8"), processor (A11 Bionic), battery (2,716mAh), and RAM (3GB). The only difference is storage.
  
- iPhone XR across all three variants (64/128/256GB) is similarly identical in every spec column.
  
- Largest screen at 7.9 inches

- Heaviest at 300.5g (nearly double the iPhone X)
  
- Biggest battery at 5,124mAh — almost double the iPhone X's 2,716mAh.

### [4] Matrix visual using DAX:
- iQOO: $399 → 538g (heaviest, cheapest)
- Honor: $607 → 284g
- Apple: $1,028 → 258g
- Huawei: $1,112 → 222g
- Google: $755 → 189g (lightest premium brand)

📊 Brand Quadrant Summary:
- QuadrantBrands💎 
- Premium Heavy SpendersHuawei, 
- Apple🎯 Value RAM ChampionsXiaomi, 
- OnePlus, 
- Oppo💼 Mid-Market BalancedSamsung, 
- Google, 
- Honor🛒 Budget AccessibleRealme, 
- Infinix, 
- POCO, 
- Lenovo⚠️ 
- Data AnomalyNokia
- Apple & Huawei — charge premium, keep RAM lean, focus on optimization & experience
- Xiaomi, OnePlus & Oppo — compete on raw specs per dollar, RAM-heavy strategy
- Google — premium price but lightest devices, minimalist hardware approach

