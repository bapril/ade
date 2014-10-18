# ADE - Revisiting TLP

Version 0.1.3

## Overview

TLP has been a key part of the Internet security comminty for years. It provided simple handles that could be applied to shared information in order to communicate to the recipient what audiences they might share the information with. This protocol supports 3 dimensions. Attribution who is credited with publishing the data, Distribution who you may share the data with, and Execution what you may do with the data.

## The Problem with TLP

On the grand scale TLP has been hugly successful. After some time in service the imprecision of the graudations are beginning to show. In particualr the AMBER designation has recently changed leaving many to wonder if everything they have publised under the origional TLP:AMBER is now associated with the old rules or the new ones? There are also a number of orginizations that have adopted slightly varying rules around the levels of TLP.  

This proposal is not built on top of TLP to avoid confusion. Once a 1.0 version is released, category designators may be added or depreciated, but never reused. There will be one source for the official version of the protocol that all other copies should reference. 

## Operation

An ADE tag in normal text-based communication is made up of a simple case sensitive ASCII URL. The prefix will always be "https://$domain/ade/". In place of the traditional "TLP:", this indicates which system the author wishes to proclaim. The remainder of the URL indicates what permissions and restrictions the author wishes to perscribe. These wishes are declared in three categories. Attribution, Distribution, and Execution. Each category comes with a one character designators. This URL will return a detailed breakdown of the tag and the requirements it conveys.

The first character will indicate the author's choice of attribution requirements. For example F = Attribution forbidden, R = Attribution Required, further details of each option will be discussed in greater detail in the per categories files found in this repository. The second character designates distribution limits placed on the data. Examples here are P = Public distribution (think TLP WHITE), 0 = Recipent only, no redistribution (think TLP RED, "YOUR EYES ONLY"). Finanlly is the execution category, this indicates what the recipent is permitted to do with the covered information. For example "I" indicates that the data is informational only, it is not to be used for blocking, interogated, or reported. "A" indicates all actions are permitted.

##Requirements for use. 
* Encryption - If you recieved ADE tagged information under cover of encryption, it is required that any forward sharing you initiate is done under the same or stronger protections. This can be altered by the author in the text itself in cases of embargos and the like.
* Agreement - By accepting information under ADE tag you agreee to honor the requirements and responsibilities of that tag and only forward to individuals and orginizations you trust follow suit. 

##Future work. 
* $domain should be decided before ADE 1.0. The domain should be a stable, neutral property that can support ADE for its long-term use. Possibly a trusted community group. 
* The URL for any TAG needs to generate an informational web-page explaining the requirement and responsibiliites associated with the specified ADE tag.

##Rules
* Categories should avoid Homoglyph characters, lowercase l and upper-case O. 
* New characters may be added to a category or depreciated, but not replaced.
* Category designators should be somehow mnemonic where possible. (e.g. F = Forbidden)

##Examples
* https://$domain/ade/F0I - Attribution forbidden, No distribution, No Action - Most restrictive
* https://$domain/ade/FPA - Attribution forbidden, Public distribution, Any Action - Least restrictive


