


Geohashes:
- originaly designed as url-friendly way of expressing location.
- recursively divide the world into smaller and smaller nested grids via Z-order (morton) curve.
  - Level 1: 32 cells (4 rows and 8 columns).
  - each cell at level 1 is subdivided by 32 children cells.
  - series of bits that repeatedly bisects a search space of longitude and latitudes.
  - first bit bisects the longitude, second bit bisects the latitude (resulting in some square some 2:1 rectangles)
  - result is increasing precision with more bits (similar to floats!) which means nearby places will share similar prefixes
- base-32
- each geohash represents an area (can't decode a single geohash to a single point)
- close geohashes will begin with the same bits.  More similar bits = closer.


- http://mapzen.github.io/leaflet-spatial-prefix-tree/
- https://www.elastic.co/guide/en/elasticsearch/guide/current/geohashes.html
- https://en.wikipedia.org/wiki/Geohash#Decode_from_base_32
- https://www.factual.com/blog/how-geohashes-work/


S2:
- designed as a fast spatial index on a sphere
- "this makes it possible to build a worldwide geographic database with no seams or singularities, using a single coordinate system, and with low distortion everywhere"
- 64-int integers
- built with hilbert curve
- hierarchical (subdivision)
- Starts by internally projecting the points/regions of the sphere onto a cube, each face of cube has a quad-tree where sphere point is projected.  The quad tree is transformed to adjust for distortion and enumerated onto a Hilbert Curve.
- Hilbert curve transforms multi-dimensional data into one dimension which allows range queries
- good with b trees


http://s2geometry.io/
http://blog.christianperone.com/2015/08/googles-s2-geometry-on-the-sphere-cells-and-hilbert-curve/


H3:
