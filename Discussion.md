**Motivation: have a plasmid library numbered chronologically so we are not at risk of losing/misplacing our clones.**

**Perks: The google spreadsheet is downloadable in CSV format so we can parse it to do other useful things!**

Some questions for everyone:

    - Do we want both empty plasmids and plasmids with inserts in the same library?

**Lucelenie**:
Yes. Having multiple inventories/libraries complicates things. A general plasmid library with the option/column to choose between the plasmid being an ‘empty vector’ or ‘plasmid with insert’ is less complicated.

**John**:
Pros: Reduced overhead and technical debt since everything is in one library. Guaranteed coverage of all plasmids (rather than having a library for plasmids with inserts and no library for empty plasmids to start with).
Cons: Increased complications every time we want to do a cloning experiment because we are always cherry-picking a set of cloning vectors, instead of picking a library or block. Then again, we might always be cherry-picking, so this may not be problematic if we just have one "cherry picking" script or protocol.

**Mehtap**:
I think there is no harm having them together.

    - Do we want to have a uniform concentration in the plasmid library?

**Lucelenie**:
The main source for storing plasmids should be glycerol stocks. Different plasmids will have different DNA yields so if we want to have a uniform concentration we will need to make aliquots of DNA preps. I don’t think is necessary to have a uniform concentration if we make sure to have glycerol stocks.

**John**:
Technical debt is our enemy, so a uniform concentration sounds ideal.

**Mehtap**: 
Trying to achieve some target concentration may be difficult in some cases. How about having a target concentration but also having a column to report known concentration of the plasmid sample?

    - Should we include the stop codon in the nucleotide sequence?

**Lucelenie**:
Yes.

**John**:
I think the nucleotide sequence for the insert should include start and stop codons.

**Mehtap**: 
I think it is better to have the stop codon explicitly in the nucleotide sequence.

    - How do we want to link this up to the "Chodera Lab Fridge and Freezer Inventory”?

**Lucelenie**:
We could have rows in the "Chodera Lab Fridge and Freezer Inventory” that specifies where the plasmid library is. For example, if the plasmid library takes up shelves 20-30, we should note this in the "Chodera Lab Fridge and Freezer Inventory” and provide a link to the Plasmid library (Google Drive link or Github repo).

**John**:
Do you envision having a separate tab for this library, or a separate document?
I believe you can add a URL to the whole "plasmid library" document in an entry in the freezer inventory, at simplest.

**Mehtap**:
Is it not simpler to have a separate inventory for plasmids? I think there should be separate spreadsheets since the information we want to capture for plasmids is different than cells, proteins etc. I think the best way will be listing our general plasmid library as “plasmid box 1, plasmid box 2, …”  in respective fridges and provide a link to plasmid library spreadsheet for more detail about contents.

    - How should we store and analyze our sequencing results? lab-protocols? .seq are text, but .ab1 also contain important information, but are less github-friendly. (https://seqcore.brcf.med.umich.edu/sites/default/files/images/clonesite.GIF)

**Lucelenie**:
We should store and analyze the .ab1 results. We should have a folder in the Google Drive to store sequencing results (.ab1) by date and at the same time store them in the repo assigned for the plasmid library (maybe lab-protocols).

**John**:
I'm not sure what these files represent. Is .seq the most likely sequence, but .ab1 is the nucleotide intensity at each position (necessary for getting confidence when base calling)? Why is .ab1 less github-friendly? Is it the size? If so, can we compress them?
    - It would be great to keep a revision-controlled repository of primary data, but I have a feeling there is a way to keep all of this data integrated in a manner that doesn't involve "starting from scratch" to build something ourselves. Plasmid libraries are very common data management tasks for wetlabs. Are there best practices? Online solutions?

**Mehtap**: 
I agree we should definitely save .ab1 type of sequencing information. If that is too much data for GitHub, can Google Drive be useful to organize extra files about plasmids?
I think lab-protocols should only have protocols related to plasmids (how to prepape, store them, PCR etc) but not contain the plasmid information. I think it would be easier to manage if we have a separate GitHub repo for plasmid library.

    - Any suggestions on how to make this maybe more machine readable? Ideally we would want to download a csv file of this spreadsheet and be able to do things programatically (compare e.g. experimental sequence to computational sequence, and calculate MW and extinction coefficient automatically from this information to input into denovix)?

**Lucelenie**:
Plasmids and primers can be different tabs in the same spreadsheet. Protein stocks can be listed in another spreadsheet. They are currently listed in "Chodera Lab Fridge and Freezer Inventory”; is there a reason not to keep listing them here?

**John**:
We should probably first spec out what the standard tasks are for using this plasmid library:
        - Check whether we have a plasmid with an insert of interest
        - Find all plasmids matching a certain criteria
        - Add one or more plasmids to the library (physically and to the database)
        - Cherry-pick one or more plasmids (physically and updating the database)
Am I missing anything?

**Mehtap**: 
I like the idea of using a well structured GoogleDrive spreadsheet. It is very easy to enter data that way and also easy to convert to csv and parse programmatically.

    - Should we have separate spreadsheets for Plasmid, Primer, and Protein Stocks rather than as tabs of the same spreadsheet? Is there any reason to have a separate spreadsheet for the glycerol stocks since these will just duplicate the plasmid library?

**Lucelenie**:
No, we can keep the glycerol stock information in the plasmid spreadsheet; have a column where we store the location and information of the glycerol stock.

**John**:
I'm not sure if there is an advantage to keeping them in the same spreadsheet since we treat these all differently.
What's the correspondence between glycerol stocks and purified plasmid stocks? Is it one-to-one? One-to-many?

**Mehtap**: 
I think a spreadsheet for glycerol stocks will be good too, to track what we have/ what is finished at any moment. Otherwise in the future we may need to open freezer boxes to check if we have stuff we assumed to be there. It could be a good place to organize information about glycerol stocks too, like preparation date, concentration etc.
Can we create UUID for each plasmid and connect both normal plasmid stocks and glycerol stocks?

    - Will be great to keep actively working on this till we have all of our plasmids in this (maybe excluding the 96 kinase plasmids??), making sure we have sequences, and concurrently maybe writing a mini package (a la peanut) that converts sequences to useful information from the PLASMID LIBRARY and PROTEIN STOCK csv files. Useful information being primers, MW, extinction coefficient. Should this be in lab protocols? Or create a new repo?

**Lucelenie**:
It could be in the lab-protocols repo.

**John**:
Do we really need to start from scratch here? We should always ask the question whether it's worthwhile to build something ourselves, since we don't want to put a good deal of effort into something that isn't as good as something off the shelf. On the other hand, if we need to create something very tailored to our particular situation, we should design it rather carefully (which you are trying to do!) and make sure it meets all of our carefully-enumerated use cases.

**Mehtap**: 
I think it is better to keep these tools together with the plasmid library repository, and maybe separate from lab-protocols.


**Mehtap**'s general comments about the spreadsheets:

 - Plasmid Library

     - I think we need a uniform way to write mutants:      
        - If no mutation: None      
        - If there is mutations: D464N, T415I     
        -  Deletion/insertion: ?
     - We must save Vector Map documents somewhere (Google Drive?) in case links to vector information stop working after a long time.
     - “Antibiotic resistance” instead of “Antibiotic”
     - I think we should have linker sequence information of expression tag too, but I don’t know what is the best way to write its sequence and position.

     - Adding remaining volume column

 - Primer Library

     - Adding “date” column

     - Adding remaining volume column
