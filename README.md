# PerSquareMile Project
This README provides a high-level overview of the PerSquareMile data product, which uses an arbitrary one square mile grid laid over California to prioritize park needs along with other priorities. The simple grid has proven to have substantial explanatory power, allowing agency staff, park advocates, and others to quickly zero in on the areas where new parks would have the biggest impact.

PerSquareMile is a classically utilitarian tool — where can the fewest new parks serve the most people who currently lack them? 

Grid cells are attributed with numbers of people in various filters – total population, population more than a half-mile from a park, population in DAC/SDAC areas, etc. Plus other attributes as needed by any specific application, such as biodiversity score or total park acres.

## Who created the PSM?

PerSquareMile is a joint production of Jon Christensen at UCLA and GreenInfo Network, whose work was led and driven by Dan Rademacher from 2022 to 2025. The PSM tool specifically came out of work done on a website called [ParkAccess.org](http://ParkAccess.org). That work was funded by the Resources Legacy Fund and The Wilderness Society. As part of that project, we developed very high resolution population data to estimate park access at a granular level. You can read more about [the methods of that project here](https://parkaccess.org/about/).

We developed a Memorandum of Understanding specifying that the work was co-owned by GreenInfo and Jon Christensen. We agreed in 2025 to open-source the methods and data, while continuing to advocate for using the methods in our own projects. This is similar to the successful approach GreenInfo Network has taken with the California Protected Areas Database (https://calands.org) and the California School Campus Database (https://californiaschoolcampusdatabase.org)

## Uses of PSM

### The first use case: Estimating statewide park development needs

In November 2022, Katherine Toy, who was then California's undersecretary for equitable access, asked us if we could tell her how many parks would need to be built to reduce by half the number of Californians who live farther than a half mile from a park.

We had 30m resolution data estimating where everyone in California lived, so we knew the location of everyone who lacked a nearby park. But we hadn’t assessed their distribution in any way. If those people were evenly distributed across the state, you might need thousands of parks to reach them. If they were concentrated in a few areas, you might need only hundreds.

The lightbulb moment was when we realized that if we aggregated our 30m point data up to a 1 mile grid, we could just sort by no-park population and see how many grid cells would be needed to hit any number of people you might want to serve. Theoretically, a park in the center of any grid cell would serve those people. (Importantly, this is a coarse prioritization tool, not a site selection or feasibility assessment tool.)

We found that just 1,313 parks would be needed to serve 4 million of the 8 million Californians who lack a nearby park.

Though Katherine Toy left her role and the momentum in Sacramento declined, we could see that the PerSquareMile tool had value.

We later created this general PSM slide deck based on the original work focused on CNRA: [PerSquareMile - Access Research Project](https://docs.google.com/presentation/d/1JjlhfO0yIBYdmeqzQP1r8sBy2gl6zQdx9ocjsTiXQMc/edit?slide=id.g18009c5ac17_1_0#slide=id.g18009c5ac17_1_0)

### RLF / WCB Pilot: Where do biodiversity and low-access overlap in Southern California?

Jon Christensen was working with Resources Legacy Fund and others to successfully persuade the state Wildlife Conservation Board to include equity in their funding guidelines. Historically, WCB focused on biodiversity and habitat protection. Now, they would consider equity for people as well.

Anecdotally, it is often assumed that communities who lack parks don’t live in areas with high biodiversity. That seems sensible — Aren’t park-poor neighborhoods mostly concrete?

To test that, we did an initial assessment of the top 1,313 PSM grid cells mentioned above, and we found that over 700 of them are in areas with above-average biodiversity according to one of the state’s preferred metrics.

Our frequent collaborators at the Resources Legacy Fund proposed a pilot project to use the PSM with the biodiversity overlay to find and fund planning projects in Southern California that advance both equitable access and biodiversity.

As of Fall 2025, RLF and Jon Christensen are in the process of working with partners to develop potential projects.

### OLIN City of Los Angeles Park Needs Assessment

The most public and prominent use of the PSM has been the City of Los Angeles Park Needs Assessment. For this project, Jon Christensen approached the landscape architecture firm OLIN specifically about working with us to get the benefit of the PSM tool.

We used the PSM to successfully prioritize 36 locations in the city where new parks would most benefit Angelenos who lack nearby parks or live in areas with insufficient parks for nearby population.

The simplicity of the PSM data allowed us to create flexible Google Sheets workbooks to model multiple scenarios where we target various levels of reduction in populations who lack parks, who live in DAC or SDAC or CES Exposure areas and lack parks, or in areas without enough parks (low PPK), etc. 

This allowed the OLIN team to go back to the steering committee and show these results and get guidance from them on what to prioritize. Their direction was a 25% reduction in the SDAC or CES75+ population who either lacks a park within a halfmile or lives in an area with less than 3 acres PPK.

Once we had the 36 grid cells, we were then able to use schools and parcel data to see what opportunities there might be within those grid cells. This step was very compelling for folks in understanding that every grid cell had some opportunity that could increase access without undertaking expensive land acquisition.

## Read methods and download some data!


## Known Challenges

### Latest data is limited to Southern California

As of October 2025, we have developed PSM grids for the following:

* 2023 ACS data in seven SoCal Counties: Los Angeles, Orange, Riverside, San Bernardino, Ventura, Imperial, and San Diego.   
* 2019 ACS data for all of California.

So the only statewide data is from 2019, and there’s currently no identified budget to update the statewide data to newer ACS data. 

### No automation in data production

The first version of this data, created in 2022, was very much a prototype, built ad hoc as we explored the idea of the grid. This was a statewide dataset, but one based on 2019 ACS data and 2020 or 2021 CPAD data, since it was all based on existing data from the [ParkAccess.org](http://ParkAccess.org) project.

The data for [ParkAccess.org](http://ParkAccess.org) is produced in a highly automated and repeatable way, but the PerSquareMileGrid as a derivative product is made with manual GIS processes. In 2025, we made improved versions with more current data, but due to capacity limitations, we did this only for subsets of the state — the 6 counties that make up Southern California. Those were also done with manual GIS processing. The methods are documented but not scripted.

### Upstream Human Settlements Layer is no longer maintained by Meta

Any update using current ACS data but would continue to use “People Point” 30m grid data from 2016, the most recent data available from Meta (which has subsequently abandoned the work). In the specific uses in Los Angeles and select locations in Southern California, we manually reviewed the data and determined that the changes in the built environment since 2016 were not material to our findings. 

We did this by looking at Census Block Groups with no People Points (representing new construction in greenfield or brownfield areas) and People Points in areas reporting no population (less common, uncertain of cause). In our specific cases, there was not substantial evidence of new construction in the locations we cared about, though there was such evidence in other areas around Southern California. And there might be more divergence statewide.

The best path forward in the future would be to replace the Meta data with another source of high resolution population data that is still regularly updated. 