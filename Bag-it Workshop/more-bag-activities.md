# MORE BAGIT ACTIVITIES AND SCRIPTS

Recommendations for activities and tasks to increase comfort with using the Python build of BagIt, including small scripts to accomplish tasks that were previously built into the CLI instance of the BagIt Java build.

## ADDING BAG METADATA WHILE CREATING BAGS
1. Use _NDSR_BagIt_sample_03_ to play around with bag metadata that can be added to the _bag-info.txt_ file. Read about the optional descriptive information you can include in that file in [Bag Metadata: bag-info.txt section of the BagIt spec](https://tools.ietf.org/html/draft-kunze-bagit-13#section-2.2.2). 

2. Add your phone number, a description, and a unique identifier when you create a new bag using the command line. 
- Options are structured like:

  `--optionName 'The information you want to add to the bag-info.txt file'`

So a command would look like:

  `bagit.py --contact-name 'Kathryn Gronsbell' --contact-email 'kgronsbell at gmail dot com' --external-description 'There may be something a little off about this bag...' /Users/kathryngronsbell/Desktop/NDSR_BagIt_sample_02`

3. Look at the _bag-info.txt_ in the new _NDSR_BagIt_sample_03_. 
 - Does the bag metadata you entered in the command show up?
 - How could this be useful for an organization's collections? Having a dedicated field for external identifier and descriptive information increases transparency and interoperability. 

## "LIBRARY USAGE" aka PROGRAMMING TASKS RELATED TO YOUR BAGS

On the Library of Congress' [bagit-python page](https://github.com/LibraryOfCongress/bagit-python#library-usage), they include examples of Python scripts to accomplish certain tasks. 

To do this exercise, you will need to be running atleast **[Python 3](https://www.python.org/downloads/)**. You can find out what version of Python you have by typing `python --version` into Terminal. If you think you might have Python 3 already installed, try typing `python3 --version`. 

1. Included in the sample bag is _bagmetadata_update.py_, which is a Python script cribbed from the bagit-python page linked above. It will change the metadata in the _bag-info.txt_ by using the "info" property on a bag.

3. Invoke the provided Python script. 

  `python3 [drag and drop bagmetadata_update.py] [drag and drop NDSR_BagIt_samples_03]`

4. Open the _bag-info.txt_ in _NDSR_BagIt_samples_03_. Does it match the example one below? 

![bag metadata update](https://github.com/kgrons/ndsr-2016-bagit/blob/master/updatemetadata_example.png "Bag Metadata Update")

5. Open _bagmetadata_update.py_. Change the values between the '  ' characters in lines 9 and 10. You can use any text editor (NOT MICROSOFT WORD). Save the file with the new values. Run the command from Step 3 again, and check the updated _bag-info.txt_. 

## MESS WITH YOUR BAGS
1. Create a bag with copied files from your own materials. **REMEMBER, YOU WILL BAG-IN-PLACE WITH THE PYTHON BAGIT BUILD. Use copies of your data!**

2. In the bag's data payload, modify text or image files. Delete a few payload files. Modify information in the generated BagIt text files (eg. _BagIt.txt_). 

3. Validate the bag. What kind of error messages do you get? What do they mean? 
