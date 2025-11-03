# PerSquareMile Data for Southern California

## Accessing the data

* Download [GDB with PSM data](https://drive.google.com/file/d/1wRh-kwsfOluzV5YxHZInbBKLh2LhgxOd/view?usp=drive_link)  
* Layer name: Grid\_SoCal

Note this file also includes a layer called “FbPts\_SoCal” that is the raw data used to estimate who lives where. In principle, this could be used to create alternative estimates of populations near parks or within other areas of interest. See the [readme] for more backgorund about the data and methods.

## Schema and data dictionary

| Field Name | Definition |
| :---- | :---- |
| GridID | Numeric ID of the grid cell |
| SpBioRnkEco | Plurality value for ACE (as defined above), so the cell is tagged with the score that has the highest percentage in that cell. |
| TotPop\_ACS2023 | Total population of cell, used for PPK calculations if needed |
| ParkNo\_ACS2023 | Population who live further than a halfmile from a park, based on Euclidean distance |
| ParksNoCESYes\_ACS2023 | Population who live in a CES75+ tract and are further than a halfmile from a park, based on Euclidean distance |
| ParksNoDisadvYes\_ACS2023 | Population who live in a Census Block Group with Median Household income 80% or less of statewide, and who live further than a halfmile from a park, based on Euclidean distance |
| ParksNoSevDisadvYes\_ACS2023 | Population who live in a Census Block Group with Median Household income 60% or less of statewide, and who live further than a halfmile from a park, based on Euclidean distance |
| PkNoDisYesCESYes\_ACS2023 | Population who live in a Census Block Group with Median Household income 80% or less of statewide, a CES75+ tract, and who live further than a halfmile from a park, based on Euclidean distance |
| PkNoSevDisYesCESYes\_ACS2023 | Population who live in a Census Block Group with Median Household income 60% or less of statewide, a CES75+ tract, and who live further than a halfmile from a park, based on Euclidean distance |
| ParkAc\_CPAD | Acres of CPAD lands in the grid cell, used for PPK calculations if needed |

## **Source Data**

The data used in the tool consisted of:

* Data for species biodiversity from California Department of Fish and Wildlife’s Areas of Conservation Emphasis (ACE) **Combined Biodiversity Summary**  
  * About this data: [Areas of Conservation Emphasis (ACE)](https://wildlife.ca.gov/Data/Analysis/ACE)   
  * ACE includes many layers. We used the default rollup layer: “Combined (Terr \+ Aq) Biodiversity Summary \- ACE \[ds2769\]”. [Layer metadata](https://map.dfg.ca.gov/metadata/ds2769.html)  
  * Data was filtered based on the field SpBioRnkEco to:  
    * Rank 4 supports a significant number of species, rare species or important habitat.  
    * Rank 5 represents the most significant locations, often with rare, endemic or highly vulnerable species.  
  * The California Department of Fish and Wildlife (CDFW) Areas of Conservation Emphasis (ACE) Species Biodiversity dataset is a summary of the best available information on species biodiversity in California, and is based on species occurrence and distribution information for amphibians, aquatic macroinvertebrates, birds, fish, mammals, plants, and reptiles. It synthesizes information from the ACE Terrestrial Biodiversity Summary, which is compiled by hexagon, and the Aquatic Biodiversity Summary, which is compiled by watershed.   
* Data for connectivity from The Nature Conservancy's (TNC) Omniscape algorithm, Intensified, Channelized and Diffused.  
  * About this data: [Data viewer](https://www.arcgis.com/apps/webappviewer/index.html?id=3cbb9454372e43ffac44b9dda07b5551)  
  * This analysis represents a wall-to-wall picture of regional habitat connectivity for plant and animal species whose movement is inhibited by developed or agricultural land uses.   
  * Intensified which is like a superhighway for movement. Lots of animals or things are moving through one area, making it very busy. Imagine a big road where many cars are driving fast in the same direction.  
  * Channelized which is like a winding river or a narrow path. Movement is squeezed into a certain space, so things can only go through specific routes. Think of a sidewalk that people must use because there’s a fence on both sides.  
  * Diffuse which is like a gentle breeze spreading in all directions. Movement is slow and spread out, with no clear paths. Imagine dandelion seeds floating everywhere in the wind instead of all following the same road.  
* CalEnviroScreen  
  * About this data: [CalEnviroScreen 4.0 \- OEHHA](https://oehha.ca.gov/calenviroscreen/report/calenviroscreen-40)   
  * CES 4.0 Percentile, filtered to 75 and higher  
  * CalEnviroScreen is a mapping tool that helps identify California communities that are most affected by many sources of pollution, and where people are often especially vulnerable to pollution’s effects. It uses environmental, health, and socioeconomic information to produce scores for every census tract in the state.  
  * The scores are mapped so that different communities can be compared. An area with a high score is one that experiences a higher pollution burden than areas with low scores.  
* CPAD (release 2024b, December 2024\)  
  * About this data: [California Protected Areas Database (CPAD)](https://calands.org/cpad/)   
  * The California Protected Areas Database (CPAD) is a GIS database of lands that are owned in fee and protected for open space purposes by over 1,000 public agencies or non-profit organizations. It is the authoritative GIS database of parks and open space in California.  
  * We used CPAD units to query lands within county boundaries for the counties in the study area.  
  * Units are displayed by access type (Open Access, Restricted Access, No Public Access, and Unknown Access).  
* Disadvantaged and Severely Disadvantaged Communities (DAC/SDAC)  
  * DAC and SDAC were defined using percentages of the statewide Median Household Income (MHHI), which is the standard method used by the California Department of Parks and Recreation for the Statewide Parks Program, a long-term funding program to prioritize park improvements in higher need areas. DAC is defined as 80% of California’s Median Household Income, while SDAC is defined as 60%.  
  * Further documentation is available on [the Methods page of ParksforCalifornia.org](http://ParksforCalifornia.org), under Data Definitions at the entries for Disadvantaged Community and Severely Disadvantaged Community.  
* PerSquareMile  
  * GreenInfo Network and UCLA’s Luskin Center for Innovation developed this data as a prototype prioritization product. The data defines a continuous one-square mile grid that covers all of California.   
  * Grid cells are tagged with the plurality value for ACE (as defined above), so the cell is tagged with the score that has the highest percentage in that cell.  
  * Grid cells are also attributed with the population of people who have no park within a halfmile, based on halfmile Euclidean buffers around parks in CPAD 2024b (defined above) and using the latest population and household data from the American Community Survey 5 year average (2019-2023).  
  * Grid cells contain variant values of households that lack a park within a halfmile and are within a DAC/SDAC or above 75th percentile of CalEnviroscreen, as defined above.  
* Parcel data  
  * Since this project is funded by WCB/CNRA, GreenInfo used parcel data accessible through our work with CNRA for the seven counties in Southern California. Unfortunately, license restrictions prevent us from sharing this data.  
  * To limit the number of parcels used in the application, we selected parcels that are within 1 mile of the PerSquareMile grids that represent areas with above average biodiversity and people who lack parks (spbiornkeco \>= 4 AND pop\_ngbdoa\_eq0\>0 ). To mitigate issues with data size, we also limited to parcels that are 5 acres in size or larger, though this is likely to change due to user feedback.

## Example PerSquareMile Filters

Examples of some filters applied to the PSM grid:

* Areas with above average biodiversity and people who lack parks in CES75 plus or SDAC areas `("ParksNoSevDisadvYes_ACS2023">0 or "ParksNoCESYes_ACS2023">0) and "SpBioRnkEco" >=4`  
* Areas with above average biodiversity and people who lack parks and are in CES75+ areas: `"ParksNoCESYes_ACS2023">0 and "SpBioRnkEco" >=4`  
* Areas with above average biodiversity and people who lack parks in Severely Disadvantaged Area Communities (SDAC): `"ParksNoSevDisadvYes_ACS2023">0 and "SpBioRnkEco" >=4`  
* Areas with above average biodiversity and people who lack parks in Disadvantaged Area Communities  
  `"ParksNoDisadvYes_ACS2023">0 and "SpBioRnkEco" >=4`  
* Areas with above average biodiversity and people who lack parks  
  `"ParksNo_ACS2023">0 and "SpBioRnkEco" >=4`