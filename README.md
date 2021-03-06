<!-------------------------------------------------------------------->
<!--                            WARNING!                            -->
<!-------------------------------------------------------------------->
<!--                                                                -->
<!-- THIS IS AN AUTOGENERATED FILE. DO NOT EDIT THIS FILE DIRECTLY. -->
<!-- for your changes use README.template.hbs file                  -->
<!--                                                                -->
<!-------------------------------------------------------------------->
<!-------------------------------------------------------------------->

# transformation-matrix
Javascript isomorphic 2D affine transformations written in ES6 syntax. Manipulate transformation matrices with this totally tested library!

[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard.js-brightgreen.svg)](https://standardjs.com)
[![Build Status](https://travis-ci.org/chrvadala/transformation-matrix.svg?branch=master)](https://travis-ci.org/chrvadala/transformation-matrix)
[![Coverage Status](https://coveralls.io/repos/github/chrvadala/transformation-matrix/badge.svg?branch=master)](https://coveralls.io/github/chrvadala/transformation-matrix?branch=master)
[![npm](https://img.shields.io/npm/v/transformation-matrix.svg?maxAge=2592000?style=plastic)](https://www.npmjs.com/package/transformation-matrix)
[![Downloads](https://img.shields.io/npm/dm/transformation-matrix.svg)](https://www.npmjs.com/package/transformation-matrix)
[![Donate](https://img.shields.io/badge/donate-PayPal-green.svg)](https://www.paypal.me/chrvadala/25)

Transformations, i.e. *linear invertible automorphisms*, are used to map a picture into another one with different size, position and orientation. Given a basis, transformations are represented by means of squared invertible matrices, called **transformation matrices**.
A geometric transformation is defined as a one-to-one mapping of a point space to itself, which preservers some geometric relations of figures. - [Geometric Programming for Computer Aided Design](https://books.google.it/books?vid=ISBN9780471899426)

This library allows us to:
- generate transformation matrices for the following operations: **translation**, **rotation**, **scale**, **shear**, **skew**
- merge multiple transformation matrices in a single matrix that is the **composition of multiple matrices**
- work with strings in both directions: **parse**, **render**
- **apply a transformation matrix to point(s)**

## Usage example (ES6)
```js
import {scale, rotate, translate, compose, applyToPoint} from 'transformation-matrix';
let {scale, rotate, translate, compose, applyToPoint} = window.TransformationMatrix;
let {scale, rotate, translate, compose, applyToPoint} = require('transformation-matrix')

let matrix = compose(
  translate(40,40),
  rotate(Math.PI/2),
  scale(2, 4)
);

applyToPoint(matrix, {x: 42, y: 42});
// { x: -128, y: 124.00000000000001 }

applyToPoint(matrix, [16, 24]);
//  [ -56, 72 ]
```

## Setup
```sh
npm install transformation-matrix
# or
yarn add transformation-matrix
```
```html
<script src="https://unpkg.com/transformation-matrix@1"></script>
```


## Data Model
A **Transformation Matrix** is defined as an `Object` with 6 keys: `a`, `b`, `c`, `d`, `e` and `f`.
```js
const matrix = { a: 1, c: 0, e: 0,
                 b: 0, d: 1, f: 0 }
```
A **Point** can be defined in two different ways:
- as `Object`, with inside two keys: `x` and `y`
```js
const point = { x: 24, y: 42 }
```
- as `Array`, with two items in the form `[x, y]`
```js
const point = [ 24, 42 ]
```

## Live Demo
available at [http://chrvadala.github.io/transformation-matrix/](http://chrvadala.github.io/transformation-matrix/)

# Reference
## Functions

<dl>
<dt><a href="#applyToPoint">applyToPoint(matrix, point)</a> ⇒ <code>Object</code> | <code>Array</code></dt>
<dd><p>Calculate a point transformed with an affine matrix</p>
</dd>
<dt><a href="#applyToPoints">applyToPoints(matrix, points)</a> ⇒ <code>array</code></dt>
<dd><p>Calculate an array of points transformed with an affine matrix</p>
</dd>
<dt><a href="#fromObject">fromObject(object)</a> ⇒ <code>Object</code></dt>
<dd><p>Extract an affine matrix from an object that contains a,b,c,d,e,f keys
Each value could be a float or a string that contains a float</p>
</dd>
<dt><a href="#fromString">fromString(string)</a> ⇒ <code>Object</code></dt>
<dd><p>Parse a string matrix formatted as matrix(a,b,c,d,e,f)</p>
</dd>
<dt><a href="#fromTransformAttribute">fromTransformAttribute(transformString)</a> ⇒ <code>Object</code></dt>
<dd><p>Parser for SVG Trasform Attribute <a href="http://www.w3.org/TR/SVG/coords.html#TransformAttribute">http://www.w3.org/TR/SVG/coords.html#TransformAttribute</a> <br/>
Warning: This should be considered BETA until it is released a stable version of pegjs.</p>
</dd>
<dt><a href="#fromTriangles">fromTriangles(t1, t2)</a> ⇒ <code>Object</code></dt>
<dd><p>Returns a matrix that transforms a triangle t1 into another triangle t2, or throws an exception if it is impossible.</p>
</dd>
<dt><a href="#identity">identity()</a> ⇒ <code>Object</code></dt>
<dd><p>Identity matrix</p>
</dd>
<dt><a href="#inverse">inverse(matrix)</a> ⇒ <code>Object</code></dt>
<dd><p>Calculate a matrix that is the inverse of the provided matrix</p>
</dd>
<dt><a href="#isAffineMatrix">isAffineMatrix(object)</a> ⇒ <code>boolean</code></dt>
<dd><p>Check if the object contain an affine matrix</p>
</dd>
<dt><a href="#rotate">rotate(angle, [cx], [cy])</a> ⇒ <code>Object</code></dt>
<dd><p>Calculate a rotation matrix</p>
</dd>
<dt><a href="#rotateDEG">rotateDEG(angle, [cx], [cy])</a> ⇒ <code>Object</code></dt>
<dd><p>Calculate a rotation matrix with a DEG angle</p>
</dd>
<dt><a href="#scale">scale(sx, [sy])</a> ⇒ <code>Object</code></dt>
<dd><p>Calculate a scaling matrix</p>
</dd>
<dt><a href="#shear">shear(shx, shy)</a> ⇒ <code>Object</code></dt>
<dd><p>Calculate a shear matrix</p>
</dd>
<dt><a href="#skew">skew(ax, ay)</a> ⇒ <code>Object</code></dt>
<dd><p>Calculate a skew matrix</p>
</dd>
<dt><a href="#skewDEG">skewDEG(ax, ay)</a> ⇒ <code>Object</code></dt>
<dd><p>Calculate a skew matrix using DEG angles</p>
</dd>
<dt><a href="#smoothMatrix">smoothMatrix(m, [precision])</a> ⇒ <code>Object</code></dt>
<dd><p>Rounds all elements of the given matrix using the given precision</p>
</dd>
<dt><a href="#toCSS">toCSS(matrix)</a> ⇒ <code>string</code></dt>
<dd><p>Serialize the matrix to a string that can be used with CSS or SVG</p>
</dd>
<dt><a href="#toSVG">toSVG(matrix)</a> ⇒ <code>string</code></dt>
<dd><p>Serialize the matrix to a string that can be used with CSS or SVG</p>
</dd>
<dt><a href="#toString">toString(matrix)</a> ⇒ <code>string</code></dt>
<dd><p>Serialize the matrix to a string that can be used with CSS or SVG</p>
</dd>
<dt><a href="#transform">transform(...matrices)</a> ⇒ <code>Object</code></dt>
<dd><p>Merge multiple matrices into one</p>
</dd>
<dt><a href="#compose">compose(...matrices)</a> ⇒ <code>Object</code></dt>
<dd><p>Merge multiple matrices into one (alias of <code>transform</code>)</p>
</dd>
<dt><a href="#translate">translate(tx, [ty])</a> ⇒ <code>Object</code></dt>
<dd><p>Calculate a translate matrix</p>
</dd>
</dl>

## Changelog
- **0.0** - Preview version
- **1.0** - First public version
- **1.1** - Splits lib into different files
- **1.2** - Adds shear operation
- **1.3** - Adds umd support
- **1.4** - Adds typescript definitions
- **1.5** - Upgrades deps
- **1.6** - Adds optional parameter support on `translate(tx)`, `scale(sx)`, `rotate(angle, cx, cy)`
- **1.7** - Upgrades deps
- **1.8** - Fixes [#12](https://github.com/chrvadala/transformation-matrix/issues/12), Adds `fromTransformAttribute`, Discontinues node 4 support
- **1.9** - Adds `skew(ax, ay)`, Upgrades deps, Improves `fromTransformAttribute`
- **1.10**- Updates typescript definitions [#15](https://github.com/chrvadala/transformation-matrix/pull/15)
- **1.11**- Upgrades deps
- **1.12**- Migrates tests on [Jest](https://jestjs.io/), Integrates [standard.js](https://standardjs.com/), Upgrades deps
- **1.13**- Adds `compose` function, Upgrades deps, Exposes skew operation [#37](https://github.com/chrvadala/transformation-matrix/pull/37)
- **1.14**- Adds support for points defined as `Array` in the form `[x, y]` [#38](https://github.com/chrvadala/transformation-matrix/pull/38)
- **1.15**- Adds `fromTriangle` and `smoothMatrix` functions [#41](https://github.com/chrvadala/transformation-matrix/issues/41)

## Some projects using transformation-matrix
- [**React Planner**](https://github.com/cvdlab/react-planner)
- [**React SVG Pan Zoom**](https://github.com/chrvadala/react-svg-pan-zoom)
- [**ngx-graph**](https://github.com/swimlane/ngx-graph)
- [**learn-anything**](https://github.com/learn-anything/learn-anything)
- [**Others...**](https://github.com/chrvadala/transformation-matrix/network/dependents)
- Pull request your project!

## Contributors
- [chrvadala](https://github.com/chrvadala) (author)
- [forabi](https://github.com/forabi)
- [nidu](https://github.com/nidu) (PEG.js descriptor)
- [aubergene](https://github.com/aubergene)
- [SophiaLi1](https://github.com/SophiaLi1)

# API
<a name="applyToPoint"></a>

## applyToPoint(matrix, point) ⇒ <code>Object</code> \| <code>Array</code>
Calculate a point transformed with an affine matrix

**Kind**: global function  
**Returns**: <code>Object</code> \| <code>Array</code> - Point  

| Param | Description |
| --- | --- |
| matrix | Affine matrix |
| point | Point |

<a name="applyToPoints"></a>

## applyToPoints(matrix, points) ⇒ <code>array</code>
Calculate an array of points transformed with an affine matrix

**Kind**: global function  
**Returns**: <code>array</code> - Array of points  

| Param | Description |
| --- | --- |
| matrix | Affine matrix |
| points | Array of points |

<a name="fromObject"></a>

## fromObject(object) ⇒ <code>Object</code>
Extract an affine matrix from an object that contains a,b,c,d,e,f keys
Each value could be a float or a string that contains a float

**Kind**: global function  
**Returns**: <code>Object</code> - }  

| Param |
| --- |
| object | 

<a name="fromString"></a>

## fromString(string) ⇒ <code>Object</code>
Parse a string matrix formatted as matrix(a,b,c,d,e,f)

**Kind**: global function  
**Returns**: <code>Object</code> - Affine matrix  

| Param | Description |
| --- | --- |
| string | String with a matrix |

<a name="fromTransformAttribute"></a>

## fromTransformAttribute(transformString) ⇒ <code>Object</code>
Parser for SVG Trasform Attribute http://www.w3.org/TR/SVG/coords.html#TransformAttribute <br/>
Warning: This should be considered BETA until it is released a stable version of pegjs.

**Kind**: global function  
**Returns**: <code>Object</code> - Parsed matrices  

| Param | Description |
| --- | --- |
| transformString | string |

<a name="fromTriangles"></a>

## fromTriangles(t1, t2) ⇒ <code>Object</code>
Returns a matrix that transforms a triangle t1 into another triangle t2, or throws an exception if it is impossible.

**Kind**: global function  
**Returns**: <code>Object</code> - Affine matrix which transforms t1 to t2  
**Throws**:

- Exception if the matrix becomes not invertible


| Param | Type | Description |
| --- | --- | --- |
| t1 | <code>Array.&lt;{x: number, y: number}&gt;</code> \| <code>Array.&lt;Array.&lt;number&gt;&gt;</code> | an array of points containing the three points for the first triangle |
| t2 | <code>Array.&lt;{x: number, y: number}&gt;</code> \| <code>Array.&lt;Array.&lt;number&gt;&gt;</code> | an array of points containing the three points for the second triangle |

<a name="identity"></a>

## identity() ⇒ <code>Object</code>
Identity matrix

**Kind**: global function  
**Returns**: <code>Object</code> - Affine matrix  
<a name="inverse"></a>

## inverse(matrix) ⇒ <code>Object</code>
Calculate a matrix that is the inverse of the provided matrix

**Kind**: global function  
**Returns**: <code>Object</code> - Affine matrix  

| Param | Description |
| --- | --- |
| matrix | Affine matrix |

<a name="isAffineMatrix"></a>

## isAffineMatrix(object) ⇒ <code>boolean</code>
Check if the object contain an affine matrix

**Kind**: global function  

| Param |
| --- |
| object | 

<a name="rotate"></a>

## rotate(angle, [cx], [cy]) ⇒ <code>Object</code>
Calculate a rotation matrix

**Kind**: global function  
**Returns**: <code>Object</code> - Affine matrix *  

| Param | Description |
| --- | --- |
| angle | Angle in radians |
| [cx] | If (cx,cy) are supplied the rotate is about this point |
| [cy] | If (cx,cy) are supplied the rotate is about this point |

<a name="rotateDEG"></a>

## rotateDEG(angle, [cx], [cy]) ⇒ <code>Object</code>
Calculate a rotation matrix with a DEG angle

**Kind**: global function  
**Returns**: <code>Object</code> - Affine matrix  

| Param | Description |
| --- | --- |
| angle | Angle in degree |
| [cx] | If (cx,cy) are supplied the rotate is about this point |
| [cy] | If (cx,cy) are supplied the rotate is about this point |

<a name="scale"></a>

## scale(sx, [sy]) ⇒ <code>Object</code>
Calculate a scaling matrix

**Kind**: global function  
**Returns**: <code>Object</code> - Affine matrix  

| Param | Default | Description |
| --- | --- | --- |
| sx |  | Scaling on axis x |
| [sy] | <code>sx</code> | Scaling on axis y (default sx) |

<a name="shear"></a>

## shear(shx, shy) ⇒ <code>Object</code>
Calculate a shear matrix

**Kind**: global function  
**Returns**: <code>Object</code> - Affine matrix  

| Param | Description |
| --- | --- |
| shx | Shear on axis x |
| shy | Shear on axis y |

<a name="skew"></a>

## skew(ax, ay) ⇒ <code>Object</code>
Calculate a skew matrix

**Kind**: global function  
**Returns**: <code>Object</code> - Affine matrix  

| Param | Description |
| --- | --- |
| ax | Skew on axis x |
| ay | Skew on axis y |

<a name="skewDEG"></a>

## skewDEG(ax, ay) ⇒ <code>Object</code>
Calculate a skew matrix using DEG angles

**Kind**: global function  
**Returns**: <code>Object</code> - Affine matrix  

| Param | Description |
| --- | --- |
| ax | Skew on axis x |
| ay | Skew on axis y |

<a name="smoothMatrix"></a>

## smoothMatrix(m, [precision]) ⇒ <code>Object</code>
Rounds all elements of the given matrix using the given precision

**Kind**: global function  
**Returns**: <code>Object</code> - the rounded matrix  

| Param | Type | Description |
| --- | --- | --- |
| m | <code>Object</code> | a matrix to round |
| [precision] |  | a precision to use for Math.round. Defaults to 10000000000 (meaning which rounds to the 10th digit after the comma). |

<a name="toCSS"></a>

## toCSS(matrix) ⇒ <code>string</code>
Serialize the matrix to a string that can be used with CSS or SVG

**Kind**: global function  
**Returns**: <code>string</code> - String that contains a matrix formatted as matrix(a,b,c,d,e,f)  

| Param | Description |
| --- | --- |
| matrix | Affine matrix |

<a name="toSVG"></a>

## toSVG(matrix) ⇒ <code>string</code>
Serialize the matrix to a string that can be used with CSS or SVG

**Kind**: global function  
**Returns**: <code>string</code> - String that contains a matrix formatted as matrix(a,b,c,d,e,f)  

| Param | Description |
| --- | --- |
| matrix | Affine matrix |

<a name="toString"></a>

## toString(matrix) ⇒ <code>string</code>
Serialize the matrix to a string that can be used with CSS or SVG

**Kind**: global function  
**Returns**: <code>string</code> - String that contains a matrix formatted as matrix(a,b,c,d,e,f)  

| Param | Description |
| --- | --- |
| matrix | Affine matrix |

<a name="transform"></a>

## transform(...matrices) ⇒ <code>Object</code>
Merge multiple matrices into one

**Kind**: global function  
**Returns**: <code>Object</code> - Affine matrix  

| Param | Type | Description |
| --- | --- | --- |
| ...matrices | <code>object</code> | list of matrices |

<a name="compose"></a>

## compose(...matrices) ⇒ <code>Object</code>
Merge multiple matrices into one (alias of `transform`)

**Kind**: global function  
**Returns**: <code>Object</code> - Affine matrix  

| Param | Type | Description |
| --- | --- | --- |
| ...matrices | <code>object</code> | list of matrices |

<a name="translate"></a>

## translate(tx, [ty]) ⇒ <code>Object</code>
Calculate a translate matrix

**Kind**: global function  
**Returns**: <code>Object</code> - Affine matrix  

| Param | Default | Description |
| --- | --- | --- |
| tx |  | Translation on axis x |
| [ty] | <code>0</code> | Translation on axis y |

