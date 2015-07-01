# ADE - Revisiting TLP

Version 0.2.0

## Overview

TLP has been a key part of the Internet security community for years. It provided simple handles that could be applied to shared information in order to communicate to the recipient what audiences they might share the information with. The first version of this protocol supports 3 dimensions. Attribution who is credited with publishing the data, Distribution who you may share the data with, and Execution what you may do with the data.

## The Problem with TLP

On the grand scale TLP has been hugely successful. After some time in service the imprecision of the graduations are beginning to show. In particular the AMBER designation has recently changed leaving many to wonder if everything they have published under the original TLP:AMBER is now associated with the old rules or the new ones? There are also a number of organizations that have adopted slightly varying rules around the levels of TLP.  

This proposal is not built on top of TLP to avoid confusion. Once a 1.0.0 version is released, category designators may be added or depreciated, but never reused without a major revision change. There will be one source for the official version of the protocol that all other copies should reference. 

## Terminology
 * Dimension - ADE is initially comprised of 3 dimensions, (Attribution,Distribution,Execution)
 * TLP - Traffic Light Protocol, (https://www.us-cert.gov/tlp)

## Operation

An ADE tag in normal text-based communication is made up of a simple case sensitive ASCII URL. The prefix will always be "ADE:https://$domain/". In place of the traditional "TLP:", this indicates which system the author wishes to proclaim. The next element is a version e.g. "1.2.3". ABE will follow the Semantic Versioning(http://semver.org/) model. The remainder of the URL presents one or more characters for each dimension ,Attribution, Distribution, and Execution, separated by a ".". These characters indicate what permissions, restrictions and possibly modifiers the author wishes to prescribe. This URL will return a detailed breakdown of the tag and the requirements it conveys.

The first character will indicate the author's choice of attribution requirements. For example F = Attribution forbidden, R = Attribution Required, further details of each option will be discussed in greater detail in the per categories files found in this repository. The second character designates distribution limits placed on the data. Examples here are P = Public distribution (think TLP WHITE), 0 = Recipient only, no redistribution (think TLP RED, "EYES ONLY"). Finally is the execution category, this indicates what the recipient is permitted to do with the covered information. For example "I" indicates that the data is informational only, it is not to be used for blocking, interrogated, or reported. "A" indicates all actions are permitted.

The code behind the URL will also support format specification via either an extension (e.g. .json, .yaml, .xml) or setting the request Content-type header appropriately. Ideally this feature will allow automated systems the ability to decide and act based on the restrictions stated.

##Requirements for use. 
* Encryption - If you received ADE tagged information under cover of encryption, it is required that any forward sharing you initiate is done under the same or stronger protections. This can be altered by the author in the text itself in cases of embargoes and the like.
* Agreement - By accepting information under ADE tag you agree to honor the requirements and responsibilities of that tag and only forward to individuals and organizations you trust follow suit.
* Content will be held to the standard of the ADE tag that precedes it. This way it is possible to have one document that contains content protected under different tags.
* Any URI preceded by "ADE:" must always point or redirect to a ADE format service.

##Future work. 
* $domain should be decided before ADE 1.0.0. The domain should be a stable, neutral property that can support ADE for its long-term use. Possibly a trusted community group.
* The URL for any TAG needs to generate an informational web-page explaining the requirement and responsibilities associated with the specified ADE tag.
* Find a way to express the rules associated with each identifier in a machine-readable way.
* Referential tags. It should be possible for a tag to refer to a document specific URI that always redirects to the current ADE URI. This will support embargo functionality at a later date.

##Rules
* Dimension identifiers should avoid homoglyph characters like lowercase l, capital I, lowercase 0, zero and capital O.
* New characters may be added to a category or depreciated, but never replaced within the same major revision.
* Dimension designators should be somehow mnemonic where possible. (e.g. F = Forbidden)
* New dimensions may be added only in major revisions.
* The following characters are reserved and cannot be used as dimension designators: ./\_

##Examples
* ADE:https://$domain/0.0.1/F.0.I - Attribution forbidden, No distribution, No Action - Most restrictive
* ADE:https://$domain/0.0.1/F.P.A - Attribution forbidden, Public distribution, Any Action - Least restrictive
* ADE:https://$domain/0.0.1/F.P.A.json - Generate JSON output.
