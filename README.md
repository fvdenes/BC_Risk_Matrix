# Mig Birds Matrix / BC VRI models

Welcome to Nicole's BC models built in collaboration with Canfor and West Fraser!

BAM (rep: Nicole Barker, supervised by Erin Bayne) was recruited to collaborate 
on a project with BC forest products companies (reps: Kari Stuart-Smith of Canfor 
and Laura Trout of West Fraser), and CWS (rep: Mark Drever). 

The primary goal was to evaluate a Stand Ranking Matrix created by the BC 
forest products companies. 

The secondary goal was to create an alternative to the Stand Ranking Matrix, 
by creating maps of predicted total bird density at the scale of Vegetation
Resource Inventory (VRI) polygons. 

## Why are you looking at these files? 

If you're part of the BAM team, maybe Nicole suggested these files could teach you about working with the BAM dataset. Or maybe you're running similar analyses in a different region. Either way, here's what you need to know: 

1. Access the Dropbox folder containing all data files. 
2a. If possible, use RMarkdown via RStudio.
2b. If RMarkdown isn't possible, you can knit my scripts with tangle=T. e.g., 
`library(knitr)`
`knit("munge/00.02.FixorCalculateOffsets.Rmd", tangle=T)`

3. Fork the Repo into your own GitHub profile 

## Reproducing these Analyses
To repeat the work, follow this overall workflow:

Run scripts from directories in the following order:
	  * MUNGE: Pre-process data using munge scripts	
	  * SRC: Run analysis scripts saved in the src folder 

There are readme files within the munge and src folders with more specific details but the generally applicable steps are: 
1. The first two chunks in any Rmd file will be setup chunks. Chunk 1 has:

	`require(knitr) # loads knitr package`
	
	`opts_knit$set(root.dir = '..') #sets reference directory one level up from where the current file is (don't worry about this too much; but it is important for re-running scripts)`

-----------
# Currently considering taking projectTemplate out of the equation. I'll need to update this readme to reflect the new workflow. 
-----------

I also need to adjust for the fact that data is now stored on Dropbox while scripts are elsewhere. Relative directories become a bit more challenging then. 


2. Chunk 2 is:

    `require('ProjectTemplate') #absolutely essential!`

    `load.project() #essential!`

The second line of code prompts some automated processing set up by Nicole for this project, and you'll see several messages. Depending on the project configuration, this may include: 

* Reading in the global configuration file contained in `config`.
* Loading any R scripts in the `lib` directory
* Loading any R packages listed in the configuration file. (load_libraries set to TRUE)
* Reading in any datasets stored in `data` or `cache`.  (if data_loading and cache_loading set to TRUE)
* Preprocessing data using the files in the `munge` directory. (if munging set to TRUE)

Nicole turned off many of the automatic loading because of large file sizes and lengthy pre-processing. 

3. Then run the remaining code by line or by chunk, as per your preference. Again, refer to the munge and src readmes for more details. 


### What is ProjectTemplate?
For more about the ProjectTemplate package, see http://projecttemplate.net
