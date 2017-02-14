---
layout: page
title: Example Qunit
---


This example demonstrates how to use aXe with the QUnit unit testing framework.

The unit test is in `test/a11y.js`, and has two test cases: One that shows the
expected results from HTML with no errors, and one that shows the expected
result from HTML with a single error.

## To configure the example ##

* Node must be installed; please follow the directions at http://www.nodejs.org
  to install it.
* `npm install -g grunt-cli` to install the Grunt task runner (may need to be
  run with `sudo` on Unix or as Administrator on Windows)
* Move to the `doc/examples/qunit` directory
* `npm install` to install dependencies

## To run the example ##

* Move to the `doc/examples/qunit` directory
* `grunt qunit` to run QUnit

You should see output indicating that the tests ran successfully, with zero
failures.

## To modify the example ##

To run the example on your own HTML, such as widgets or controls, insert the
HTML into the document, retrieve the root element of your widget (with e.g.,
`document.getElementById()`), and pass that as the first argument into a call
to `axe.a11yCheck`.  

The third argument to the `axe.a11yCheck` call should be the function to test
the results. The example is simply looking at the count of violations, but much
more detailed information is available if desired.  The aXe documentation
should be consulted for more details on customizing and
analyzing calls to `axe.a11yCheck`.


## package.json
<pre><code class="highlight language-javascript">
{
  "name": "axe-qunit-example",
  "description": "aXe QUnit Example",
  "version": "0.0.1",
  "private": true,
  "author": {
    "name": "David Sturley",
    "organization": "Deque Systems, Inc.",
    "url": "http://deque.com/"
  },
  "dependencies": {},
  "scripts": {
    "build": "grunt"
  },
  "devDependencies": {
    "axe-core": "~1.0.1",
    "grunt": "~0.4.4",
    "grunt-contrib-qunit": "~0.4.0",
    "qunitjs": "~1.14.0"
  }
}

</code></pre>

## Gruntfile.js
<pre><code class="highlight language-javascript">
module.exports = function (grunt) {
	'use strict';

	grunt.loadNpmTasks('grunt-contrib-qunit');

	grunt.initConfig({
		qunit: {
			all: ['test/**/*.html']
		}
	});
};
</code></pre>
