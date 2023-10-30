
# WORKFLOW

## Tasks

(FolderOrganization)=

### Folder Organization

#### Assignment Folders Dropbox vs Github

The difference between Github and Dropbox will become clearer after [Github](Tools:Github), but we should note a few things beforehand. The two are fundamentally different in their purposes: Dropbox is great at storing huge amounts of data in the cloud, while Github excels at storing multiple versions of your code. In practice, this means that you will have a Dropbox folder with all your data and one Github folder with all your codes. Your plots, pictures, and tables can go in either.

Currently, we prefer to create an organization in GitHub that manages entire project. You can have one repository for analysis and then a final repository called writing that only stores your final tex code for presentation, paper draft, final graphs and tables. We will explain this in detail in [Code](Code) and [Tools](Tools) the best practices of creating all this output. 


#### Example Directory
We recommend adopting the directory structure outlined by Gentzkow & Shapiro in their handbook, [Code and Data for the Social Sciences](https://web.stanford.edu/~gentzkow/research/CodeAndData.pdf). This structure is well-suited for comprehensive empirical research projects. Below is an example of one of our projects that follows that stracture. 

![alt text](Figures/DirExample.png "Folder Stracture")

These different folders serve following purpose:
1. **Comments:** This folder serves as a repository for feedback and insights gathered throughout the course of your project, sourced from interactions with fellow academics. This could encompass input received during seminars or workshops, as well as informal discussions with colleagues within your department. In the field of economics, actively seeking and integrating feedback from peers is a vital practice for refining and enhancing the quality of your work, ultimately contributing to the production of a well-polished paper.

2. **Context:** This folder outlines your project's motivation and research design. It contains detailed background information on your data and the policy you are studying. For instance, in the picture folder above, we study randomized Valued Added Tax audits in Pakistan and our context folder stores details such as audit policy documents and how audits were conducted. For example, in the displayed directory structure, the project investigates randomized Value Added Tax (VAT) audits in Pakistan. The "Context" folder, therefore, contains essential documents like audit policy materials and descriptions of audit procedures, ensuring all crucial background and methodological details are comprehensively documented and easily accessible.
3. **Empirics:** This central folder is designated for storing data and, if applicable, code (especially when using Dropbox for code storage). It typically encompasses three subfolders: Build, Analysis, and Log.
    - **Build:** This subfolder is further divided into three categories:
        - **Input:** Here, you store all the raw data collected for your project.
        - **Code:** This is where the code for preparing the final dataset, ready for analysis, is kept. Tasks such as merging multiple files, standardizing variable names, and cleaning strings are performed to produce a clean and analyzable dataset.
         - **Output:** The final, cleaned dataset is stored here, ready for further analysis.

    - **Analysis:** Within this subfolder, you'll find two more categories:
        - **Code:** All code related to your analysis is stored here.
        - **Output:** This contains folders for storing visualizations (Pictures) and data tables. We provide guidance in the [Tools](#Tools:STATA) section on how to write STATA code that directly produces LaTeX files for your tables.
    - **Log:** This subfolder is used to store log files, although its specific contents and organization might vary depending on your project's needs.
4. **Funding:** Funding folders tracks your funding resources and applications.
5. Then you can have extra folders depending on your needs such as Presentation folder that store Latex code for your presentations, Writing folder stores Latex code for the draft of your paper and Readings folder stores all papers that are relevant to your project. 

If you store your code on GitHub, you can create further folders for different types of codes such as 

![](Figures/GitHhubFolders.png)

Once you create a this folder stracture, you should write a master file that stores paths of these foldes for all of your co-authors. This approach eliminates the need to manually configure paths, enabling anyone to generate tables or figures by simply running the master file, followed by any other code file, directly on their computer. Below, you will find the STATA code for the master file used in our Pakistan Audits Project.

```bash
version 16
set more off

***************************************************************************************************
* THIS FILE SETS ALL THE PATHS YOU NEED FOR THE PAKISTAN AUDIT PROJECT
* TO ADD YOURSELF, ASK STATA WHAT YOUR USERNAME IS (TYPE di "`c(username)'") AND
* ADD ANOTHER `ELSE IF' CONDITION BELOW THE OTHERS
***************************************************************************************************

/* PRELIMINARIES */
*------------------

if "`c(username)'" == "michaelbest" {
	global github "/Users/michaelbest/Documents/GitHub/PakistanAudits/"
	global dropbox "/Users/michaelbest/Dropbox/Pakistan Audit/"
} 
else if "`c(username)'" == "mb5061" {
	global github "/Users/mb5061/Documents/GitHub/PakistanAudits"
	global dropbox "/Users/mb5061/Library/CloudStorage/Dropbox/Pakistan Audit"
} 
else if "`c(username)'" == "muhammadbashir" {
	global github "/Users/muhammadbashir/Documents/GitHub/PakistanAudits"
	global dropbox "/Users/muhammadbashir/Dropbox (Personal)/Pakistan Audit"
} 
else if "`c(username)'" == "RBTG V2" {
	global github "/Users/RBTG V2/Documents/GitHub/PakistanAudits/"
	global dropbox "/Users/RBTG V2/Dropbox/Pakistan Audit/"
}
else {
	di _n as error "YOU DON'T SEEM TO BE ONE OF THE USERS LISTED, PLEASE CHECK YOUR C(USERNAME)" _n
}
	
global project_code	"${github}/Code"
global project_data "${dropbox}/Empirics/Build/Output"
global project_pics "${dropbox}/Empirics/Analysis/Output/Pictures"
global project_tabs "${dropbox}/Empirics/Analysis/Output/Tables"
global project_log	"${github}/Logs"

```
This file defines STATA globals storing paths to all important folders. If I want to read final cleaned data that is stored in output folder inside build, I would write 

```bash
use     "$project_data/PakAudit.dta", clear
```
Note that you use `$` sign to refer to globals inside any Do file. For more details on globals in STATA, read [this](https://www.stata.com/manuals/pmacro.pdf) manual on STATA website. 







#### Make Files

Once you reach towards final stages of your project, each folder should have a “main” file that calls the other scripts/functions from the folder. A folder can quickly grow into having multiple files, and the master file should help one to figure out the connections between them, e.g., in what order each file should be called. An example in Stata:

![alt text](Figures/MainFile.png "STATA Master File")

Beyond the “master code” already mentioned, ideally, a code directory would contain a “ReadMe.pdf” that describes briefly the codes and their connection, as well as the conclusions met and the main evidence found. Even though Github stores all the versions of our code, it is useful to keep at least the last version of the code in an “Archive” folder, to avoid going through the different versions of Git. If you use generic auxiliary functions in many of your codes, they should go in an “AuxFunctions” folder. The following picture illustrates an example directory:

![alt text](Figures/ExampleDir.png "ExampleDir")

## Project Manual

## Version Control








