# CREATE A BAG

Instructions for creating a BagIt bag with the Python build.

## BEFORE YOU BEGIN

- You [installed Python BagIt](install-directions.md).
- You downloaded the [zip package of samples and resources](https://github.com/kgrons/ndsr-2016-bagit/blob/master/NDSR-NYC_BagIt.zip). Save **A COPY** of the _NDSR_BagIt_samples_01_ folder on your Desktop. (Leave the downloaded zipped version in your Downloads folder.)

## CREATING BAGS WITH BAGIT ON THE COMMAND LINE

1. Open Terminal (Applications > Utilities > Terminal)
2. In Terminal, type the command below. You will see usage and options information for BagIt. Read through them.

       `bagit.py --help`


3. What does 'creating a bag' actually mean? You will create a structured package of target data based on an existing structure. On the desktop, open _NDSR_BagIt_samples_01_ and review the files inside to understand your source data.
    - What types of files are in the folder?
    - What information is in the text files?
    - How many files are in the folder?
    - Want to see how your data looks on the command line instead of opening the files in Finder? Enter these commands into Terminal:
        - `cd [drag and drop the _NDSR_BagIt_samples_01_ folder into Terminal]` _Changes the directory to our samples_
        - `ls` _Lists the files within our sample directory_
        - `cat [drag and drop one of the text files]` _Prints/displays the contents of a text file into Terminal_

4. It's time to create the bag, or package your data into a bag _payload_. In Terminal, enter the command below. **IMPORTANT: This will REPLACE the folder on your Desktop with a BagIt-structured bag.** This action is referred to as "bag in place", or replacing a data source with a bag that adheres to the BagIt specifciation.  

       `bagit.py --contact-name '[FirstName LastName]' [directory of sample files]`

![Create bag command example](https://github.com/kgrons/ndsr-2016-bagit/blob/master/createbag_example.png "Create bag command example")

5. Congratulations! You made a bag! :tada:

6. Look at the processing log in Terminal below your command from Step 4. What did the _BagIt.py_ script do? 
       - It created a payload directory, moved existing data, and wrote the text files required in the BagIt spec.

## WHAT'S IN YOUR :pouch:?

1. Time to open up the bag and see what's inside. You can use the commands you tried in Step 3, or simply double click the text files from the Finder window. What you should see:
![bag_01 structure](https://github.com/kgrons/ndsr-2016-bagit/blob/master/bag_01_structure.png "Bag_01 Structure")

2. Open each file and the data directory. 
       - **bag-info.txt** : Report summary of the bag. Includes size of the bag,  bag create date, and the number of files in the bag.
       - **bagit.txt** : Bag Declaration. It contains information about what version of BagIt was used and the encoding mechanism. What version of BagIt are you running on your machine?
       - **data subdirectory** : Data directory or ‘payload’ of the existing files. What is contained in your newly created bag? It should look familiar... 
       - **manifest-md5.txt** : Essential for validating the bag is the md5 manifest, which is an inventory of files in the bag and their file paths and associated md5 checksums.
       - **tagmanifest-md5.txt** : Inventory of information files (not the payload) and associated checksums. This is essential in ensuring the metadata has not been corrupted during bagging. 


**Ready for more? Head over to the directions for [validating a bag](https://github.com/dinahhandel/ndsr-2016-bagit/blob/master/validate-bag.md).**
