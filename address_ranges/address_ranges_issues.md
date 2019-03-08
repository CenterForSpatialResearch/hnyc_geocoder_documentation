# HNYC

## Address Range + Street Attribute Entry
Preparing historical street geometries to geocode census microdata. Dan Edit.

## Project Documentation

As a general rule, if you have a question about something you’re seeing on the map, a street geometry, address number, or if you think something is inconsistent/missing, *please document it*.


### Documentation Guidelines

Please keep your own notes. Also log issues and questions you’re having (either with a particular segment/block, with the ArcOnline app, etc) on the [Address Range Trello board](https://trello.com/b/bkFvGgcE/address-ranges) as an issue card. Include a screenshot and a brief description of the issue (e.g. “There are odd and even addresses on both sides of the street on Myrtle Avenue near Fort Greene Park”). Use the Trello board labels (e.g. FYI, Can Wait, Critical) and tag other team members on the card.

If the issue you're encountering is **not** one of the issues covered already in document, do not try to infer or guess the address range on your own. Flag it in the Issues field using the issue codes **x**, take a screenshot and skip it. **DO NOT SPEND MORE THAN ~20 SECONDS TRYING TO SOLVE AN ISSUE ON YOUR OWN**. We will return to problem segments as a group -- it’s important we that uniformly and systematically address those.


## Common Issues

Some common issues for address range entry are:
+ Special street and address number patterns (odd intersections, roundabouts, merged or stacked avenues, etc)
+ Address numbers are not consistent or evenly distributed on either side of street
+ Address numbers are not given for the beginning / end of the block or street segment
+ Address numbers are only given on one side of the street
+ Address numbers are not listed at all
+ Large building or institutions break the pattern of address numbers
+ Random omission of numbers on the map, or possible mislabelings/misspellings
+ Small or irregular blocks with one or just a few buildings, one address, or no buildings at all
+ Large adjacent buildings setting the perpendicular addresses too far back for proper geocoding (weird street layouts)
+ Gaps in address numbers between blocks that should be numbered consecutively


## Guiding Principles for Digitizing Address Ranges
+ For each block / street segment be as inclusive with `low` and `high` number inputs as possible (capturing as many possible address numbers in your entry). The property atlases may omit numbers inconsistently and go against what we may know/assume about the address system. Use your critical judgement and these guidelines to fill in the blanks or resolve any inconsistencies.
+ Prioritize your critical reading of the property atlases. Use relevant street guides and other basemaps as secondary address finding aids.
+ Source analysis suggests contradicting the map in the attribute entry process in only a few instances: when the maps omit property lots and address numbers, mislabel or misspell, and/or when you need to enter address attributes in such a way as to assure a more accurate geocoding match.


## Types of Address Numbering Systems in New York City

Sections of New York City will follow different rules for address numbering. In Manhattan and Brooklyn, there are two prevailing systems:

+ **Consecutive Address Numbers**

   Avenues in Manhattan and much of Brooklyn will be numbered (mostly) consecutively from block to block along the entire length of the street. Address numbers ascend sequentially, with even and odd numbers on opposite sides of the street. There are occasionally large or irregular gaps or discrepancies in the ranges.

   ![Diagram of the consecutive system](https://github.com/mapping-hnyc/documentation/blob/master/hnyc_addressRanges/images/consecSystem_1.png)
   ![Example of the consecutive system in place along 6th Ave in Manhattan](https://github.com/mapping-hnyc/documentation/blob/master/hnyc_addressRanges/images/consecSystem_2.png)

+ **Decimal System Address Numbers**

   Crosstown streets in Manhattan are numbered from the most recent intersection. Split into East and West by Fifth Avenue, address numbers progress sequentially from each intersection but skip to the next set of 100 numbers on every block (1, 100, 200, 300...). Even and odd numbers are given on opposite sides of the street.

   ![Diagram of the decimal system](https://github.com/mapping-hnyc/documentation/blob/master/hnyc_addressRanges/images/decSystem_1.png)
   ![Example of the decimal system in place along W 20th St in Manhattan](https://github.com/mapping-hnyc/documentation/blob/master/hnyc_addressRanges/images/decSystem_2.png)

## Solutions to Common Issues by Street Type
The following guidelines were developed for digitizing **CONSECUTIVE** and **DECIMAL SYSTEM** address numbers.

### Solutions to Common Issues that Apply to Both Systems

![Address numbers are not labeled at the very end of this block](https://github.com/mapping-hnyc/documentation/blob/master/hnyc_addressRanges/images/allIssue_1.png)

+ Are all lots/buildings on a block/segment labeled? if not, do their associated labels extend all of the way from the start of the block/segment to the end? If there are missing address labels from the very beginning or end of the block, you will need to pad your entry with an appropriate number of address numbers.
    1. Consult the relevant street guide. It may provide more information that would help you fill in the blanks. Street guides make note of the address numbers found at each intersection along the entire length of a street.
    2. If the addresses are better labeled on the opposite side of the street and are comparably distributed (roughly the same number of lots), you may reference those numbers to help fill in the blanks (adjusting for odd/even)
    3. If the first + last numbers on a block/segment are set back by an adjacent building, lot, yard, or other property, you may pad with address numbers based on a standard lot dimension. Sketching and/or roughly estimating are fine.

When padding, make sure that you're not adding numbers that are associated with a preceding / proceeding block. Duplicate numbers will break the geocoder.


### Consecutive Address Numbers  

![](https://github.com/mapping-hnyc/documentation/blob/master/hnyc_addressRanges/images/consecIssue_2.png)

+ There are large gaps in address numbers between blocks / segments when they should be consecutive.
  1. Under the consecutive address number system, every possible number that could exist along the street *should* be captured and associated with a segment of the street. This sometimes conflicts with what is depicted on the property maps and what was assigned on the ground. **Is the gap made up of 6 or fewer address numbers?** If yes, divide up the missing numbers and add them to the adjacent segments (the end of the preceding block / the beginning of the next). If fewer than 6 add just one number to the end of the preceding block.
  2. **Is the gap made up of more than 6 address numbers?** If yes, do not add any numbers to the end of the preceding block / the beginning of the next block. This guideline does not impact any address number / lot padding you may have accounted for on the interior of the block already.
  3. The street guide may help clear up instances of very large gaps between blocks. Reference it selectively.


![](https://github.com/mapping-hnyc/documentation/blob/master/hnyc_addressRanges/images/consecIssue_3.png)

+ Address numbers are only given on one side of the street
  1. Are there residential buildings on the side of the street without address numbers? If no, you can leave the relevant `low` and `high` fields blank. Sometimes large institutional buildings will occupy an entire block -- the address for that building may be associated with another adjacent street.
  2. Have the address numbers on either side of the street generally been ascending at the same rate / at an even distribution? If yes, you may use the address range opposite as a rough guide for inputting addresses into the blank fields, adjusting even/odd accordingly.
  3. Is there a park or some other type of non-residential land type or use (e.g. warehousing, waterfront) on the block? Do the addresses given on one side of the block contain both even and odd address numbers? If yes, please see the next guideline -->


![](https://github.com/mapping-hnyc/documentation/blob/master/hnyc_addressRanges/images/consecIssue_1.png)

+ Addresses are only given on one side of the street and the address numbers depicted are both odd and even numbers
  1. Flag this in the `Issues` field with an **x** and skip it. We will need to create a point-based geocoder for these cases (like Central Park West, 5th Ave at Central Park, Riverside Ave, etc). You should take a screenshot and post this to the Trello board.


![](https://github.com/mapping-hnyc/documentation/blob/master/hnyc_addressRanges/images/consecIssue_3%20Copy.png)
![](https://github.com/mapping-hnyc/documentation/blob/master/hnyc_addressRanges/images/consecIssue_3%20Copy%203.png)

+ There are duplicate addresses given on different blocks / segments of the same street.
  1. If the `high` address of one block and the `low` address of the block above on the same side of the street have the same address number, consult the street guide.
  2. If the street guide is not helpful in resolving this, look at the layout of address numbers leading up to the first duplicate number. Can you choose which number to keep in a way that preserves the consecutive progression of address numbers?
  3. Is it still not possible to resolve? Or are there other issues associated with the duplicate like an alphanumeric address or letter suffix? Flag this in the `Issues` field with an **x** and skip it. We will need to create a point-based geocoder for these cases. You should take a screenshot and post this to the Trello board.


![](https://github.com/mapping-hnyc/documentation/blob/master/hnyc_addressRanges/images/consecIssue_4.png)

+ Odd intersections, roundabouts, merged or stacked avenues
  1. Irregular intersections can pose challenges to determining relevant address ranges (Broadway at Times Square, Broadway and West End, , etc)
  2. Does a street or avenue terminate at the intersection? Where do the avenues or streets pick up again with address ranges after the intersection? Consult the street guide in this case and make sure to capture all addresses depicted on the map on a relevant, labeled street segment.
  3. Does the underlying geometry need to be edited to more accurately reflect the historical layout of streets at this intersection? If yes, flag this in the `Issues` field with an **g** and skip it.


![](https://github.com/mapping-hnyc/documentation/blob/master/hnyc_addressRanges/images/consecIssue_5.png)

+ Streets or avenues with two or more centerlines
  1. Some avenues are partitioned and have two centerlines, one for each side of the street. Two lines segments are needed when there is a median (e.g. Park Ave and Broadway)
  2. Input left ranges for the left centerline and right ranges for the right segment, leaving the others blank.


### Decimal System Address Numbers
+ Beginning address ranges
  1. `Low` address numbers follow the rules of the decimal system.
  2. Even if the maps don’t depict 100, 200, 300... or 101, 201, 301... address numbers as the first, or lowest, addresses, on the block, these should always be the address numbers you input for the `low` values on crosstown street segments on the decimal system
  3. At the beginning of the crosstown streets split by 5th avenue, you should enter either a 1 or 2 for the `low` field depending on the east/west, odd/even direction of the street you’re working on. Do not enter a **0**. It is not a valid address number.


### Data Entry Fields Explained
+ `ST Direction [YYYY]`: Leave EMPTY, we will edit this in a batch process later
+ `ST Name [YYYY]`: If there is a different street name listed on the map (OR in the street directory) than in the original FULL_STREET field, input new name in all caps

   **NOTE**: alternate street names are important to capture. The addresses given in the census or city directory may be based on alternate, outdated or colloquial street names.

+ `Left Low [YYYY]`
+ `Left High [YYYY]`
+ `Right Low [YYYY]`
+ `Right High [YYYY]`

   Left and Right are determined by the direction of ascension of address numbers along the street. This direction also indicates the placement of Low and High address numbers on the block / segment.

+ `Issue [YYYY]`: If you have an issue reading, interpreting, or transcribing the address ranges or working with the underlying street geometries.

   **ISSUE LEGEND**:
   * `X` - unspecified issue
   * `D` - delete
   * `M` - merge
   * `S` - split
   * `G` - geometry edit

+ `ST Name Alternate [YEAR]`: Is there yet another street name given on the basemaps that differs from the label? Often these will be in parentheses.
+ `ST Unopened [YYYY]`: "Paper Streets". If the street was open on the historical basemap (see legend), do not enter anything in this field (default). If the street was closed, planned (drawn on the map) but not yet opened, enter a **1** in this field.
