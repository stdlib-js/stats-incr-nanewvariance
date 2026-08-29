<!--

@license Apache-2.0

Copyright (c) 2026 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# incrnanewvariance

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Compute an [exponentially weighted variance][exponentially weighted variance] incrementally, ignoring `NaN` values.

<section class="intro">

The [exponentially weighted variance][exponentially weighted variance] is defined as

<!-- <equation class="equation" label="eq:exponentially_weighted_variance" align="center" raw="S_n = \begin{cases} 0 & \textrm{if}\ n = 0 \\ (1 - \alpha) (S_{n-1} + \alpha(x_n - \mu_{n-1})^2) & \textrm{if}\ n > 0 \end{cases}" alt="Recursive definition for computing an exponentially weighted variance."> -->

```math
S_n = \begin{cases} 0 & \textrm{if}\ n = 0 \\ (1 - \alpha) (S_{n-1} + \alpha(x_n - \mu_{n-1})^2) & \textrm{if}\ n > 0 \end{cases}
```

<!-- <div class="equation" align="center" data-raw-text="S_n = \begin{cases} 0 &amp; \textrm{if}\ n = 0 \\ (1 - \alpha) (S_{n-1} + \alpha(x_n - \mu_{n-1})^2) &amp; \textrm{if}\ n &gt; 0 \end{cases}" data-equation="eq:exponentially_weighted_variance">
    <img src="https://cdn.jsdelivr.net/gh/stdlib-js/stdlib@49d8cabda84033d55d7b8069f19ee3dd8b8d1496/lib/node_modules/@stdlib/stats/incr/nanewvariance/docs/img/equation_exponentially_weighted_variance.svg" alt="Recursive definition for computing an exponentially weighted variance.">
    <br>
</div> -->

<!-- </equation> -->

</section>

<!-- /.intro -->



<section class="usage">

## Usage

```javascript
import incrnanewvariance from 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-nanewvariance@esm/index.mjs';
```

#### incrnanewvariance( alpha )

Returns an accumulator function which incrementally computes an [exponentially weighted variance][exponentially weighted variance], ignoring `NaN` values.

```javascript
var accumulator = incrnanewvariance( 0.5 );
```

#### accumulator( \[x] )

If provided an input value `x`, the accumulator function returns an updated exponentially weighted variance. If not provided an input value `x`, the accumulator function returns the current exponentially weighted variance.

```javascript
var accumulator = incrnanewvariance( 0.5 );

var v = accumulator();
// returns null

v = accumulator( 2.0 );
// returns 0

v = accumulator( 4.0 );
// returns 1

v = accumulator( NaN );
// returns 1

v = accumulator( 5.0 );
// returns 1.5

v = accumulator();
// returns 1.5
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   Input values are **not** type checked. If non-numeric inputs are possible, you are advised to type check and handle accordingly **before** passing the value to the accumulator function.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="module">

import randu from 'https://cdn.jsdelivr.net/gh/stdlib-js/random-base-randu@esm/index.mjs';
import incrnanewvariance from 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-nanewvariance@esm/index.mjs';

var accumulator;
var v;
var i;

// Initialize an accumulator with smoothing factor α = 0.5:
accumulator = incrnanewvariance( 0.5 );

// For each simulated datum, update the exponentially weighted variance...
for ( i = 0; i < 100; i++ ) {
    // With a 20% chance, provide NaN to test that invalid inputs are ignored:
    v = ( randu() < 0.2 ) ? NaN : randu() * 100.0;
    accumulator( v );
}
console.log( accumulator() );

</script>
</body>
</html>
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/stats-incr-nanewvariance.svg
[npm-url]: https://npmjs.org/package/@stdlib/stats-incr-nanewvariance

[test-image]: https://github.com/stdlib-js/stats-incr-nanewvariance/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/stats-incr-nanewvariance/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/stats-incr-nanewvariance/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/stats-incr-nanewvariance?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/stats-incr-nanewvariance.svg
[dependencies-url]: https://david-dm.org/stdlib-js/stats-incr-nanewvariance/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/stats-incr-nanewvariance/tree/deno
[deno-readme]: https://github.com/stdlib-js/stats-incr-nanewvariance/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/stats-incr-nanewvariance/tree/umd
[umd-readme]: https://github.com/stdlib-js/stats-incr-nanewvariance/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/stats-incr-nanewvariance/tree/esm
[esm-readme]: https://github.com/stdlib-js/stats-incr-nanewvariance/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/stats-incr-nanewvariance/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/stats-incr-nanewvariance/main/LICENSE

[exponentially weighted variance]: https://en.wikipedia.org/wiki/EWMA_chart

</section>

<!-- /.links -->
