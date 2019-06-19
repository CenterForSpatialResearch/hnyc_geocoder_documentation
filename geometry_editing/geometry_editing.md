# HYNC

## Geometry Editing Guide

### Documentation Guidelines
Please keep your own notes. Also log issues and questions you’re having (either
with a particular segment or with the ArcGIS software) on the [Street Geometry
Trello Board](https://trello.com/b/sqVDLXwu/street-geometries) as an issue card.
Include a screenshot and a brief description of the issue (e.g. “Basemap missing
in Canarsie”). Use the Trello board labels (e.g. FYI, Can Wait, Critical) and
tag other team members on the card.

### Guiding Principles for Street Geometry
* Do not blindly trust georeferenced maps. Always consult at least 2 sources
(e.g. contemporary map, different atlas editions, city directories) before
making edits.
* Make sure that all segments snap onto each other. This will be critical for
geocoding and calculating travel time.
* Mark a `1` in the `geometry check [census year]` field for every segment
without issues
* Don’t be trigger happy with the delete button. Deleted segments are gone.
Forever.
* When in doubt, flag an issue on the Geometry Trello Board. It is important
that we resolve difficult issues together to ensure common practices.

## Common Issues

Some common issues for geometry editing are:

* Two or more segments need to be merged
* A segment needs to be split into two or more parts
* Missing segments need to be drawn into existing streets
* Intersections are imperfect and break up continuing streets
* Two atlas editions from years surrounding the census year show different
conditions
* Unopened or planned streets need to be drawn in
* Due to urban developments streets on the waterfront are absent
* Old country roads intersect with the (existing or proposed) city grid
* Old buildings appear in the middle of existing or planned roads
* Ambiguous alleys or unnamed streets show up
* Segments that already have attributes filled in need to be planarized
* Basemaps are poorly georeferenced
* Georeferenced maps overlap at edges, covering important information

## Strategies for Common Issues

### Screening, Merging, and Splitting

All street segments need to be checked for geometry errors. Using the `select`
tool, draw a line over a number of segments to see if their geometry corresponds
with the situation for the given year (1910, 1880, 1850). If the city block
consists of two or more segments, merge them. If a street segment extends beyond
its intersections with other streets, split the segment at the junction(s). When
a segment is checked, mark a \`1\` in the attribute field `Geometry Check
[census year]`.

![Image 1](https://github.com/CenterForSpatialResearch/hnyc_documentation/blob/master/geometry_editing/images/selection_merge.png)

### Missing Segments

When segments are missing along open streets, make sure to add these back in.
This can happen where portions of streets no longer exist due to large scale
developments, e.g. parks, highways, housing projects. Draw in a new street
segment in the direction of ascending address numbers. Be sure to snap the new
street segment to the junctions on either side.

Alternatively, if the missing segment is at the end of the road, you can extend
the existing street as a benchmark in order to ensure the right placement of the
new segment. Then, draw in the new segment based on the benchmark street.
Afterwards, move the existing street back to its original place.

![Image 2](https://github.com/CenterForSpatialResearch/hnyc_documentation/blob/master/geometry_editing/images/missing_segment.png)

### Imperfect Intersections

Along intersections there are often small segments that connect street segments
holding address ranges, but do not represent any addresses or buildings
themselves. They can be a result of an imperfect junction or the intersection of
boulevard streets with multiple segments, and are important for maintaining the
spatial continuation of each street. Even if they do not contain any ranges
themselves, make sure to add them where streets clearly continue across
intersections.

![Image 3](https://github.com/CenterForSpatialResearch/hnyc_documentation/blob/master/geometry_editing/images/junctions.png)

### Discrepancies Between Atlas Editions

In some cases, maps of different years contain divergent or contradictory
information. If there is a discrepancy between various atlas plates, try to
infer whether roads were in existence and in use at the census year from other
sources at your disposal, e.g. city directories, current situation, and other
maps.

In one case in Flatbush, Brooklyn, a 1906 map included a series of planned
roads, while 1916 showed an extension of the adjacent cemetery instead. Today's
situation mirrors the image of 1916. The cemetery exists and it looks like the
planned roads from 1906 were never built. However, we decided to add in these
roads anyway, since we cannot know for sure their status in 1910 or if anyone
lived in this area at any point before the cemetery extension. As a rule, it is
always best to preserve as much information as possible. In most cases, streets
that exist in one map but not another should be added nonetheless. It can also
be helpful to double check with the directories of surrounding dates to see if
any address numbers were ever assigned to the area.

![Image 4](https://github.com/CenterForSpatialResearch/hnyc_documentation/blob/master/geometry_editing/images/discrepancy.png)

### Drawing In Unopened Streets

In the example above, new street segments had to be drawn in. When you need to
create a larger collection of streets rather than just one segment, try to use
as many anchor points from the existing street network as possible.

If roads are broken up by rivers, canals, parks, or in this case a cemetery, you
can observe the following strategy:

![Image 5](https://github.com/CenterForSpatialResearch/hnyc_documentation/blob/master/geometry_editing/images/1906_1916_holy_cross.png)

### Waterfront

Often, waterfront streets and docks are missing segments at places where streets
are visible in atlas maps. To best reflect these industrial areas and their
buildings, add segments for streets leading to the waterfront whenever there are
clear indications of opened streets and/or potential addresses. Reference all
basemaps in deciding where to add segments and in determining their start and
end points.

![Image 6](https://github.com/CenterForSpatialResearch/hnyc_documentation/blob/master/geometry_editing/images/waterfront.png)

### Old Roads

There are a number of old country roads that intersect with the street grid,
especially in outer neighborhoods of Brooklyn. When encountering such roads, it
is important to establish whether they are still in use. Ask yourself a set of
questions in each ambiguous case. Are there buildings or plots that align with
the old street? Does the old street intersect with buildings that follow the new
grid system? Are the intersections and junctions with other streets colored,
implying continued use? If it seems likely that the road was still operational,
**planarize** with other existing roads.

![Image 7](https://github.com/CenterForSpatialResearch/hnyc_documentation/blob/master/geometry_editing/images/old_road.png)

In the example below, an old road intersects with the new grid at various
points. Since there are buildings and plots aligned with the old road, we can
conclude that it’s still in use. The road should be drawn in and then planarized
with existing intersecting streets.

![Image 8](https://github.com/CenterForSpatialResearch/hnyc_documentation/blob/master/geometry_editing/images/old_road_planarize.png)

### Buildings and Roads Overlapping

There are a lot of cases where old buildings along old roads intersect with
planned but unopened grid streets. These will most likely have no official
addresses and will shortly be demolished. In these cases it is best to mark the
streets unopened with no addresses if none are found on either the map or the
directory. Make sure to reference each map year

![Image 9](https://github.com/CenterForSpatialResearch/hnyc_documentation/blob/master/geometry_editing/images/building_on_road.png)

### Alleys

There are a number of alleys across the city, particularly in industrial
waterfront areas. They are usually named but do not contain any addresses. In
these cases, add missing segments for alleyways, write in their names if they
have them, mark additional or secondary names written in parentheses, and check
for address ranges on the maps and in the directories (they often don't have
any). Also check to see if they exist today, and if additional information can
be recorded based on their current condition.

### Planarizing Streets With Attributes

When you planarize streets that already have attribute fields filled in, the
attributes will duplicate into the new street segments. Look at the attributes
of each new segment and change them **immediately** after planarizing if
they are no longer correct.

### Poor Georeferencing

Sometimes it may seem like the street networks of entire neighborhoods are
misaligned and in need of significant geometry edits. However, it may just be
that the corresponding atlas plate is poorly georeferenced. In a situation like
this, **first compare the different atlas plates**. Also take into
consideration the contemporary street network in order to determine whether it
is the geometry or the atlas that is misaligned.

![Image 10](https://github.com/CenterForSpatialResearch/hnyc_documentation/blob/master/geometry_editing/images/georeferencing.png)

### Map Seams

At streets located on the border of two atlas maps, or wherever various maps
touch, there will often be some overlap, where one map covers the edge of the
other. Here, information from the covered map can be lost. It is important to
record this information by either manually viewing the map at its source site,
or cropping the covering map if there is no available external information. In
many instances, it suffices to leave the map covered and pull up another copy
temporarily to record the necessary address ranges. Long term edits should be
made to the map layer to be able to see all information permanently. Record the
issue on Trello.
