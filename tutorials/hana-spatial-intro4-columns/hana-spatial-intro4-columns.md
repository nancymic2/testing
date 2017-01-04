---
title: Intro to SAP HANA Spatial: Spatial columns
description: Using columns that support spatial data
tags: [  tutorial>beginner, topic>big-data, topic>sql, products>sap-hana, products>sap-hana\,-express-edition ]
---
## Prerequisites  
 - **Proficiency:** Beginner
 - **Tutorials:** [Intro to SAP HANA Spatial: Polygons](http://www.sap.com/developer/tutorials/hana-spatial-intro3-polygon.html)

## Next Steps
 - Intro to SAP HANA Spatial: 3rd dimension (coming soon), or
 - Select a tutorial from the [Tutorial Navigator](http://www.sap.com/developer/tutorial-navigator.html) or the [Tutorial Catalog](http://www.sap.com/developer/tutorials.html)

## Details
### You will learn  
In previous tutorials you learned how to create spatial objects and run selected methods to perform some calculations using them. Now it's time to learn how to store, retrieve and process spatial data in SAP HANA tables. You will learn as well about the Spatial type hierarchy.

### Time to Complete
**10 Min**.

---

1. For the purpose of this tutorial create a schema `TESTSGEO` or use any other schema in your instance, where you have a privilege for creating tables.

    ```sql
    CREATE SCHEMA TESTSGEO;
    SET SCHEMA TESTSGEO;
    ```

2. The following spatial types can be used in column tables in SAP HANA:
    - `ST_POINT`,
    - `ST_GEOMETRY`.

    >Spatial columns are not supported in SAP HANA row tables.

    Column type `ST_GEOMETRY` supports multidimensional spatial data for the following spatial data types: `ST_CircularString`, `ST_GeometryCollection`, `ST_LineString`, `ST_MultiLineString`, `ST_MultiPoint`, `ST_MultiPolygon`, `ST_Point`, and `ST_Polygon`.

    `ST_GEOMETRY` is a core component of the SQL Multimedia (`SQL/MM`) standard for storing and accessing geospatial data. `SQL-MM` follows object-oriented approach. The term **geometry** means the overarching type for objects such as points, strings, and polygons. The geometry type is the supertype for all supported spatial data types.

    The following diagram is taken from official SAP HANA Spatial Reference Guide and illustrates the hierarchy of the `ST_Geometry` data types:

    ![Spatial hierarchy](spatial0401.png)

    Object-oriented properties of spatial data types:
    - A subtype (or derived type) is more specific than its supertype (or base type).
    - A subtype inherits all methods from all supertypes. For example, `ST_Polygon` values can call methods defined for the `ST_Geometry`.
    - A value of a subtype can be automatically converted to any of its supertypes. For example, an `ST_Point` value can be used where a `ST_Geometry` parameter is required.
    - A column or variable of type `ST_Geometry` can store spatial values of any type.

3. Create and load data into `SpatialShapes` table. This example is taken from SAP HANA Spatial Reference, so that you can run exercises from the official help as well.

    ```sql
    CREATE COLUMN TABLE SpatialShapes
    (
      ShapeID integer,
       shape ST_GEOMETRY
    );

    -- a set of points
    INSERT INTO SpatialShapes VALUES(1,  NEW ST_POINT('POINT(2.5 3.0)'));
    INSERT INTO SpatialShapes VALUES(2,  NEW ST_POINT('POINT(3.0 4.5)'));
    INSERT INTO SpatialShapes VALUES(3,  NEW ST_POINT('POINT(3.0 6.0)'));
    INSERT INTO SpatialShapes VALUES(4,  NEW ST_POINT('POINT(4.0 6.0)'));
    INSERT INTO SpatialShapes VALUES(5,  NEW ST_POINT());

    -- a set of linestrings
    INSERT INTO SpatialShapes VALUES(6,  NEW ST_LINESTRING('LINESTRING(3.0 3.0, 5.0 4.0, 6.0 3.0)'));
    INSERT INTO SpatialShapes VALUES(7,  NEW ST_LINESTRING('LINESTRING(4.0 4.0, 6.0 5.0, 7.0 4.0)'));
    INSERT INTO SpatialShapes VALUES(8,  NEW ST_LINESTRING('LINESTRING(7.0 5.0, 9.0 7.0)'));
    INSERT INTO SpatialShapes VALUES(9,  NEW ST_LINESTRING('LINESTRING(7.0 3.0, 8.0 5.0)'));
    INSERT INTO SpatialShapes VALUES(10,  NEW ST_LINESTRING());

    -- a set of polygons
    INSERT INTO SpatialShapes VALUES(11, NEW ST_POLYGON('POLYGON((6.0 7.0, 10.0 3.0, 10.0 10.0, 6.0 7.0))'));
    INSERT INTO SpatialShapes VALUES(12, NEW ST_POLYGON('POLYGON((4.0 5.0, 5.0 3.0, 6.0 5.0, 4.0 5.0))'));
    INSERT INTO SpatialShapes VALUES(13, NEW ST_POLYGON('POLYGON((1.0 1.0, 1.0 6.0, 6.0 6.0, 6.0 1.0, 1.0 1.0))'));
    INSERT INTO SpatialShapes VALUES(14, NEW ST_POLYGON('POLYGON((1.0 3.0, 1.0 4.0, 5.0 4.0, 5.0 3.0, 1.0 3.0))'));
    INSERT INTO SpatialShapes VALUES(15, NEW ST_POLYGON());
    ```

    Check shapes you loaded, including types of geometries and what geometry values represent empty sets.

    ```sql
    SELECT SHAPEID, SHAPE.ST_asWKT(), SHAPE.ST_GeometryType(), SHAPE.ST_isEmpty()
    FROM SPATIALSHAPES;
    ```

    ![Dataset select](spatial0402.jpg)

4. When you need to combine multiple shapes into one you can use different set operations and aggregation methods.

    Aggregation methods are executed on spatial columns of tables in SAP HANA.

    `ST_UnionAggr()` returns the spatial union of all of the geometries in a group.

    ```sql
    SELECT ST_UnionAggr(SHAPE).ST_asWKT() as UnionAggr
    FROM SPATIALSHAPES
    WHERE SHAPE.ST_isEmpty()=0 and SHAPE.ST_GeometryType() = 'ST_LineString';
    ```

    ![LineString Union](spatial0403.jpg)

    Or if presented graphically

    ![LineString Union SVG](spatial0404.jpg)

    Note as well spatial predicates used in the query above to select only geometries of `LineString` type and only those not empty.

5. Two more important aggregate methods are
    - `ST_ConvexHullAggr()` returning the convex hull for all of the geometries in a group, also known as "rubber band",
    - `ST_EnvelopeAggr()` returning the bounding rectangle for all of the geometries in a group.

    Execute this query to best illustrate both types of aggregations. It is using as well set operation method `ST_Union()` returning the geometry value that represents the point set union of two geometries.

    ```sql
    SELECT
    ST_ConvexHullAggr(SHAPE).ST_Boundary().ST_Union(ST_UnionAggr(SHAPE)).ST_asWKT() as ConvexHullAggr,
    ST_EnvelopeAggr(SHAPE).ST_Boundary().ST_Union(ST_UnionAggr(SHAPE)).ST_asWKT() as EnvelopeAggr
    FROM SPATIALSHAPES
    WHERE SHAPE.ST_isEmpty()=0 and SHAPE.ST_GeometryType() = 'ST_LineString';
    ```

    Please note the use of `ST_Boundary()` method to convert a polygon (which is a result of the aggregation) into just a curve surrounding the shape, so that combined geometries are all visible.

    ![Other type of aggregations](spatial0405.jpg)

    Seeing is believing, so here are the graphical outputs (with slightly modified SVG to draw shapes of aggregates in red)

    The result of `ST_ConvexHullAggr()`:

    ![result of ST_ConvexHullAggr()](spatial0406.jpg)

    And the result of `ST_EnvelopeAggr()`:

    ![result of ST_EnvelopeAggr()](spatial0407.jpg)

### Optional
- Check SAP HANA Spatial Reference at http://help.sap.com/hana_platform for the complete list of objects and methods

## Next Steps
 - Intro to SAP HANA Spatial: 3rd dimension (coming soon), or
 - Select a tutorial from the [Tutorial Navigator](http://www.sap.com/developer/tutorial-navigator.html) or the [Tutorial Catalog](http://www.sap.com/developer/tutorials.html)
