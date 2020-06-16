---
layout: post
title:  "Computing the Tangent to Point without Polyframe"
date:   2020-05-20 00:15:25 +0000
categories: houdini linearalgebra computergraphics visualeffects
---

Recently I had to come up with an alternative to using the 'Polyframe' node to computing tangents. I had a single polygon which was made up of around 20 edges. For some reason the 'Polyframe' node in this case would not compute tangents, and subsequently bitangents, for certain points on the polygon. I inspected the geo and everything seemed fine. Point count was ok, edges were all connected correctly, no duplicate points or overlapping geo.

After spending a little time on it, I found using the 'polyDoctor' node to repair face's made up of 5+ edges woud fix it. Essentially it would just triangulate the face which is something I didn't want to do.

As a consequence I decided to compute my own tangents.

Putting down an 'Attribute Wrangle' SOP and simply using the following:

```C

v@tangentu = normalize(@P - point(0, "P", neighbour(0, @ptnum, 1)));

```

The neighbour function returns the point number of the next point connected to a given point. Using that point and our current point, we can calculate a normal which is a tangent to the edge connecting the two points being used.
