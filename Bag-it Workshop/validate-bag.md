# VALIDATE AND CHECK BAG COMPLETENESS

Instructions for validating an existing bag with the BagIt Python build.

## WHAT DOES 'VALIDATION' AND 'COMPLETENESS' MEAN?

From the [BagIt spec](https://tools.ietf.org/html/draft-kunze-bagit-13#section-3),

**A _complete_ bag** MUST have the following attributes:
   1.  Every required element MUST be present.
   2.  Every file in every payload manifest MUST be present.
   3.  Every file in every tag manifest MUST be present.  Tag files not listed in a tag manifest MAY be present.
   4.  Every payload file MUST be listed in at least one manifest. Payload files MAY be listed in more than one payload manifest.
   5.  Every element present MUST comply with this specification.

**A _valid_ bag** MUST have the following attributes:
   1.  The bag MUST be complete
   2.  Every CHECKSUM in every payload manifest and tag manifest can be sucessfully verified against the contents of its corresponding FILENAME.

## VALIDATING A BAG
1. Validate the bag you created. In Terminal, enter this command:

`bagit.py --validate [drag and drop existing bag]`

![Validate bag command example](https://github.com/kgrons/ndsr-2016-bagit/blob/master/validatebag_example.png "Validate bag command example")

2. Is your bag valid? I hope so! The bag should contain files consistent with the original files and that are appropriately formed. Congratulations on your first bag validation! :pouch::white_check_mark:

3. Try to validate a bag provided to you. Run the validation command again but this time on _NDSR_BagIt_sample_02_. 

4. What message was printed in Terminal? Was it _NDSR_BagIt_sample_02 is invalid: Oxum error.  Found 3 files and 613223 bytes on disk; expected 3 files and 613217 bytes._? 
   - That's because this bag's payload had been modified. Take a peek in the _t_ file. The text in this file has been changed, which BagIt recognized as a byte different of 6 bytes. No difference too small for BagIt to catch! 

5. I have to be honest with you - I threw you another curveball! Open the _tagmanifest-md5.txt_ file in _NDSR_BagIt_sample_02_. There's something in there that shouldn't be. But why didn't the validation error tell you that?
   - According the [BagIt spec](https://tools.ietf.org/html/draft-kunze-bagit-13#section-3), "tag files that do not appear in a tag manifest can be modified, added to, or removed from a bag without impacting the completeness or validity of the bag". 


**Still can't get enough BagIt? Check out [more activities around creating, modifying, and validating bags](more-bag-activities.md).**
