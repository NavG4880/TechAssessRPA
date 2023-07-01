PLANIT Assessment:
===================

Description: To Read the input excel file, save in data table and process it on web form of UiPath RPA challenge web page and submit the form. 

Additional consideration taken care as part of this challenge:
==============================================================
1) Check if input excel sheet is having NO Data, then log the exception as business exception and complete the process.
2) Check each field data format in Excel and log it if any data format is not correct for example , email id format is not correct or phone number is not 11 digits numeric data... since if we will enter wrong data on challenge page than our result will degrade, but for demo purpose i am just logging it in log and proceeding further in process.

How to run this project :
========================
- Download the zip file from Github.
- Extract complete folder.
- Open Main.Xaml in UiPath studio application community edition.
- Run/Debug the project in UiPath Studio.
- Note: Uipath extension should be pre-enabled in the chrome on which this process will execute.


Project developed using RE Framework.
====================================
* Uses *State Machine* layout for the phases of automation project.
* Offers high level logging, exception handling and recovery.
* Keeps external settings in *Config.xlsx* file stored in Data folder of the project.
* Takes screenshots in case of system exceptions and on completion of the RPA challenge.


### How It Works ###
====================

 1. **INITIALIZE PROCESS**
 + ./Framework/*InitiAllSettings* - Load configuration data from Config.xlsx file and from assets
 + ./Framework/*KillAllProcesses* - Kill any open instance of Chrome and Excel

 2. **MAIN PROCESSING**
 + *Process* - Process invoke other workflow of "ReadInputExcel" related to the process being automated 
 + *ReadInputExcel* - Reads the Input excel file of employees data and store it in Data table, checks if excel is empty else invokes other 
workflow "ProcessDataTable" and further "FormFillAndSubmit" workflow.
 + *ProcessDataTable* - will check format of each data field in the data table to log a message if format is not correct for any field.
 + *FormFillAndSubmit* - will open the RPA challenge web page than will read each row of Data table and fill the form by entering the data for respective field on web form from data table and submit the form.
 + *TakeScreenShot* - will take the screen shot when ever this workflow is invoked anywhere in the automation project and will store in Screenshot folder in project.

 3. **END PROCESS**
 + ./Framework/*CloseAllApplications* - closes applications used throughout the process and logs if there was any exception of BUsiness exception type or system exception type.


