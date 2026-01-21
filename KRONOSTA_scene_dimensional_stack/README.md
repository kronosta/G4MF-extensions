The KRONOSTA\_scene\_dimensional\_stack extension allows for multiple scenes in one file in a manner similar

to the Dimensional Stack/Trinsfer fiction. It supports named scenes, dead timelines, and higher-dimensional

time.



\# Added to the root document

In `extensions/KRONOSTA\_scene\_dimensional\_stack`, there is an object with the following keys:



| Name | Type | Description | Default |

| --- | --- | --- | --- |

| geometries | `object` | A dictionary of geometry names to Geometry objects. | {} |

| --- | --- | --- | --- |



\# Added to Node object

In `extensions/KRONOSTA\_scene\_dimensional\_stack`, there is an object with the following keys:



| Name | Type | Description | Default |

| --- | --- | --- | --- |

| origin | `object` | An instant path describing where this node originated, if it traveled from another world, or null if it came from here. | null |

| --- | --- | --- | --- |



\# Geometry object



| Name | Type | Description | Default |

| --- | --- | --- | --- |

| time\_manifolds | `object` | A dictionary of time manifold names to TimeManifold objects | {} |

| dimension | `integer` | The dimension for this geometry. | Required ||

| --- | --- | --- | --- |



\# TimeManifold object



| Name | Type | Description | Default |

| --- | --- | --- | --- |

| rubberband\_present\_manifolds | `object` | A dictionary of time manifold names to RubberbandPresentManifold objects | {} |

| dimension | `integer` | The dimension for this time manifold. | Required |

| --- | --- | --- | --- |



\# RubberbandPresentManifold object



| Name | Type | Description | Default |

| --- | --- | --- | --- |

| main\_timeline | `object` | A Timeline object for the current timeline of this world. | {} |

| dead\_timelines | `object` | A DeadTimelineComplex for dead timelines. | {} |

| dimension | `integer` | The dimension for this rubberband present manifold. | Required |

| --- | --- | --- | --- |



\# DeadTimelineComplex object



| Name | Type | Description | Default |

| --- | --- | --- | --- |

| timelines | object | A dictionary of timeline names to Timeline objects.

| --- | --- | --- | --- |



\# Timeline object



| Name | Type | Description | Default |

| --- | --- | --- | --- |

| instants | object | A dictionary of instant names to Instant objects. | Required |

| current\_instant | string | The name of the current instant of this timeline. | Required |

| --- | --- | --- | --- |



\# Instant object



| Name | Type | Description | Default |

| --- | --- | --- | --- |

| point\_in\_time\_euclidean | number\[] | A representation of the point in the time manifold, if the manifold is Euclidean. | null |

| point\_in\_time | number\[] | A representation of the point in the time manifold, in an unspecified format involving only numbers (if you want to store other data you can use this as a byte array). | null |

| scene | object | A file ref for the G4MF scene file. This may contain another dimensional stack. | {} |

| --- | --- | --- | --- |



Exactly one of `point\_in\_time\_euclidean` or `point\_in\_time` are required. `point\_in\_time` requires agreement about the format not provided in this document.



\# InstantPath object



| Name | Type | Description | Default |

| --- | --- | --- | --- |

| geometry | string | The name of the geometry. | "@E4" |

| time\_manifold | string | The name of the time manifold. | "@E1" |

| rubberband\_present\_manifold | string | The name of the rubberband present manifold. | "@E0" |

| timeline | string | The name of the dead timeline, or null for the main timeline. | null |

| instant | string | The name of the instant. | "Present" |

| --- | --- | --- | --- |



\# Standard names of manifolds

To name a Geometry, TimeManifold, or RubberbandPresent manifold, the string must follow this system:

* A name can consist of `\&` followed by a match to the regex (\[A-Za-z0-9\_]|\\{\\R(,\\R)\*\\})+ where \\R recursively refers to the entire regex for custom manifolds
* Any name can be suffixed with `#` followed by  a match to the regex (\[A-Za-z0-9\_]|\\{\\R(,\\R)\*\\})+ where \\R recursively refers to the entire regex for multiple of the same manifold
* `@E` followed by a number N refers to N-dimensional Euclidean space
* `@T` followed by a number N refers to the N-dimensional flat torus
* `@TG` followed by a number N refers to the orientable toroidal 2-manifold of genus N
* `@TGN` followed by a number N refers to the non-orientable toroidal 2-manifold of genus N
* `@S` followed by a number N refers to the N-dimensional sphere
* `@H` followed by a number N refers to N dimensional hyperbolic space
* `@Nil` followed by a number N refers to N dimensional Nil space
* `@Sol3` refers to Sol3
* `@Sol4\_1` refers to Sol4\_1
* `@Sol4\_0` refers to Sol4\_1
* `@Sol4\_M\_N` where M and N are replaced with integers refers to Sol4\_{M,N}
* `@Sol5\_M\_N\_P` where M, N, and P are replaced with integers refers to Sol5\_{M,N,P}
* `@SL2R` refers to SL(2,R)
* `@PSL2R` refers to PSL(2,R)
* `@USL2R` refers to the universal cover of SL(2,R)
* `@T1H` followed by a number N refers to the unit tangent bundle of N-dimensional hyperbolic space
* `@TH` followed by a number N refers to the tangent bundle of N-dimensional hyperbolic space (F4 can be written as `@TH2`
* `@CP` followed by a number N to the complex projective space of dimension N
* `@HC` followed by a number N refers to H^N(C) geometry
* `@AndrewGeng` followed by a number N refers to the Nth geometry in \[https://arxiv.org/pdf/1605.07545]
* `@SL2X\_{N}S3` and `@SL2X\_{N}SL2` where N is replaced by a decimal number (above zero in both cases and less than or equal to one in the latter) refer to geometries in the above paper.
* `L{A,1}X\_{S1}L{B,1}` where A and B are replaced with two coprime integers greater than zero refer to geometries in the above paper.
* `@Seifert{b,e,g,p}` where b is replaced with an integer, g is replaced with a natural number, e is replaced with `o1`, `o2`, `n1`, `n2`, `n3`, or `n4`, 

&nbsp; and p is replaced with a comma separated list of an even number of integers. All of this refers to a Siefert fiber space with the corresponding notation

* `@Tora{N,R}` where N is replaced with the (|||)-type toratope notation, and R is replaced with a comma-separated list of radii in order of closing

&nbsp; brackets.

* `{G}\*` where G is a comma-separated list of names in this system refers to the product of the represented manifolds.
